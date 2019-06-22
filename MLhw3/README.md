### Homework 3

##### Programming Problem 1
For this problem, your task will be to implement kernel ridge regression and ridge
regression with landmark based features (let’s call the latter simply “landmark-ridge”), and train and test these
models on the provided dataset (already split into training and test). For both models, you have to use the RBF
kernel k(x n , x m ) = exp(−γ||x n − x m || 2 ) with bandwidth parameter γ = 0.1. The training and test datasets
are given in files ridgetrain.txt and ridgetest.txt. In each file, each line is an example, with first
number being the input (a single feature) and the second number being the output.
You need to do the following
1. For kernel ridge regression, train the model with the regularization hyperparameter λ = 0.1 and use the
learned model to predict the outputs for the test data. Compare the model’s predictions with the true test
3outputs (given to you) by plotting on a graph. In particular, plot all the test inputs and the corresponding
true outputs (x, y) on a 2D plot in blue color, and likewise all the test inputs and corresponding predicted
outputs in red color. Repeat this exercise for λ = 1, 10, 100. What do you observe from the plots? For
each case, also report the root-mean-squared-error (RMSE) on the test data, which is defined as square
root of the mean of squared differences of true outputs and the predicted outputs.
2. For landmark-ridge, you first need to extract landmark based features using the RBF kernel and you will
then use data with these features to train a linear ridge regression model. Again, keep the regularization
hyperparameter fixed at λ = 0.1. Try L = 2, 5, 20, 50, 100 uniformly randomly chosen landmark points
from the training set, train the model for each case and compute the predictions on the test data. Plot the
results for each case just like you did in part 1 (but only for λ = 0.1). What do you observe from the
plots? What’s the RMSE in each case? What value of L seems good enough?

##### Programming Problem 2
For this problem, your task will be to implement the K-means clustering algorithm
and try it on a provided toy (but interesting) dataset (kmeans data.txt) consisting of points in two dimen-
sions. The provided dataset also has 2 clusters (so you would use K = 2). However, the data is such that the
standard K-means will NOT work well since the clusters are not spherical and not separable linearly (you can
check this by plotting the data in 2D using a scatter plot). You will consider two ways to handle this issue.
1. *Using Hand-crafted Features*: Propose a feature transformation to the original data that will transform it
such that K-means will be able to learn the correct clusters! Before proposing the transformation, plot the
original data to see what transformation(s) might probably work. Apply your K-means implementation on
this transformed version of the data to verify if your transformation works. Plot your obtained clustering
results by showing points (in the original 2D space) in cluster 1 in red and points in cluster 2 in green.
2. *Using Kernels*: Although you can kernelize K-mean via the kernel K-means algorithm, you will try
something else. You will use the landmark based approach to extract good features and your implementa-
tion of standard K-means on these features. The kernel that you will use for the landmark based approach
is the RBF kernel k(x n , x m ) = exp(−γ||x n − x m || 2 ) with bandwidth parameter γ = 0.1. We are going
to try something (that may seem) crazy: We will pick L = 1 (yes, just ONE) landmark point randomly
from the dataset and see whether L = 1 (which basically means just a single landmark based feature) is
good enough to learn a correct clustering (at least for this data). It turns out that some landmark choices
will be work and some won’t work. Try 10 runs of the algorithm, each time with a different randomly
chosen (single) landmark and check the obtained clustering. For each run, produce a plot as you did in
part 1 and, on the same plot, also show the chosen landmark point in blue color. Justify why you get a
correct clustering in some cases and a not-so-correct looking clustering in other cases.
Important Note: To avoid randomness in cluster mean initialization, we will choose the first two points in the
dataset (the first two lines in the provided dataset) as the initial cluster centers.
