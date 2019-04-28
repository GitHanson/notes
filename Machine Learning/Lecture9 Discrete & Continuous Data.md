## Lecture09 Discrete & Continuous Data

### Supervised ML Recap:

- Class is **nomial** : <u>Classfication</u>
  - Naive Bayes, 1-R, Decision Trees : all attribute are **noimal**
  - K-Nearest Neighbour, Nearest Prototype, Suport Vector Machines : all attribute are **numeric**
  - 0-R: who cares about attribute?
- Class is **numeric** : <u>Regression</u>



### Our attribues are nomial, But learners are numeric

- nomial — <u>alter data</u> —> a format suitable for **K-NN, NP, SVM**
- For K-NN and NP, use **Hamming distance**:

$$
d_H(A, B) = \sum_{i}\begin{cases}
    0, & \text{if $ a_i ==  b_i$}.\\
    1, & \text{otherwise}
    \end{cases}
$$

- method 1 : **randomly assign numbers** to attribute values
  - if **scale is constant** between attributes, this is *not bad*
  - *Worse* with **high-parity** attributes (more attribute values)
- method 2 : **“One-hot encoding”**
  - If nominal attribute takes *m* values, replace it with *m* Boolean attributes
  - Example : 
    - hot = [1, 0, 0]
    - mild = [0, 1, 0]
    - cool = [0, 0, 1]
  - solves the problem of nominal attribute by <u>massively increasing the feature spaces</u>



### Our attributes are numeric, But leaners are nominal

- Example : Naive Bayes

  - **Multivariate** NB : attributes are nominal, and can take **any number** of values
  - **Binomal** NB : attributes are **binary** (special case of MV)
  - **Multinomial** NB : attributes are **nature number**
  - **Gaussian** NB : attributes are **real number**

  <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426141907.png" height="240px"/>



- Example Decision Tree
  - popular strategy is **Binarisation**:
    - Each node is labelled with $\alpha_k $, and has two branches:  one is.$\alpha_k \leq m$, one is $\alpha > m$
    - Info Gain/ Gain Ratio must be calculated at each split point



### What is Discretisation?

- **Discretisation** is the translation of **continuous** attributes <u>onto</u> **nomial** attributes

- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426143545.png" height = "100px"/>

  - Step1 :  how many values = {${(x_0, x_1], (x_1, x_2],…, (x_{n-1}, x_n]}$}
  - Step2 : map each continuous value to discrete value
  - <u>*Advantages*</u>:
    - **Simple** to implement
  - <u>*Disadvantages*</u>:
    - **Loss of generality**
    - no sense of "numeric ordering"
    - **overfitting**

  

### Unsupervised Discretisation (ranges)

- **equal width**
  - Partition the values into **bins** of **equal size**
  - partition the overall spacce into n equals intervals = **<u>equal width</u>**
  -  <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426144645.png" height = "80px"/>
  - $ (83 - 64) / 3 = 6.333$ ,  [64,70]  [71,77]  [78,85]
  - <u>*Advantages*</u>:
    - **simple**
  - <u>*Disadvantages*</u>:
    - **badly** effected by **outliers**
    - **arbitray** **n**
- **equal frequency**
  - Sort the values and identify breakpoints which produce n equal-sized partitions = **<u>equal frequency</u>**
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426153313.png" height = "80px"/>
  - <u>*Advantages*</u>:
    - **simple**
  - <u>*Disadvantges*</u>:
    - **arbitray n**



### K-means Clustering

- k-mean can requrie any number of iterations up to C(n, k) to converge
- or never converge
- One typical improvement: runs multiple times k-means
- Weaknesses:
  - need multiple runs to have any certainty about convergence
  - random behaviour
  - sensitive to outliers
  - still need to know number of intervals (k)



### Naive Supervised  Discretisation

- Step1: Sort the values and identify breakpoints in class membership
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426154422.png" height = "70px"/>
- Step 2 : Reposition any breakpoints where there is no change in numeric value:
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426154528.png" height = "70px"/>

- Step 3: Set the <u>breakpoints</u> midway between the neighbouring values
- <u>*Advantages*</u>:
  -  simple to implement
- <u>*Disadvantages*</u>:
  -  usually creates too many categories (overfitting)
- Modified procedure to <u>avoid overfitting</u> **(v1**): 
  - **delay inserting a breakpoint** until **each “cluster” contains at least n instances** of a single class:
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426154930.png" height = "70px"/>
- Modified procedure to <u>avoid overfitting</u> (v2):
  -  **merge neighbouring clusters** until they reach **a certain size/at least n instances** of a single class:
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426155049.png" height ="70px"/>



### Probability Density Functions

- For numerical attributes, we assign probabilities to range:
  - $P(a_k \in [2.06, 3.12] | Y) = 0.38$
  - $\int_{2.06}^{3.12} pdf(a_k = x; c_j)dx = 0.38$
- PDF is based on the **Gaussian distribution(normal distribution)**
- $f(x) = \frac{1}{\sqrt{2\pi\sigma}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ where $\sigma$ is std and $\mu$ is mean
- Why Gaussians?
  - In practice, a normal distribution is approximation for many events
    - including binomial, poisson, chi-square...
    - e.g. height, weight, age..

<img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426161324.png" height = "200px"/>

