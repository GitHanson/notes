# Lecture 08 Support Vector Machine



###  What is a Support Vector Machine?

- The goal is to find a **hyperplane** that **separates** <u>two</u> classes<img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/Screen%20Shot%202019-04-26%20at%204.27.33%20am.png" height="240px"/> 

- Linear separability:
  - linearly separable
  - not linearly separable



### Linear Classifiers

- a seprarting hyperplane in D dimensions can be defined by a **normal** **w** and **intercept** **b**
- hyperplane equation **f(x) =  w • x + b = 0**
  - **w<sup>T</sup>x** = w<sub>1</sub>x<sub>1</sub>+w<sub>2</sub>x<sub>2</sub>+…+w<sub>m</sub>x<sub>m</sub> = **w • x**
  - "*" means dot product

- the training data is used to learn **w**



### SVMs: Maximum Margin

- one solution ——>  lots more solutions
- Margins:
  - point A ——> quite confident in prediction
  - point C ——> less confident in prediction



### Soft margins

* trade-off between the Margin and the number of mistakes on the training data<img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426050842.png" height = "180px" /> 



### SVM-based Classification

* one class as postive(+1), one as negative(-1)
* find the best hyperplane **w** and b which maximizes the margin between the positive and negative traing instance



### Learning the SVM

- for small traning sets — we can use a **naive** training model (too expensive!)
- if the data isn't  linearly separable
  - applying a **mapping function** to transform data
  - Kernal function  ⧲ :ℝ<sup>𝑛</sup>→ℝ<sup>m</sup>
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190426051719.png" height = "300px"/>



### Formal specification of SVM

- {X<sub>k</sub>} traning vector, {y<sub>k</sub>} ∈ {-1,1} class labels

- The hyperplane separating the two classes can be represented as: **w<sup>T</sup>x + b =  0 ** (assume two classes are linearly separable)
- such that
  * **w<sup>T</sup>x<sub>k</sub> + b ≥  1** for y<sub>k</sub> = +1
  * **w<sup>T</sup>x<sub>k</sub> + b ≤  -1** for y<sub>k</sub> = -1
- **"Support Vectors"**
  - Objective is to find the data points act as the boundaries of the two classes
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



### Multiple Class for SVM

- Most common approaches to extending to multiple classes:
  - One-vs-All : choose which classifers test data with point with greatest margin
  - One-vs-One : choose selected by most classifiers

- Traning time a serious issue