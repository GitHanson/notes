## Lecture12 Logistic Regression

### Log-linear models

- **linear Regression** : $\hat P(c = Y|x) = \beta · x$ 
- but **no guarantee** $\hat P \in [0,1]$
- $P(c|x) = \gamma_o · \gamma_1^{x_1} · … · \gamma_d^{x_D}$
- $logP(c|x) = log\gamma_0 + x_1log\gamma_1 + … + x_Dlog\gamma_D$
- $logP(c|x) = \beta_0 + \beta_1x_1 + … + \beta_Dx_D$ 
- $log(P) = \beta x$
- Directly fit $\beta_i ≡ log\gamma_i$
- D : number of feature values
- $ P = e^{\beta x}$



### Logistic Regression

- logit function
  - $logit(P) = log\frac{P}{1-P}$
  - $logit(1-P)  = -logit(P)$
- $P(c|x) = \frac{1}{1+e^{-(\beta_0+\beta_1x_1+…+\beta_DxD)}}$
- $P(c|x) = \frac{1}{1+e^{-(\beta x)}} \ where P \in [0,1] for \ all\  \beta · x$
- $P(c_j|x_1,x_2,…x_D;\beta) = h_\beta(x)$
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190427160715.png" height = "200px"/>
  - Positive $ β · x$ means class is Y
  - Negative $β · x$ means class is N

- In Logistic Regression, we model $P(c_j|x_1,x_2,…,x_D)$ directly; no need extimate P(x|x)

  



### Training a Logistic regression model

- How do we determine $\beta$ ?
  - Gradient Descent
  - but need error function
- goal : choose $\beta$
- $P(Y|X;\beta) = \smash{\displaystyle \prod^N_{i=1}h_\beta (x_i)^ {y_i} * (1-h_\beta(x_i))^{1-y_i}} $ 
- Log-likelihood
  - $logP(Y|X;\beta ) = \smash{\displaystyle \sum_{i=1}^N y_ilog h_\beta(x_i)+ (1-y_i)log(1-h_\beta(x_i))}$



### Multi-class classification

- Take one class (“pivot”)

- For every other class (“Y”), build regression model compared to pivot class (“N”)

- End up with (|C| − 1) different logistic regression models

- Predict according to the one that has the highest score

- Example:

- $$
  class : A, B, C \\
  setp 1 : Pivot class = C \\
  setp 2 : log\frac{P(A|x)}{P(C|x)} = \frac{other class}{pivot class} = \beta_A  · x ==> P(A|x ) = P(C|x) · exp(\beta_A  · x) \\
  setp 3 : log\frac{P(B|x)}{P(C|x)} =\beta_B  · x ==> P(B|x ) = P(C|x) · exp(\beta_B  · x) \\
  step 4 : P(A|x) + P(B|x) + P(C|x) = 1 \\
  step 5 : P(c|x) = 1 -  P(A|x) - P(B|x) \\
  step 6 : p(C|x) = \frac{1}{1+\sum_{k \in \{ A,B\}}}exp(\beta_k)·x \\
  step 7 : p(B|X) \times exp(\beta_B \cdot x) \\
  step 8 : p(A|X) \times exp(\beta_A \cdot x) \\
  $$

- choose what pivot is **irrevalent**



### Pros and Cons

- Pros:
  - **Vast improvement** than NB
  - Particularly suited to **frequency-based** features
- Cons:
  - slow
  - feature scaling issues
  - needs lot of data
  - Regularisation nuisance(hard) but important since overfitting can be a big problem
    - when too many feature -> overfitting

