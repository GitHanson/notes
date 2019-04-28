## Lecture 08 Support Vector Machine

### Nearest Prototype Classification

- Step 1 : Calculate prototype for each class by averaging attribute value
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428163048.png" height ="150px" />

- Step 2: Classification is then based on some distance formula

###  What is a Support Vector Machine?

- SVM is a **non-probabilistic binary linear classifier**

- The goal is to find a **hyperplane** that **separates** <u>two</u> classes<img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/Screen%20Shot%202019-04-26%20at%204.27.33%20am.png" height="240px"/> 
- Linear separability:
  - linearly separable
  - not linearly separable
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428163801.png" height = 200px/>



### Linear Classifiers

- a seprarting hyperplane in D dimensions can be defined by a **normal** **w** and **intercept** **b**
- hyperplane equation **f(x) =  w • x + b**
  - $ w^T \cdot x = w_1x_1 + w_2x_2+w_3x_3+…+w_mx_m= w  \cdot x$
  - $b$ called $w_0$ which is a **bias**
- the training data is used to learn **w**
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428164259.png" height = "200px"/>

###SVMs: Maximum Margin

-  one solution ——>  lots more solutions
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428164404.png" height = "200px"/>
- Margins:
  - See above $\uparrow$ Point A, C
  - point A ——> quite confident in prediction
  - point C ——> less confident in prediction

- SVMs finds an **optimal solution**, Maximizes the distance between the hyperplane and "difficult" points close to decision boundary

### Soft margins

* trade-off between the Margin and the number of mistakes on the training data<img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426050842.png" height = "180px" /> 



### SVM-based Classification

* one class as postive(+1), one as negative(-1)
* Find the best hyperplane **w** and **b** which maximizes the margin between the positive and negative traing instance



### Learning the SVM

- for small traning sets — we can use a **naive** training model (too expensive!)
- if the data isn't  linearly separable
  - applying a **mapping function** to transform data
  - Kernal function  ⧲ :ℝ<sup>𝑛</sup>→ℝ<sup>m</sup>
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426051719.png" height = "300px"/>



### Formal specification of SVM

- $\{x_k\}^N_{k=1}$ a set of N traning vectors , $  \{y_k\}^N_{k=1} \in \{-1,1\}$ class labels
- (Assume two classes are linearly separable at the beginning)
- The hyperplane separating the two classes can be represented as: **w<sup>T</sup>x + b =  0 ** 
- such that
  * **w<sup>T</sup>x<sub>k</sub> + b ≥  1** for y<sub>k</sub> = +1
  * **w<sup>T</sup>x<sub>k</sub> + b ≤  -1** for y<sub>k</sub> = -1
- **"Support Vectors"**
  - Objective is to **find the data points act as the boundaries of the two classes**
  - These are referred to as the **“support vectors”**. They <u>constrain the margin</u> between the two classes.
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426053054.png" height = "400px"/>	



### Optimization: Maximizing the marigin

- we want to choose **w** so that the margin $\frac{2}{||w||}$ is **maximised**
- maximising $\frac{2}{||w||}$ is inconveninet
- so we **minmise** $\frac{1}{2}||w||^2 = \frac{1}{2}(w_1^2+w_2^2+…+w_n^2)$



###  “Slack Variable” — allow soft margin

- <u>case: two classes are **not** linearly separable</u>

- introduce a slack variables $\zeta$

- $\smash{\displaystyle\min_{w}} \frac{1}{2}||w||^2 + C\sum_{k=1}^{N}\zeta_k $

  $s.t. y_k(w^Tx_k + b) = \zeta_k -1 \geqslant 0,$

  ​	$\zeta_k \geqslant 0, \forall k \in {1 ...N}$

- The parameter C must be tuned



### Soving the optimisation problem

- Introduce Largrange multiple $\alpha_k$ for every instance in the traning set
- $\uparrow\downarrow$ no need to understand $\uparrow \downarrow$ 
- finally the classifcation function eventually becomes:
  - $f(t) = \smash{\displaystyle\sum_{i}}\alpha_iy_ix_i^Tt+b$
  - $b = y_i(1-\zeta_j) - \smash{\displaystyle\sum_{i}\alpha_iy_ix_i^Tx_j}$
- Most $\alpha_k$ are 0, the non zero values are **support vectors**
- If we need a non-linear SVM, just replace dot product with kernal function:
  - $f(t) = \smash{\displaystyle\sum_{i}}\alpha_iy_ix_i^TK(x_i,t)+b$
  - $b = y_i(1-\zeta_j)  - \smash{\displaystyle\sum_{i}\alpha_iy_ix_i^TK(x_i,x_j)}$



### Multiple Classes for SVM

- Most common approaches to extending to multiple classes:
  - One-vs-All : choose which classifers test data with point with greatest margin
  - One-vs-One : choose selected by most classifiers

- Traning time a serious issue