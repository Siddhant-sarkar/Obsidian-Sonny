---
tags:
  - AML
  - UNI
  - SEM
date: 2025-02-08
modified: 15:48
---
# Introduction and Basics.
# Wichtig
 >[!important] What we will study.
• What do artificial neurons have in common with real neurons?
• What is an SVM?
• What is an activation function?
• How are these used in context of SVM?
• How would you group the different activation functions? Why?
• Which ones are used where? (This extends to later lectures!)
• Why don’t we use the linear function as an activation function for all layers?
• What is an artificial neural network (ANN)?
• What are weights and biases?
• What are (input, hidden, output) layers?
• What are the dimensions of the weights and biases?
• Is a neural network a (continuous, differentiable, analytic) function?
• What is a feedforward neural network (FNN)?
• How are FNN evaluated?
• How many parameters does an FNN have?
• How would you implement a FNN? (Extends to later lectures.)
• How could you change a FNN into other neural networks (NN)?
• Why are NN successfully used nowadays?
• How would you speed up the computations in an NN?
• What is universal approximation (UA)?
• Are NN universal approximators?
# Alles
efficient implementation of neural networks.
## [[Support Vector Machines]]
- the entire maths is just like this ->  $matA * mat x - mat b$.
- weights are the  points perpendicular which helps to determine what  $W^{T}.x - b$ ![[Screenshot 2025-02-08 at 23.51.07.png]]
- $l(x) = w^{t}x + b = x^{T}w+b$ where W is weights and b is biases.
- Size of margin of the area defines by the line:
$$
\frac{<x_{1} - x_{2},w> }{||w||_{2}} = \frac{<x_{1},w>}{||w||_{2}}  - \frac{x_{2},w>}{||2||_{2}} 
$$
- So at the end of the day we just want to $min_{w,b} {∥w∥2 |y_{i}ℓ(x_{i}) ⩾1, i= 1,...,N}$
## [[Heavyside function]]
- $H(w^{T}x +b)$ and $H(x):={0 x<0, 1 x \geq 0}$
- there are some smooth function without the break in [0,1] classes.
	- $Logistic(x) = (1 + e^{-x})^{-1}$ and $logistic' = Logistic . (1 - Logisitic)$ 
	- Heavy-side : $Logisitic_{k}(x) = Logisitic(kx) =\frac{1}{1+e^{ -kx }}$ ![[Screenshot 2025-02-09 at 12.57.29.png]]
- Sign function $Sign(x)= (2M-1)(x)$
	- $2Logistic(2x) -1 =\frac{e^{x}- e^{-x}}{e^{x} + e^{-x}} = TanH(x)$
	- has range between [-1,1]
	- $TanH'= 1 - TanH^{2}$ the derivative
	![[Screenshot 2025-02-09 at 13.04.06.png]]
## [[RelU Function]]
- $\mathrm{Re}lu(x) = max(x,0)$
- Leaky RElu = $max(x,0) + min(0,\alpha x)$
- $ELU_{\alpha}(x) = \alpha(e^{x}-1) x \leq{0} || x , x \geq 0$
- $SoftPlus_{k}(x)=\frac{\ln(1+e^{kx})}{k}$![[Screenshot 2025-02-09 at 13.12.29.png]]
## [[Abs family]]
$Abs(x) = |x|$
- $SoftAbs_{k}(x) = x.Softsign_{k}$ where $SoftSign_{k}(x)= \frac{kx}{1+|kx|}$
![[Screenshot 2025-02-09 at 13.16.14.png]]
![[Screenshot 2025-02-09 at 13.16.31.png]]
### IMPORTANT Ranges and domains.
![[Screenshot 2025-02-09 at 13.17.07.png]]
![[Pasted image 20250209135215.png]]
# [[ANN : Artifical Neural Networks]]
- Column wise combination of SVM + component wise application of an activation function.
- Feed forward neural network, since we go in forward direction.
![[Screenshot 2025-02-09 at 13.20.31.png]]
>[!danger] 
>Red = input ,green = output ,all other layer = hidden layer ,coloured circles = neurons.
## [[Universal Approximation Theorem]]
![[Screenshot 2025-02-09 at 13.27.37.png]]
- *Every continuous function can be approximated with a polynomial. such that there exists $|f - p_{t}| < \epsilon$*
- *Every continuous function is combination of finite linear combination of univariate function (having only one output) combined.
>[!imp] but functions are unknown and functions known per layer are not known in advance.
