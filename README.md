# Multi-Classifier-GTD-Pytorch

Deep Neural Network built in Pytorch (with some functions from fastai library) to predict the 
name of the terrorist group attributed to an act of terrorism from the publicly available 
Global Terrorism Database (GTD).
The model is one of multi-class classification and uses both categorical and continuous 
training variables. The categorical variables have been giving embeddings. This mixed type of 
model is not often found and so, perhaps, this example might be a starting point for any other 
similar problems.
An html version is included for simple access without requiring opening a Jupyter Notebook.
Please note this will only run on CUDA enabled machines. Simple edits are required to run on 
any CPU only machine.

# Instructions

1. Create a subdirectory '/data/' in the directory storing GTDPytorchCUDA.ipynb file.

2. Navigate to http://www.start.umd.edu/gtd/contact/ in order to download the database to
    your '/data' directory.

3. Convert the database from Excel format to .csv format.

4. Rename file 'gtd.csv'.

5. Jupyter Notebook can now be run on a GPU enabled machine.

6. (Optional) Edit notebook to remove .cuda() references. This is neither an exact nor complete
    set of instructions but there should be few errors which are relatively easy to correct after
    doing so and running on CPU.
    

# Description

The purpose of this example is to demonstrate how to create a Pytorch model that accepts data
with both categorical and continuous values to predict a target with categorical values. In addition,
it demonstrates this with embeddings for the categorical variables which are very useful in order
to reduce space and dimensionality while allowing still great expressiveness of features.
This more than the tuning of hyper-parameters or optimization, etc. Such aspects are left to basic
levels.
It uses Pytorch, mostly, along with the fastai library which is built on top of Pytorch.
There is also a bit of data wrangling and processing some of which could have been offloaded to 
previously created functions in Pytorch and fastai but which provides some transparency to the process.

The original file is eventually converted to a Pandas dataframe and processed so as to be a proper
input for Pytorch. Some of the processing is accomplished using fastai which does eliminate the need
to recreate some functions such as normalizing column data. Also, note, some of the odd looking
hard-coded bits are due to using the GTD documentation to make decisions such as whether variable X
should be categorical or continuous.
The categorical variables all are given embeddings for a, hopefully, additional use as a resource.
fastai did inspire the goals of this resource and while some of the library is useful, more of it 
could only be used as a reference and original Pytorch code had to be created as the library code
is not as simple to refactor as one might think according to the problem.

Pytorch Dataset, DataLoader and final model neural net architectures are created. 
Training, validation and testing are performed. The architecture is very simple with only 2 fully
connected layers and the usual standards of dropout, batch normalization, etc. applied where
appropriate. While the validation loss is fluctuating in this notebook, given the disparity in
the number of examples of each target variable, ie. terrorist group encoded to an integer, from 1
to almost 10 thousand and mini-batch effects on this type of data the accuracy is still quite good.

Final note, again, that this notebook is for GPU enabled machines though refactoring for CPU should
be fairly simple and painless.

# WARNING: Notebook in current form will only run on GPU enabled machine.






