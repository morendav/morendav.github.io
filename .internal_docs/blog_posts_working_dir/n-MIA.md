# Idea Research
Idea:
Summary: an overfit model memorizes training data more, this is suboptimal for the generalizability of the model but also comes with an additional privacy risk
* train a binary classificaiton model
* pause at X epoch, demonstrate overfitting by comparing training data vs test data accuracy
* Run MIA at each epoch, demonstrate that as the model becomes overfit the MIA returns a higher measure of memorization

Alt Idea: larger models memorize more
  * larger models tend to overfit faster (fact check this)
  * compare models of different size against memorization


Pilot projects
[x] stop a classfication model training at epoch M of N total epoch, to test memorization and overfitting? 
    * In other words, start training, stop, do some anslysis, continue training same model

``` python
# train model on 5 epoch, then evaluate on x-test data and y-test data labels
model.fit(x_train, y_train, epochs=5)
model.evaluate(x_test,  y_test, verbose=2)
# resume training model for another 5 epochs, then evaluate on x-test and y-test
model.fit(x_train, y_train, epochs=5)
model.evaluate(x_test,  y_test, verbose=2)
```

[ ] train a classfication model, run MIA on it
[x] RESEARCH: how to quanity overfit model. Belief it is accuracy of training data vs test data
  * **ANSWER:** when a model has accuracy(training data) > accuracy(test data)



### Tech Debt
[ ] GPU in training env does not support tensorflow GPU optimization. Prompts non-critical error (see below)
```
2023-03-25 22:01:54.845797: I tensorflow/compiler/xla/stream_executor/cuda/cuda_gpu_executor.cc:996] successful NUMA node read from SysFS had negative value (-1), but there must be at least one NUMA node, so returning NUMA node zero. See more at https://github.com/torvalds/linux/blob/v6.0/Documentation/ABI/testing/sysfs-bus-pci#L344-L355
2023-03-25 22:01:54.846061: W tensorflow/core/common_runtime/gpu/gpu_device.cc:1956] Cannot dlopen some GPU libraries. Please make sure the missing libraries mentioned above are installed properly if you would like to use GPU. Follow the guide at https://www.tensorflow.org/install/gpu for how to download and setup the required libraries for your platform.
Skipping registering GPU devices...
```












-----------------------
# Dev Notes

(02/23/23)
* command (see below) for pip install failed
   * fails install step at fortran dependency. This was non-intel terminal and non-intel conda env
   * error message hints at archiecture mismatch
   * next, try nonintel terminal and intel conda

```
pip install tensorflow_privacy
```


(02/28/2023)
* Created new conda env with intel emulation, in a terminal that was apple metal
* retried to install 'tensorflow_privacy'
  * was successful
  * tried to import in python, failed with message "zsh: illegal hardware instruction  python"

(03/01/2023)
* deleted intel emu env, recreated using a terminal in intel emulation
  * same error
  * set up alias in intel terminal
    `alias python=python3`
  * getting different error now
    `zsh: illegal hardware instruction  python3`
* likely root cause: Not all x64 instructions will work in rosetta emulated environment
  * source: https://developer.apple.com/forums/thread/709063
  * tensorflow_privacy may have used AVX or AVX2 or fp16 extensions - used to optimize apps
  * e.g. tensorflow privacy was optimized using AVX: https://github.com/tensorflow/tensorflow/issues/24548

What are my options?
1. buy a new laptop
  * Probably get a linux laptop, e.g. lenovo thinkpad carbon x ($1400)
  * or maxOS but older versions ($1600)
  * not really worth spending more money on this since it's single purpose purchase
2. remote desktop to windows desktop
  * Requires: setting up python, dev env
  * PROs: Use 3080 for hardware accelerated machine learning training & predictions
  * How to
    * Set up desktop for remote desktop: https://support.microsoft.com/en-us/windows/how-to-use-remote-desktop-5fe128d5-8fb1-7a23-3b8a-41e636865e8c
    * Use MacOS client: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac
    * security considerations: https://www.microsoft.com/en-us/security/blog/2020/04/16/security-guidance-remote-desktop-adoption/
  * Alternative: remote to ubuntu instal on same desktop
    * Requires keeping PC on all the time and in ubuntu install
3. find an online dev host
  * compute will run high as work on ml related projects increases
  * potentially high tocuh to set up push pipeline from local machine to cloud
4. ?


(03/24/2023)
* installed ubuntu on home server to do dev work on
* need to instal cuda drivers to use gpu for ml work






# Sandbox area

## ml classifier - Keras tutorial
``` python
import tensorflow as tf
print("TensorFlow version:", tf.__version__)

mnist = tf.keras.datasets.mnist
# x is data, y are labels
(x_train, y_train), (x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

model = tf.keras.models.Sequential([
  tf.keras.layers.Flatten(input_shape=(28, 28)),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.Dropout(0.2),
  tf.keras.layers.Dense(10)
])
predictions = model(x_train[:1]).numpy()
# predictions
tf.nn.softmax(predictions).numpy()
loss_fn = tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True)
loss_fn(y_train[:1], predictions).numpy()
model.compile(optimizer='adam',
              loss=loss_fn,
              metrics=['accuracy'])
model.fit(x_train, y_train, epochs=5)
model.evaluate(x_test,  y_test, verbose=2)

```



## mia - how to
``` python
# map between datasets
train_data = x_train
train_labels = y_train # labels for training dataset
test_data = x_test
test_labels = y_test # labels for test dataset

print('Predict on train...')
logits_train = model.predict(train_data)
print('Predict on test...')
logits_test = model.predict(test_data)

print('Apply softmax to get probabilities from logits...')
prob_train = tf.nn.softmax(logits_train, axis=-1)
prob_test = tf.nn.softmax(logits_test)

print('Compute losses...')
cce = tf.keras.backend.categorical_crossentropy
constant = tf.keras.backend.constant

y_train_onehot = to_categorical(train_labels)
y_test_onehot = to_categorical(test_labels)

loss_train = cce(constant(y_train_onehot), constant(prob_train), from_logits=False).numpy()
loss_test = cce(constant(y_test_onehot), constant(prob_test), from_logits=False).numpy()

attack_input = AttackInputData(
  logits_train = logits_train,
  logits_test = logits_test,
  loss_train = loss_train,
  loss_test = loss_test,
  labels_train = train_labels,
  labels_test = test_labels
)

slicing_spec = SlicingSpec(
    entire_dataset = True,
    by_class = True,
    by_percentiles = False,
    by_classification_correctness = True)

attack_types = [
    AttackType.THRESHOLD_ATTACK,
    # AttackType.LOGISTIC_REGRESSION
] 


## For mnist failed to converge error (see below)
## This is only for attackType.logistic_regression, the error implies the algorithm fails to converge which would imply the regression based test failed
## commenting out that type of attack makes this script succeed
attacks_result = mia.run_attacks(attack_input=attack_input,
                                 slicing_spec=slicing_spec,
                                 attack_types=attack_types)

# print out report for MIA
print(attacks_result.summary(by_slices=True))

```


Failed to converge error:
``` python
Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
/home/morendav/miniconda3/envs/mia/lib/python3.9/site-packages/sklearn/linear_model/_logistic.py:458: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
/home/morendav/miniconda3/envs/mia/lib/python3.9/site-packages/sklearn/linear_model/_logistic.py:458: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
/home/morendav/miniconda3/envs/mia/lib/python3.9/site-packages/sklearn/linear_model/_logistic.py:458: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
```

