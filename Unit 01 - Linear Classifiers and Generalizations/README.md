# Unit 01 - Linear Classifiers and Generalizations
[[MITx 6.86x Notes Index]](https://github.com/Amit10311/MITx-6.86x-Machine-Learning-with-Python) 
## Course Introduction

There is a relatively small toolkit of algorithms you need to learn to understand how these different applications can work so nicely and be integrated in our daily life.

The course covers these 3 topics

**Supervised Learning**
- Make predictions based on a set of data for which correct examples are given
- E.g. Attach the label "dog" to an image, based on many couple (image/dog label) already provided
- The correct answers of the examples provided to the algorithm are already given
- What to produce is given explicitly as a target
- First 3 units in increasing complexity from simple linear classification methods to more complex neural network algorithms

**Unsupervised Learning**
- A generalisation of supervised learning
- The target is no longer given
- "Learning" to produce output (still at the end, "make predictions"), but now just observing existing outputs, like images, or molecules
- Algorithms to learn how to generate things
- We'll talk about probabilistic models and how to generate samples, mix and match (???)

**Reinforced Learning**
- Suggest how to act in the world given a certain goal, how to achieve an objective optimally
- It involves making predictions, aspects of SL and UL, but also it has a goal
- Learning from the failures, how to do things better
- E.g. a robot arm trying to grasp an object
- Objective is to control a system

Interesting stuff (solving real problems) happens at the mix of these 3 categories.

## Lecture 1. Introduction to Machine Learning
[Slides](https://github.com/sylvaticus/MITx_6.86x/blob/master/Unit%2001%20-%20Linear%20Classifiers%20and%20Generalizations/Slides%20lecture%2001.pdf)

### 1.5. A Concrete Example of a Supervised Learning Task

Let's consider a movie recommender problem.
I have a set of movies I've already seen (the **training set**), and I was to use the experience from those movies to make recommendations of whether I would like to see tens of thousands of other movies (the **test set**).

We will compile a **feature vector** (a binary list of its characteristics.. genre, director, year..) for each movie in the training set as well for those I want to test (we will denote these feature vectors as $x$).


Now I have the training set (feature vectors with associated labels), but I really wish to solve the task over the test set.
It is this discrepancy that makes the learning task interesting. I wish to generalize what I extract from the training set and apply that information to the test set.
