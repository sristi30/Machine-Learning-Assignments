### Homework 2

##### Part 1: 
You are provided a dataset in the file binclass.txt. In this file, the first two numbers on each line
denote the two features of the input x n , and the third number is the binary label y n ∈ {−1, +1}.
Implement a generative classification model for this data assuming Gaussian class-conditional distributions of
2 I ) and N (x|μ , σ 2 I ), respectively. Note that
the positive and negative class examples to be N (x|μ + , σ +
2
− − 2
here I 2 denotes a 2 × 2 identity matrix. Assume the class-marginal to be p(y n = 1) = 0.5, and use MLE
estimates for the unknown parameters. Your implementation need not be specific to two-dimensional inputs and
it should be almost equally easy to implement it such that it works for any number of features (but it is okay if
your implementation is specific to two-dimensional inputs only).
On a two-dimensional plane, plot the examples from both the classes (use red color for positives and blue color
for negatives) and the learned decision boundary for this model. Note that we are not providing any separate
test data. Your task is only to learn the decision boundary using the provided training data and visualize it.
Next, repeat the same exercise but assuming the Gaussian class-conditional distributions of the positive and
negative class examples to be N (x|μ + , σ 2 I 2 ) and N (x|μ − , σ 2 I 2 ), respectively.
Finally, try out a Support Vector Machine (SVM) classifier (with linear kernel) on this data and show the learn
decision boundary. For this part, you do not need to implement SVM. There are many nice implementations
of SVM available, such as the one in scikit-learn and the very popular libSVM toolkit. Assume the “C” (or λ)
hyperparameter of SVM in these implementations to be 1.
Note: One of the goals of this problem is to familiarize you with SVM implementations which, despite the
popularly of deep learning methods nowadays, still remain a very useful tool for classification problems. SVM
also allows learning nonlinear models too using kernels but, for now, let’s limit ourselves with linear SVMs (we
will soon see kernels in the class, after which you can try nonlinear SVMs). Also, while in this homework, you
would just be playing with existing SVM implementations, in the next homework, you will implement SVM on
your own (which isn’t all that hard if you have understood the basics of SVM and SVM optimization). :-)

##### Part 2: 
Repeat the same experiments as you did for part 1 but now using a different dataset binclassv2.txt.
Looking at the results of both the parts, which of the two models (generative classification with Gaussian class-
conditional and SVM) do you think seems to work better for each of these datasets, and in general?
