Performs the training and testing of a CNN to predict rho on an phased haploid chromosomes. 
Requires installation of keras, tensorflow, numpy, scikit-learn, matplotlib.

All python code runs on python2.7, EXCEPT the model training.  That was done in the cloud on python 3.6!  Sorry!

To run, first run the shell script to produce coalescent simulations (requires ms https://uchicago.app.box.com/s/l3e5uf13tikfjm7e1il1eujitlsjdx13)

`./run.ms.sh`

then gzip the results

`gzip all.LD.sims.txt`

Next run the python2.7 script

`python extract.data.py`

This will output a large compressed file called "ld.data.npz". Use this file as training data for the network.

To train the network, first find a computer with a GPU and get keras and tensorflow installed.  This was done in python3.6
 
 `python3 train.phased.mergenet.PYTHON3.py`
 
Before training begins, the code will print the mean of the training data.  Save that value (should be about 4.8).  
After training the model it prints a json string that specifies the model structure.  You'll want to save that too.  Also the script saves the weights from the CNN in a file called 'regularized.merge.mod.weights'
 
 Next generate some new independent test data with ms.  Run

Ignore BELOW!  Needs to be updated

# `./run.ms.test.sh`
 
# and gzip the output as above (or skip, i've provided a file `autotet.test.data.LD.sims.txt.gz`)
 
# Finally test the CNN on this independent test data, (back in python2.7)
 
# `python final.autotet.test.results.py`
 
# This will print the R^2 and RMSE and a plot