---
tags:
  - AML
  - UNI
  - SEM1
date: 2025-02-09
modified: 13:39
---
# Finding the Network Parameters.
# Wichtig
>[!important] to Do!!
>- What is the universal approximation theorem (UAT)?
>- How many neurons/layers do we need?
>- Is that true for any activation function?
>- Can you give a pictorial proof of the UAT for special dimensions and/or activation functions?
>- How do you approximate/interpolate/construct a function by an NN?
>- What is a cost function? How do you choose it?
>- What is the method of steepest descent/gradient descent (GD)? What are the mathematical preliminaries that you need for the method?
>- What is Newton’s method? 
>- What are the mathematical preliminaries that you need for the method?
>- How do you determine the step length in these methods?
>- What is the difference between the differential and the gradient?
>- Prove that the negative gradient is the direction of steepest descent.
>- Are there variants that take other directions of descent? How are these determined?
>- What is the relation of Newton’s method close to a minimum and GD?
>- What is SGD? Why do we use it?
>- What is a mini-batch?
>- What is backpropagation? How do we derive it in case of a FNN?
>- How does the multi-dimensional chain rule look like?
>- How did we change the chain rule to fit our needs?
>- What is the meaning of the notation ∂C/∂v for some vector v?
>- What is the meaning of the notation ∂C/∂A for some matrix A?
>- How do we compute the derivative of the cost function c with respect to W, x, and b, when we know the derivative of the cost function C with respect to the vector z = Wa + b?
>- How do we compute the derivatives of the cost function C with respect to the affine linear combinations zi in the ith layer? In which order?
>- How do we efficiently implement feedforward and backpropagation with minibatches in a FNN?
# Alles
## [[Universal Approximation Theorem]]
- They stated that with two hidden layer arbitrary continuous functions can be approximated if the activation function is monotone and sigmoidal.
- $\sigma : R \to [0,1]$ is sigmoidal if $\lim_{ x \to -\infty } \sigma(x) = 0, \lim_{ x \to \infty }(x) = 1$
- so its basically the having a bumps in activation function which just fills in the continuous polynomial function.
 ![[Pasted image 20250209143541.png]]
### PROOF
![[Pasted image 20250209144402.png]]
![[Pasted image 20250209144528.png]]
- so the proof is kinda, so we have a set of $C^{T}*\sigma(Wx+b)$ is the set of all the outputs which we will get.
- So we want to prove that $S = C[I_{n}]$, so we take the contradiction to true.
- We have HAHN-BANACH  there exists some $map L \neq 0, L(s) = L(S) = 0$
- and RIESZ representation $L[f] = \int f(x)d\upsilon(x)$ 
	- $L(s) = \int \sigma(w^{T}x+b) \, d\upsilon(x) = 0, \implies L =0$ so which contradicts our assumption we state that $S =C[I_{n}]$
	- There has to something which is discriminatory.
- two hidden layers with first layer having $n^{3}$ number of nuron and   second layer containing exponential number of neurons.

## ANN as function approximators
- Choose a cost or loss function which can be minimised.
$$
C(p) = \frac{1}{2N} \sum_{j=1}^{N} ||F(x_{j} - y_{j})||^{2}_{2}
$$
- important that C splits into differentiable parts.
$$
C(p) = \frac{1}{N}\sum_{j=1}^{N} (C_{j}(p)).
$$
## 1D-optimisation
### method of Gradient Descent / steepest descent.
- Derivative positive -> proceed in negative direction
- Derivative negative -> proceed in positive direction
- Derivative zero -> $f(x-f'(x)\alpha) < f(x)$ and we found the minima.
- $x_{k+1} = x_{k} - f'(x_{k})\alpha_{k}$ where $\alpha_{k}$ is step length, which specifies how big of a step are we going to take from the current step in the opposite of current gradient.
- Derivative vs Gradient descent
![[Pasted image 20250209205907.png]]
- The gradient is the transpose of derivative.
![[Pasted image 20250209212045.png]]
- Cauchy schwarz states the largest will be when they are opposite, which will help us to go down the steepest descent.
![[Pasted image 20250209212201.png]]
>[!imp] How the learning rate effect the steepest.

![[Pasted image 20250209212345.png]]
### Newtons method
- we take a twice differentiable matrix.
	- gradient = 0
	- Hessian is positive definie.
- ![[Pasted image 20250209212619.png]]
	-  we have a matrix and we have to solve something related to matrix and which needs lot more computation.
- ![[Pasted image 20250209212724.png]]
- Its is quadratically converting.
- It can jump wildly. Hence not advised.
## [[Stochastic Gradient Descent]]
- For batch Gradient Descent.
	- equation by which it just updates the previous values.![[Pasted image 20250209213001.png]]
- SGD we take the gradient of all since most of them point at the same direction where there is minimum, hence we go there.But as we more more close to the minimum the direction from each data point will wiggle a lot. Hence we make the learning rate smaller at we more closer to the end.![[Pasted image 20250209213305.png]]
#### MINI Batch SGD
- Mini Batches when all used up we say it gone through epocs.![[Pasted image 20250209213346.png]]
### Multidimensional Chain rule
- ![[Pasted image 20250209214737.png]]
> we dont do the chain rule as such. Since we want to use the Gradient not the derivative. We need to use the transpose chain rule which is $(AB)^{T} = B^{T}A^{T}$ so because of that 
### Backpropagation
- self explainatory![[Pasted image 20250209215111.png]]
- Its pretty intuitive that when we are doing the chain rule so we go from the last layer to the first layer till we reach the the component we want to do.
## Proof of BackPropagation.
- partial cost function w.r.t to am ![[Pasted image 20250209215744.png]]![[Pasted image 20250209215805.png]]![[Pasted image 20250209215943.png]]![[Pasted image 20250209220053.png]]![[Pasted image 20250209220151.png]]![[Pasted image 20250209220907.png]]![[Pasted image 20250209220926.png]]

