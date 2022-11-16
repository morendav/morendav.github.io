# python dp

## Ideas / Topics for blog post

For the first blog post: [1, 2, 4]

1. using laplace distribution eDP, query multiple times and plot (show laplace centered around target value)
  * math: why laplace vs gaussian, see page 7 of [https://privacytools.seas.harvard.edu/files/privacytools/files/complexityprivacy_1.pdf]
  * gaussian is used with (epsilon, delta) diff privacy
  * for this, just use average

2. Effect of outliers on diff privacy noise
  * tight distribution VS skewed distribution with a long tail VS wide distribution data
  * for this, compute: Average, Sum, Max
  * scale the distribution skew until you have a few very long tail in distribution
  * plots?

3. Partitions and Users
  * Dialing down how many partitions a user is in (count(days of week | user has visited)) means less noise
  * reference: https://github.com/OpenMined/PyDP/tree/dev/examples/Tutorial_2-restaurant_demo  >> see part 2 of demo jupyter notebook
    ```
    # Bounding the number of contributed partitions

    The parameter maxPartitionsContributed in Google's Java example, defines the maximum number of partitions a visitor may contribute to. You might notice that the value of maxPartitionsContributed in the example is 3 instead of 7. Why is that? Differential Privacy adds some amount of random noise to hide contributions of an individual. The more contributions an individual has, the larger the noise is. This affects the utility of the data. In order to preserve the data utility, an approximate estimate of how many times a week a person may visit a restaurant on average was made, and assumed that the value is around 3 instead of scaling the noise by the factor of 7.

    max_partitions_contributed() limits the max contribution to the entered number, in this case 3, i.e., a visitor may contribute or visit the restaurant max 3 times in a week. The rest of the exceeding data is discarded. Everyone with contributions greater than 3 will have "valid_contribution" as False.
    ```

4. eDP and the composition theorum
  * two queries from same eDP, produce data that is at most 2e privacy loss (composition theorum)
  * Practically, this is implemented using a privacy loss ledger aka 'privacy budget'. Since each query produces a loss of e, we can say sum(ei) over all i <= epsilon (total budget)
  * https://github.com/OpenMined/PyDP/tree/dev/examples/Tutorial_4-Launch_demo






``` python
partial_dp_obj = BoundedSum(epsilon=X, lower_bound=5, upper_bound=250, dtype="float")
partial_dp_obj.privacy_budget_left()
# returns X
partial_sum_dp = round(
    partial_dp_obj.result(privacy_budget=0.3), 2 # round to 2 decimals places
)  # define run privacy budget, will use 0.3 of X (remaining is X-0.3)
print(partial_sum_dp)
partial_dp_obj.privacy_budget_left() # X-0.3
partial_sum_dp2 = round(
    partial_dp_obj.result(), 2  # if no priv budget defined then it will use it all at once
)  
```





##################################
### Post scratchpad section
##################################

## post outline

1. TLDR
  * eDP is a method of creating
2. Algorithm w/out math (Algo Lite TM pending)
  * the concept
  * the math LITE
3. Demo
  1. Code demo the laplace distro
  2. Code demo the effect of outliers and wide distribution data
  3. Code demo with budget accounting
4. Algorithm with math
  1. why the Laplace?
  2. the gaussian with restrictions



## python project todo / outline
```
1. data cleanup - STATUS: DONE
  1. ~concate sample data~
    1. ~train includes column 'credit_score' (last column), but test does not. purge this column~
    2. ~concate with~
  2. drop unneeded columns... keep [Customer_ID, Month, Annual_Income, Credit_Utilization_Ratio, Amount_invested_monthly, Monthly_Balance]
  3. for each [Customer_ID] keep only last [Month]'s data
    * Skipped concat data, train and test had same set of users for different slices of months

2. Topic: Show LaPlace disro - STATUS: DONE
  * repeated queries show laplace centered on real value
  * requirement: plot, subplot (distrobiution of data) subplot (repeated queries centered on real value)

3. Topic: Outliers and noise - STATUS: DONE
  * copy data, and widen the distirbution on [Annual_Income]
  * record effect on noise per query, keeping all else same
  * plot histogram by
    * normalized array (array of noise) = array (private average) - array [real average]
    * repeat this for tight and broad distribution
  * requirement: plot, subplot (distrobution) subplot (repeated queriers centered on real value)
4. Topic: Privacy Budget - STATUS: SKIPPED
  * to address this, use the privcay budget accounting
  * query for x% of budget, until budget is exhausted, then keep querying... see noise increases
  * requirement: noise per query as a function of privacy budget
```


## During Dev Scratchpad
Section to capture thoguths and notes during dev of the programs / py notebook

**NOTES**
* we are only using test data (test.csv) and only from month = december
* leave out point #4 about using privacy budget, will speak to it but not demo

**TO DOs**
* create a class to read data that could be import seperately
* create a class / method to repeated private query & generate the normalized noise distribution

**Things left over**
* code an example that uses privacy budget accounting
   * demo a cached answer that is able to provide metric without additional query (i.e. analyst 1 performs query 1, analyst 2 performs query 1, response reuse reponse from before so as not to deplete the privacy budget)


### resources and references
* https://privacytools.seas.harvard.edu/files/privacytools/files/complexityprivacy_1.pdf
  * paper describes eDP (why laplace, when gaussian, math, etc)
* PyDP learning resources: https://github.com/OpenMined/PyDP/blob/dev/resources.md


## During writing Scratchpad

TODO:
1. (DONE) update inline references in post
2. (DONE) update Footer to ack papermod, firebase, & hugo
3. (DONE) update all references of author to be d.moreno
