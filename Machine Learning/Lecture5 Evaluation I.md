## Lecture05 Evaluation I

### Evaluating Classification

- Main idea:
  - *Train* (**build** classifier) using **training data**
  - *Test* (**evaluate** classifier) on **testing data**

- Testing on the training data:
  - Train and evaluate using all of the instance
  - Tends to **over-estimate** classifier performance
  - In fact, tell the classifier what correct answers are



### Evaluation Strategy

- **"Holdout"** evaluation strategy
  - Each instance is **randomly assigned** as either a training or testing instance
  - **No overlap** between dataset
  - Very **commonly** **used** strategy
  - <u>*Advantages*</u>*:*
    - **Simple** to implement
    - **High producibility**
  - <u>*Disadvantages*</u>:
    - **Size of the split** affects classifier behaviour
    - Lots of test instances, few training instances -> no enough information to build an accurate model
    - Lots of training instances, few testing instance -> test data may not be representative (performance can be too hight/ too low)

- **Reapted Random Subsampling** evaluation strategy
  - Like holdout, but **iterated multiple times**
  - Evaluate by **averaging**
  - <u>*Advantages*:</u>
    - Averaging Holdout tends to produce **more reliable** result
  - <u>*Disadvantages*:</u>
    - **Hard to reproduce**
    - **Slower**
    - **wrong** choice of **spliting ratio** lead to **highly misleading results**
- **Cross-Validation**
  - Data split into ***m* partitions**
  - Evaluation metric is **aggregated** across *m* test partitions
  - *<u>Why is better than Holdout/Repeatd Random Subsampling?</u>*
    - **Every** instance is a **test instance**
    - Takes the **same** time as Repeated Random Subsampling
    - Very **reproducible**
    - Minimise **bias** and **variance**
  - <u>*How big is m?*</u>
    - **Numbers** m  **impacts** **runtime** and **size** of data set
    - Common : 5
    - **Leave-One-Out** Cross-Validation
      - **m = N**
      - **Maximises** **traing** **data**
      - **Too slow**



### Stratification

- **Inductive Learning Hypothesis**
  - Any hypothesis can approximate target function well over (a sufficiently large) training data set will also approximate the target function well over unseen test examples
- **Inductive bias**
  - **Assumption must be made** to build model and make prediction
  - **Different assumption** lead **different predictions**
  - **Empirical problem**

- **No free lunch in supervised learning**
  - The only way to guarantee optimal performance over an unseen test set is to know a prior what the unseen data set looks like
- Assume **class distribution** of seen and unseen data set are the **SAME**
-  Ensure training and test data **both** have **SAME** class distribution



### What is  good classifier?

- **Acuracy**
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428120720.png" height = "50px"/>
  - How frequently** the classifier is **correct**

- **Confusion Matrix**
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428124804.png" height = "100px"/>
  - $ACC = \frac{TP + TN}{TP + FP + FN + TN}$
  - $ER = \frac{FP+FN}{TP + FP + FN + TN}$

- N.B. $ER = 1 - ACC$
- **Error rate reduction** (ERR)
  - **Compare** $ER$ for a **given method** with $ER_0$ for an **alternative method**
  - $ERR = \frac{ER_0 - ER}{ER_0}$



### Precision and Recall

- **Precision**
  - **How often** are we correct
  - $Precision = \frac{TP}{TP+FP} $ = **# of true on I / # of prediction is I**
- **Recall**
  - **What proportion** of we corect identified interesting class
  - $Recall = \frac{TP}{TP+FN}$ = **# of true on I / # of exactly I has**

- **Inverse Relationship** for P/R
- But, we want **both** high —> **F-score**
  - $F_\beta = \frac{(1+\beta^2)PR}{\beta^2P + R}$



### Multi-class Evaluation

- **macro-averaging**
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428130627.png" height = "100px"/>
- **micro-averaging**
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428130705.png" height = "100px"/>

- **weighted averaging**
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428130802.png" height ="100px"/>

### Baseline vs.  Benchmarks

- **Baseline** = naive method

- **Benchmark** = reval technique

- Random Baseline

  - **Method 1**: randomly assign a class to each test instance
    - dumb and simple
  - **Method 2**: randomly assign a class $c_k$ to each test instance, weighting the class assignment accroding to $P(c_k)$
    - Assume we know prior prob $P(c_k)$

- **Zero-R**

  - **Majority class** baseline

- **One-R**

  - Create "Decision stump" for each attribute, populate the leaf with the majority class
  - select stump which leads to the **lowest error rate** over the traing data
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428131547.png" height ="300px"/>
  - *<u>Advantages</u>*:
    - **Simple** to understand and implement
    - **Simple** to comprehend the result
    - **Surprisingly good results**

  - <u>*Disadvantages*</u>:
    - **Unable** to captue **attribute interactions**
    - Attributes with many values takes **bias**