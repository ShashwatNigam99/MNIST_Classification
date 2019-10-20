# MNIST Handwritten Digits Classification using various classifiers
![Alt text](./digits.png)
## Dataset
Using a subset of the extremely popular simple data set MNIST. This data set has many images of handwritten digits 0 to 9. i.e., 10
classes. Each image is of size 28 ×28. In our subset there are 7000 images in total from 10 classes, out of which 6000
are for training and 1000 are for testing.

## Classification Methods

### Probabilistic methods of classification
- Maximum Likelihood Estimate (MLE) 
- Maximum A Posteriori (MAP)
- Bayesian Pairwise Majority Voting
- Simple perpendicular bisector based Majority Voting

#### Analysis of accuracies obtained from the above methods
* MLE has a bad performance (accuracy = 74.3) since the estimation is based on the information received from the training set. The parameters mu and sigma for the 2-D Gaussian curve are fixed based on the training set. The parameters are not tuned to any data from the test set. Therefore, as a result of overfitting on the training set/less generality, the accuracy is low. If the training set would have been a better representative of the overall distribution of data samples, accuracy would have been better for test set also.

_Prior for MAP : 1/10 as there are are 10 classes of digits and all digits are equally probable_

* MAP has accuracy similar to MLE(accuracy = 74.3) due to similar reasons. The priori assumption does not have an affect on the accuracy since it gives equal probability to all classes.


* Pairwise bayesian method has the best accuracy (accuracy = 83.8) across all methods. It uses a common sigma value, and unique mean value for any pair of classes. This takes into consideration the means of the classes and also the covariance(though averaged), hence the spread of the data gets accounted for too. Doing a majority vote across all classes reduces error (in classification) as much as possible hence gaining more accuracy than MLE and MAP.


* Perpendicular bisector method has a little better performance (accuracy = 77) as compared to MLE and MAP but lesser than Pairwise bayesian method. Since it uses only distance of the mean point of every class, it does not incorporate sufficient information about the spread of the data in each class, as Sigma is not considered, hence has lesser accuracy than Pairwise Bayesian. Doing a majority vote across all classes reduces error (in classification) as much as possible hence gaining more accuracy than MLE and MAP.

### Nearest Neighbour based methods
- K nearest neighbour algorithm
- Reverse NN based outlier detection

#### Performance analysis for various k and optimal k
* The accuracies are different owing to the different position and the clustering of the images in the test set when compared to the training set. 
* For higher K values we take more neighbours into account and hence arent completely dependent on the nearest neighbour. 
* Graphically, our decision boundary will be more jagged as the small K would be blind to the overall distribution. On the other hand, a higher K averages more voters in each prediction and hence is more resilient to outliers. Larger values of K will have smoother decision boundaries.
* We can identify the best K based on our understanding of the data, and a binary search approach. This is because the accuracy gets worse as we move away from K on either side. We can think of this similar to the underfitting/overfitting problem.
