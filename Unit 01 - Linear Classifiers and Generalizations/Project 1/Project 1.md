The goal of this project is to design a classifier to use for sentiment analysis of product reviews. Our training set consists of reviews written by Amazon customers for various food products. The reviews, originally given on a 5 point scale, have been adjusted to a +1 or -1 scale, representing a positive or negative review, respectively.

Below are two example entries from our dataset. Each entry consists of the review and its label. The two reviews were written by different customers describing their experience with a sugar-free candy.


![Screenshot from 2023-02-28 17-15-04](https://user-images.githubusercontent.com/20908007/221912373-82d80fe1-bbf7-40b3-8b2f-bcc0c5757634.png)

In order to automatically analyze reviews, you will need to complete the following tasks:

* Implement and compare three types of linear classifiers: the perceptron algorithm, the average perceptron algorithm, and the Pegasos algorithm.

* Use your classifiers on the food review dataset, using some simple text features.

* Experiment with additional features and explore their impact on classifier performance.

# 2. Hinge Loss

In this project you will be implementing linear classifiers beginning with the Perceptron algorithm. You will begin by writing your loss function, a hinge-loss function. For this function you are given the parameters of your model $\theta$ and $\theta_0$ . Additionally, you are given a feature matrix in which the rows are feature vectors and the columns are individual features, and a vector of labels representing the actual sentiment of the corresponding feature vector.



"In this problem, you will need to adapt this update rule to add a bias term () to the hypothesis, but take care not to penalize the magnitude of ."

# Setup Details:

For this project, you will need the NumPy numerical toolbox, and the matplotlib plotting toolbox.

* https://numpy.org/doc/stable/user/absolute_beginners.html

* https://nbviewer.org/github/jrjohansson/scientific-python-lectures/blob/master/Lecture-4-Matplotlib.ipynb
