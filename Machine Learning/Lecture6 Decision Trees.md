## Lecture06 Decision Trees

 ### IDA3 Algorithm

- Decision stumps act by **1-R**
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428134621.png" height = "300px"/>
  - $Total errors = 0$
  - $Yes: (outlook = sunny ∧ humidity = normal) ∨(outlook = overcast) ∨(outlook = rainy ∧ windy = false)

- Criterion for Attribute Selection
  - We wan to get the **smallest tree** (Occam’s Razor)
  - In favor :  Fewer short hypotheses than long hypotheses



### Entropy

- A measure of **unpredictability**
- $H(x) = -\smash{\displaystyle \sum^n_{i=1}P(i)log_2P(i)}$  ( in bits )
- If **most** of the probability mass is assigned to **a single event:**
  - Entropy is **low**
  - The event is **predictable**
- If the probability mass is **evenly divided** between **many**
  **events**:
  - Entropy is **high**
  - The event is **unpredictable** 



### Information Gain (IG)

- **Know** the value of an attribute —-cause—> **expected reduction** in entropy
- **Mean Information** in tree stump
  - $Mean Info(x_1,…,x_m) =   \smash{\displaystyle \sum^m_{i=1}P(i)H(x_i)}$
  - average entropy over the children after split
- IG given **difference** between the root entropy and mean information
- $IG(R_A|R) = H(R) - MI = H(R) - \smash{\displaystyle \sum^m_{i=1}P(i)H(x_i)}$
- IG prefers highy-branching attributes
  - <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428141619.png" height = "250px"/>
  - But may result in **overfitting/fragmentation**



###Gain Ratio (GR)

- reduces the **bias** for IG towards highly-branching attributes by normalising ralative to the **split information**
- **Split info**(SI) : entropy of given split
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190428145619.png" height = "100px"/>
  - $P(x_i)$ = # of $x_i$ / # of instance



### Stopping criteria

- recurse until the **instance at a node** are of **the same class**
- If all instances are of a single class -> **entropy = 0**
- Consider other attributes can not improve an entropy of 0 -> **IG = 0**



### Practical Properties of ID3 DT

- Basic **supervised** learner
- **Fast** to train and classify
- **easy effec**t by **irrelevant** features
- some tricks to deal with missing/continuous feature values

###Other algorithms

- Oblivious Decision Trees 
- Random Tree