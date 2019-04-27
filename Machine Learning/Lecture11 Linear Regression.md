## Lecture11 Linear Regression

### Hyper-parameter

- parameter set before traning
- e.g. : tree depth, learning rate, k value
- Given an evaluation metric $D$ (like Accuracy), a dataset $T$ , a feature representation $F(T )$, and a learner $L$  with hyperparameters $θ^h$
- Max $D(L,\theta^h, F(T))$
- Grid Search ==> $\hat\theta^h = argmin_{\theta^h \in \Theta}Error(L,\theta^h, F(T))$
- Iterative Grid-search for KNN
- Exhaustive Search



### Linear Regression

- **output class is continuous**

- Continuous attributes → continuous class
- $c = w_0 + \smash{\displaystyle\sum_{i=1}^kw_ia_i}$
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190427012522.png" height = "200px"/>
- Linear regression captures a relationship between **two** variables or attributes.
  - An outcome variable(label) - y
  - A predictor(feature) - x
- $y = f(x)$
- $y = \beta • x  = \beta_0 + \beta_1x_1+…+\beta_Dx_D$
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190427013519.png" height = "200px"/>



### Fitting the model

- We want best line : Operationally, the line that minimises the distance between
  all points and the line
- $RSS(\beta) = \smash{\displaystyle \sum_i(y_i - \hat y_i)^2}$
- $\hat\beta = argmin RSS(\beta;\{X,Y\} )$



### Gradient Descent Algorithm

- $\beta_k^{i+1} := \beta_k^i + 2\alpha\smash{\displaystyle\sum_{j=1}^Nx_{jk}(y_j-\hat y_j^i)}$
- Step1: **making** a prediction for each (training) instance
- Step2: **comparing** the prediction with the actual value
- Step3: **multiplying** by the corresponding attribute value
- Step4: **updating** the weights after all of the training instances have been processed

- Logic:
  - $\nabla Error(\theta)$ is a vector of partial derivative terms. It measures the slope (= gradient) of the function $Error(\theta)$: this is the direction
  - The **gradient points up-hill**; we **follow it down-hill**. Eachupdate reduces the error slightly.
  - $α$ is a parameter of the algorithm, representing the **learning rate** (how big a step you take in updating $θ_i$)
  - If $α$ is too **small**, the algorithm might be **slow**.
  - If it is too **large**, you might **miss the minimum.**
- <img src="https://raw.githubusercontent.com/Whihat/PicAssests/master/20190427015016.png" height = "200px"/>



### Evaluation metrics

- Root mean-squared error(RMSE)
- Root relative squared error(RRSE)
- Correlation coefficient (Pearson’s correlation)