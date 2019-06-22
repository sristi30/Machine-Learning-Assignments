### Homework 1

Your task is to implement and test prototype based classification using the provided
dataset (“Animals with Attributes” version 1 - AwA v1). You may download the dataset (given in MATLAB
and Python format) using this link: https://tinyurl.com/cs771-a18-hw1data (caution: the data
is in a couple of hundred MBs; there is also a README file that contains the description of the data). In this
dataset, each input represents an image of an animal and output is the class (what this animal is). The dataset
has a total of 50 classes and the number of features for each input is 4096 (note: these features were extracted
by a deep learning model and you don’t need to perform any other preprocessing of features for this problem).
However, we are going to give a small twist to the basic prototype based classification problem. The training
set provided to you has only examples from 40 of the classes. We will refer to these 40 classes as “seen classes”
(have training data for these classes) and the remaining 10 classes as “unseen classes” (do not have training data
for these classes). The test inputs will be only from these 10 unseen clases.
Recall that prototype based classification requires computing the mean of each class. While computing the
means of the 40 seen classes is easy (since we have training data from these classes), what we actually need is
the mean of the remaining 10 classes (since these are our test classes). How do we get these means?
3Well, we clearly need some additional information about the classes in order to solve this problem (without
that there is no hope of solving this problem). To this end, you are provided an 85-dimensional class attribute
vector a c ∈ R 85 , for each class c (both seen as well as unseen classes). Each class attribute vector contains
information about that class and consists of 85 binary-valued attributes representing the class (e.g., whether this
animal has stripes). You may think of each a c as a class feature vector which tells us what the class looks like.
Now consider two ways how these class attribute vectors can be used to obtain the means of unseen classes:
• Method 1: Model the mean μ c ∈ R 4096 of each unseen class c (where c = 41, . . . , 40) as a convex
combination of the means μ 1 , . . . , μ 40 of the 40 seen classes (again note that μ 1 , . . . , μ 40 can be computed
easily since we do have training data from these 40 classes)
μ c =
40
X
s c,k μ k ,
c = 41, . . . , 50
k=1
where s c = [s c,1 , s c,2 , . . . , s c,40 ] is a vector of similarities of the unseen class c with each of the 40 seen
classes. Here each similarity is defined as the inner product of the class attribute vectors of two classes,
is the similarity between two clases c and k. Note: We will also normalize the vector s c
e.g., s c,k = a >
c a
P k 40
as s c,k = s c,k / `=1 s c,` so that it sums to 1 (and thus can be used as weights in the convex combination
defined above). This procedure will give us the means of 10 unseen classes and then you can apply the
prototype based classifer to predict the labels of each test input.
• Method 2: Train a linear model that can predict the mean μ c ∈ R 4096 of any class using its class attribute
vector a c ∈ R 85 . We can train this linear model using {(a c , μ c )} 40
c=1 as our training data and then apply
it to predict μ c for each unseen class using its class attribute vector a c . Note that this can be posed as
a multi-output regression problem μ c = Wa c where a c ∈ R 85 is the input, μ c ∈ R 4096 is the vector-
valued regression output, and W is 85 × 4096 matrix of weights that need to be learned. The solution to
−1 >
this multi-output regression problem is W = (A >
s A s + λI) A s M s where A s is the 40 × 85 matrix
containing the class attribute vectors of 40 seen classes, and M s is the 40 × 4096 matrix containing the
means of the 40 seen classes. Once you have W, you can compute the mean μ c of any unseen class as
Wa c where a c is its class attribute vector. This procedure will give us the means of 10 unseen classes
and then you can apply the prototype based classifer to predict the labels of each test input.
You task is to implement both methods. In your main write-up, report the test-set classification accuracy for
each by comparing the respective model’s predictions with the provided ground truth labels (accuracy is the
percentage of test inputs with correctly predicted classes). For method 2, try λ = 0.01, 0.1, 1, 10, 20, 50, 100
and report the test accuracy for each value of λ. Which value of λ gives the best test set accuracy?
Note: In the dataset folder, I’ve also provided a brief pseudo-code (or rather a summary) of the procedure to
follow for the implementation (since this is the very first assignment, I felt it would be helpful for you all).
Important: To predict the class of a test input, you should only compute its distances from the means of 10
unseen classes, not from the means of the seen classes (since the test data only consists of inputs from the unseen
classes). The other setting where the test data can consist of both seen and unseen class inputs is also possible
but we are not considering it here.
