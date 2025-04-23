---
tags:
  - AML
  - SEM1
  - UNI
date: 2025-02-09
modified: 23:59
---
# Variant of SGD and Regularization.
# Wichtig
>[!imp] To do... 
>- How do we initialise the weights and the biases in a FNN? (This extends to later lectures.)
>- What happens when we initialise everything by zero? By a constant?
>- Are the properties of random matrices random?
>- What is the circular law, what do Marčenko and Pastur say about singular values of random matrices?
>- How do Xavier Glorot and Kaiming He initialize the weights?
>- What is orthogonal initialization?
>- How would you initialize the weights?
>- Do you know variations of SGD? Which ones? How are these motivated?
>- Which SGD variant would you prefer? For what reason?
>- What do under- and overfitting mean?
>- What is the capacity of a neural network?
>- What groups of regularization techniques do you know?
>- What is the problem of vanishing/exploding gradients?
>- How does using ReLU help?
>- What is the problem of dying neurons?
>- Can you reactivate dead neurons?
>- How does gradient clipping work?
>- Can you describe L1 and L2 regularization? Which parts of the backpropagation change? How?
>- What is weight decay?
>- What is batch normalization?
>- What is Dropout? How would you implement it?
>- What is DropConnect? How would you implement it?
>- How do Dropout and DropConnect relate to each other?

# Alles
- Something to recap.![[Pasted image 20250210000107.png]]
---
## Zero/known/random weights
- ### Zeros
	- initialising with zeros is a bad ideas.After the first update weight matrix has all columns equal and and after the m-1 updates the all the entries in $W_{m-1}$ have all the entries equal![[Pasted image 20250210001455.png]] 
- ### Known Data
	- First layer is like what universally we know about the data. Last layers are like the what we closely want them to be.
	- Transfer Learning : Freezing the first few layers of a NN which is adapted to identifying the digits, such that only modification will be to rest of layers for identifying the alphabets.![[Pasted image 20250210002253.png]]
- ### Random values
	- Circular Law : Any random $N * N$ matrix having mean 0 and  variance $\sigma = \frac{1}{n}$ are uniformly distributed over a unit disc.
	- Smallest singular values $\left( 1\pm \frac{k}{n}  \right)\sqrt{ N }$ ![[Pasted image 20250210003319.png]]
## Xavier Golrot, Kaiming He,...
- Using a hyperbolic tangent function because its good.![[Pasted image 20250210003632.png]]
- Since Relu negative part is just vanished so we use some gain factor to amplify the only positive form.
- FOR orthonormal matrix : we have ![[Pasted image 20250210004009.png]] QR decomposition is just stable because people used some tricks to just make their life easier.
---
## Momentum and NAG
- SGD suffers from: 
	- Oscillating slow convergence in "bannana shaped valleys", get stuck in unwanted saddle points.
	- matching learning rate has to adapted in the course of computation.
- if Oscillating behaviour/getting stuck in saddle points -> momentum. So we store something like a velocity from the previous step.![[Pasted image 20250210004711.png]]![[Pasted image 20250210004744.png]]![[Pasted image 20250210004805.png]]
- *NAG : Nesterov Acclerated Gradient* ![[Pasted image 20250210005042.png]]
- Varient is composed of predictor and corrector step. Some kind of forward looking ball.![[Pasted image 20250210005339.png]]
## Adaptive Learning rates(Adagrad,RMSprop)
- ==ADAgrad(adaptive Gradient)== :  different learning rate for different components.
- additional vector , where we store component wise gradient, multiplying the all the gradients by itself, and then taking sqaure root of all component wise.![[Pasted image 20250210005941.png]]$\epsilon$ is there is just solve divide by 0.
- This is s demerit doing operations on W it may become so large that the update me become 0 and ADAgrad may become stuck.![[Pasted image 20250210010110.png]]
- ==RMSprop== : just uses some decay parameter $\gamma <1$ and vector W that stores the decaying average of componentwise squares.![[Pasted image 20250210010637.png]]
## Combination
- Combination of SGD with momentum with RMSprop.
- There are like two decay parameter one for gradient momentum and other for componentwise squares.![[Pasted image 20250210010844.png]]$\beta_{1} < \beta_{2} <1$ from the results.
- can use some correction step $k$ ![[Pasted image 20250210011120.png]]
## $L^{2} , L^{1} Regularization$
- we have to restrict the growth of weight matrices and biases, due to which we use regularization.
- too few neurons : underfitting , net learns the entire data set : overfitting.
![[Pasted image 20250210012031.png]] 
- weight matrix prolongs then exploding gradients, and otherwise vanishing gradients.
- Relu is reason for dying neurons.
- FOR L2 regularization![[Pasted image 20250210033248.png]]![[Pasted image 20250210033257.png]]
- FOR L1 regularization  : sum of absolute values of all the elements of all weight matrices is used.![[Pasted image 20250210033530.png]]
## Batch Normalization
- glues some layers such that our lives are easier.![[Pasted image 20250210040103.png]]
## Dropout and Dropconnect
- You train with all of neurons and drop the other neurons while training with some probability.
- Dropconnect connections to some neurons are dropped with some certain probability.
- 

