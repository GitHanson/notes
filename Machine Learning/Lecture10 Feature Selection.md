## Lecture10 Feature Selection

### Choosing a good feature set

#### "Wrapper" methods

- Choose **subset** of attributes that give **best performance** on the development data (with respect to a single learner)
- • Evaluate model on {Outlook}
  • Evaluate model on {Temperature}
  • ...
  • Evaluate model on {Outlook, Temperature}
  • ...
  • Evaluate model on {Outlook, Temperature, Humidity}
  • ...
  • Evaluate model on {Outlook, Temperature, Humidity,
  Windy}
- **Best performance** on data set → **best feature set**
- Advantage:
  - Feature set with **optimal** performance on development data
- Disadvantage:
  - Takes a **long** time

#### Greedy approach

- Train and evaluate model on each single attribute
- Choose best attribute
- Until convergence:
  - Train and evaluate model on best attribute(s), plus each remaining single attribute
  - Choose best attribute out of the remaining set

- Iterate until performance (e.g. accuracy) stops increasing

-  Bad news! :
  - In practice, converges much more quickly than this
  - Convergences to a **sub-optimal** (and often very bad) solution
  - (Assumes independence of attributes)

#### "Ablation" approach

- Start with all attributes

- Remove one attribute, train and evaluate model

- Until divergence:

  -  From remaining attributes, remove each attribute, train and evaluate model
  - Remove attribute that causes least performance degredation

- Termination condition usually: performance (e.g. accuracy) starts to degrade by more than $\epsilon$

-  Good news:

  - Mostly removes **irrelevant attributes**

- Bad news:

- slower with more attributes

- not feasible on non-trivial data set

  

### In-build feature selection - "Embedded" method

- Not important

- Some models actually perform feature selection as part of the algorithm!



### Feature filtering

- evaluate each attribute, separate from other attributes
  - Consider each attribute separately: **linear time** in number of attributes



### what makes a single feature good?

- well **correlated** with interesting class
- Recall indepedence : $\frac{P(A,C)}{P(A) P(C)} = 1$  /  $P(A|C) = P(A)$
  - LHS >> 1 - attribute and class randomly
  - LHS ~ 1 - expect chance
  - LHS << 1 - negatively corrleated
- PMI(pointwise mutual information)  
  - Attributes with greatest PMI: best attributes (most correlated with class)
  - $PMI (A=a ,C=c) = log_2\frac{P(a,c)}{P(a)P(c)}$
- Well correlated with [**interesting**] class
  - Knowing $a$ lets us predict $c$ with more confidence

- **Reverse correlated** with class
  - Knowing $\bar{a}$ lets us predict c with more confidence

- **Well correlated** (or reverse correlated) with **uninteresting**
  class
  - Knowing a lets us predict $\bar{c}$ with more confidence
  - Usually not quite as good, but still useful



### Contingency tables

- compact representation of these **frequency** counts
- $\sigma$ means frequency

<img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190427003028.png" height = "100px"/>

- $P(a,c) = \frac{\sigma(a,c)}{N}$



### Mutual Inforamtion

- $MI(A,C) = \sum_{i \in \{a,\bar{a} \}} \sum_{j \in \{c,\bar{c} \}}P(i,j)log_2\frac{P(i,j)}{P(i)P(j)}$



### Chi-square

<img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190427004050.png" height = "100px"/>

- $X^2 = \sum_{i=1}^r\sum_{j=1}^c \frac{ (O_{i,j} - E_{i,j}) ^2}{E_{i,j}} $



### Types of Attribute(Summary)

#### nominal attribute(e.g. Outlook = {sunny, overcast, raniy})

1. Treat as **multiple binary attribute**(one-hot)

2. modify **contigency tables**
   - MI(O,C)

3. **Chi-square**

#### Continuous attribute(e.g. Age = {1,2,3,4,5,6,7,...})

- Probabilities can be estimated by fittting a **Gaussian**
- The values can be **discretised**

#### Ordinal attributes(low,med,height or 1,2,3,4)

1. Treat as **binary**
2. Treat as **continuous**
3. Treat as **nominal**



### multiple-class

- What makes a single feature good?
  - Highly correlated with class
  - Highly reverse correlated with class
  - Highly correlated (or reverse correlated) with not class

- What makes a feature bad?
  - Irrelevant
  - Correlated with other features
  - Good at only predicting one class (but is this truly bad?)