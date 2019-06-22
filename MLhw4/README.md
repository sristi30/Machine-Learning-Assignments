### Homework 4

##### Programming Problem 1
For this problem, your task is to implement a simplified version of the Probabilistic
PCA (PPCA) model and play with it on a dataset of face images. The provided dataset contains a total of 165
face images of 15 individuals. Each image is 64x64 grayscale. So X is 165 × 4096 (N = 165, D = 4096).
2The first simplication will be that we will assume σ 2 = 0 and the second simplification will be that we will
use ALT-OPT instead of EM. The overall algorithm will basically be a simpler version of the algorithm given
on slide 10 of lecture 18. Since you are using ALT-OPT instead of EM, you don’t even have to compute the
posterior or the expectation of the latent variables. It is really that simple! :-) You will effectively be doing PCA
but using ALT-OPT instead of eigendecomposition! The ALT-OPT algorithm will alternate between estimating
Z given W, and W given Z. If using MATLAB, this shouldn’t need more than 8-10 lines or code (likewise for
Python). You will run your ALT-OPT algorithm for a fixed number of iteration (100 iterations), though it might
converge to a reasonable solution in fewer iterations.
Run your implementation with K = 10, 20, 30, 40, 50, 100 and using all the data (165 images). After the model
has been learned, for each value of K, reconstruct any 5 of the images (of your choice!), using μ (this will
be equal to the sample mean), W, and the latent code of the corresponding image, and visually inspect the
reconstructed images (note: to show the image, you will have to reshape x̂ n as 64 × 64), comparing them with
their original versions. Note that, the reconstruction of an image x n will be x̂ n ≈ μ + Wz n .
Note: You should reconstruct the same 5 images for each value of K. The goal is to see how (or whether)
increasing K improves the reconstruction (or not). What do you observe visually as K increases? Does the
reconstruction get better or worse? Briefly explain the reason for what you observe.
For each K, also show 10 of the basis images (columns of the W matrix, each reshaped as 64×64) that you think
look sort of interesting (for K = 10, it will mean showing all the columns of W; for K = 20, 30, 40, 50, 100,
you will need to select a subset of 10 columns from W and show those).
Deliverables: Submit your code (named ppca altopt.py or ppca altopt.m) and the images (for each
K, the 5 original and reconstructed images, and the 10 basis images). Everything should be zipped together in
a single file (following the naming conventions as in previous homework). Also include these images and your
experimental observations in the main PDF writeup (you can scale the sizes of images to be small enough so
that they don’t take too much space in the PDF).

##### Programming Problem 2 You are provided a subset of the MNIST data consisting of 10,000 images of digits
0-9. Each image is of size 28 × 28 (784 dimensional). The dataset also contains the digit labels.
Your goal is to run K-means clustering on two-dimensional embedding of this data. To get the two-dimensional
embeddings, you will use two approaches: PCA and tSNE. You can use any implementation of PCA and
tSNE, e.g., from sklearn if you are using Python (don’t need to implement any of these) or any MATLAB
implementation. If you want, you can use this very nice tSNE implementation (available in several langugages)
from this webpage: https://lvdmaaten.github.io/tsne/. For PCA, you can even use your code
from part 1 with the number of latent factors set to 2. You also don’t need to implement K-means on your own
(you already did it in HW3). You can use any existing implementation of K-means.
Run K-means with K = 10 for both cases (PCA based 2D embeddings and tSNE based 2D embeddings), using
10 different initializations and show the clustering results in form of the plots of the obtained clusterings with
each cluster shown in a different color. Visually, which of the two 2D embedding methods (PCA/tSNE) seems
to work better for the clustering task?
