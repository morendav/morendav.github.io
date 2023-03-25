Idea:
* train a binary classificaiton model
* pause at X epoch, demonstrate overfitting by comparing training data vs test data accuracy
* Run MIA at each epoch, demonstrate that as the model becomes overfit the MIA returns a higher measure of memorization





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
4. ?
