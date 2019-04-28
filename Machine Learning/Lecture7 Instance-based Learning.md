## Lecture07 Instance-based Learning

### Similarity

- **Jaccard Similarity**
  - $sim(A,B) = \frac{|A \cap B|}{|A \cup B|}$
- **Dice Coefficient**
  - $sim(A,B) = \frac{2|A \cap B| }{|A|+|B|}$

### Feature Vectors

- **n-dimensional vector of features** that represent some object
- Featrues may be **nominal/categorical/discrete**
  - e.g. colour, gender
- Features may be **ordinal**
  - e.g. cool< mild< hot
- Features may be **numeric/continuous**
  - e.g. height, age
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428152634.png" height = "200px"/>
- **Similarity**
  - numerical measure of **how alike two data objects are.**
  - **higher** when more alike
  - falls in range **[0,1]**

- **Dissimilarity**

  - numerical measure of **how different two data objects are.**
  - **lower** when more alike

  - MIN = 0
  - no upper limit 



### Distance

- **Euclidean Distance**
  - $d(A,B) =\sqrt{\sum_{i=1}^n(a_i-b_i)^2}$
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428153815.png" height = "200px"/>
- **Manhattan Distance**
  - $d(A,B) = \smash{\displaystyle \sum_{i=1}^n |a_i-b_i|}$
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428153938.png" height = "200px"/>

- **Cosine Similarity**
  - $cos(P,Q) = \frac{p \cdot q}{|p||q|} = \frac{\sum_ip_iq_i}{\sqrt{\sum_ip_i^2}\sqrt{\sum_iq_i^2}}$
  - Items $P$, $Q$ and theri feature vectors $p$ and $q$
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428154303.png" height = "200px"/>



### Nearest Neighbour

- **The cloest point** = $ d(x,y) = min(d(x,z)|z \in Y)$ = MIN Sim or MIN distance
- **K neighbours**
  - k = 1
    - 1-NN
    - intuced **decision boundary**
    - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428154606.png" height = "200px"/>
  - k > 1
    - K-NN algorithms
    - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428154644.png" height = "200px"/>
  - Weighted KNN
  - Offset-weighted K-NN



### Weighting Strategies

- **Majority class** - equal weight

- **Inverse linear distance** (ILD)

- $$
  w_j =\begin{cases}
  \frac{d_k-d_j}{d_k-d_1} if \ d_j \neq d_1 \\
  			1     \hspace{19pt} if d_j = d_1                    
        \end{cases}
  $$

- **Inverse distance** (ID)
  $$
  w_j = \frac{1}{d_j+\epsilon}
  $$
  

- **Breaking Ties** - solve **equal** number of votes
  - Random tie breaking
  - Take class with **highest** prior probability
  - See if the addxition of the k+1th instance(s) break the tie



### Choosing the Value of k

- **smaller value** of k == lead ==> **lower performance** due to noise(overfitting)
- **larger value** of k == lead ==> **drive the performance** toward **Zero-R** performance
- **Try k**, but **odd value**



### Strengths and Weaknesses of NN methods

- *<u> Strengths:</u>*
  - **Simple**
  - Can handle **arbitrary many classes**
  - **Incremental**

- *<u>Weaknesses:</u>*
  - need a **useful distance function**
  - need an **averaging function** for combining the labels of multiple training examples
  - **Expensive**
  - **Lazy leaner**: **Everything** is done at **run time**
  - Prone to **bias**
  - **Arbitrary** **K** value