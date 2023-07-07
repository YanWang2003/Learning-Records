# I. [A Survey about Deep Long Tailed Learning](https://arxiv.org/pdf/2110.04596.pdf)
## Re Sampling
* * *
### Class Rebalance
Change the origin samples into a new set which decrease the degree of long tailed. 
### Class Sensitive Learning
Make the loss function can adapt different classes. i.e. the loss weight increased when the sample belongs to a class which have few samples or the margin changed when facing samples from different classes.
### Logit Adjustment
Adjust the log loss function. i.e. cross entropy loss function
* * *
## Information Augmentation
* * *
### Transfer Learning
Using some knowledge or models which already exist.
### Data Augmentation
- Rotate
- Flip
- ranslate
* * *
## Module Improvement
* * *
- Representation Learning : Translate original data into a new data which can represent its features more precisely 
- Ensemble Learning
***
```mermaid
graph TB
		zero(Deep Long Tailed Learning)
		zero --> one_1(Re Sampling)
		zero --> one_2(Information Augmentation)
		zero --> one_3(Module Improvement)
		one_1 --> two_1(i.e. Balance the Dataset, Give Each Sample a Specific Weight to Train)
		one_2 --> two_2(i.e. Use Some Prior Knowledge, Rotate the Imagine)
		one_3 --> two_3(i.e. Translate the Origin Features into a New Form or Use Ensemble Learning)
```
* * *
# II. [Learning to Re-weight Examples with Optimal Transport for Imbalanced Classification](https://arxiv.org/pdf/2208.02951.pdf)
## Main Idea
We have two types of datasets, one is called training set while the other is called meta set. Samples in the training data follows the long-tailed distribution and every sample in it has different weight. On the contrary, samples in meta set is class balance and every sample has the same weight. Our goal is to train the weight and use the weight to construct a specific loss function to train a better classifier.
* * *
## Workflow
We have basic loss function for each sample $\ell (y, f(x;\theta ))$
1. Update $\theta$ through training set and $L1 = \Sigma \ell (y_{train}, f(x_{train};\theta ))$ for $t_1$ iterations.
2. Update $\theta$ and $\omega$ for $t_2$ iterations as followed:
- Sample a mini batch $B$ from training set
- Update $\theta$ through training set and $L1 = \Sigma_{B} \omega_i \ell (y_{i}, f(x_{i};\theta ))$
- Update $\omega$ through OT
- Update $\theta$ through new $\omega$
* * *
# III. [Balanced MSE for Imbalanced Visual Regression](https://arxiv.org/pdf/2203.16427.pdf)
## Main Idea
Balanced MSE use the thought of MSE to propose a new loss function. This method did some hypothesis and definitions.

**i.e,**
- the training set is unbalanced while the test set is balanced (they are all infinite set)
- the joint distribution of x, y on train set and test set is equal
- $p_{bal}(y|x;\theta)$ follows the gaussian distribution.
## Loss Function
$L = -log\frac{exp{(-||y_{pred}-y||_2^2/\tau)}}{ {\textstyle \sum_{y'\subseteq B_y}^{}} exp{(-||y_{pred}-y'||_2^2/\tau)}}$
