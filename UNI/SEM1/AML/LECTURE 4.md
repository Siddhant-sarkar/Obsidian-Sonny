---
tags:
  - AML
  - SEM1
  - UNI
date: 2025-02-10
modified: 04:06
---
# Convolutional Neural Networks (CNN)
# Wichtig
>[!imp] TO DO
>- What is a CNN?
>- What is the difference between convolution and cross-correlation?
>- What is a filter/kernel?
>- Do you know examples of convolutions?
>- How do the weight matrices look like in a CNN with 1D convolutions?
>- What is a Toeplitz matrix?
>- Is convolution a linear operation? If so, why?
>- What is the difference between full and valid convolution?
>- How do convolutions work in 1D/2D/dD?
>- What are padding/striding?
>- How does the weight matrix of a 2D convolution look like?
>- What is weight sharing in context of CNN?
>- What is pooling? Which forms of pooling do you know?
>- How would you combine convolutions and dropping for reasons of efficiency?
>- What are the changes in feedforward/backpropagation/update of the parameters when using a N in place of a FNN?
>- Where do we need to flip the kernels?
>- Why is the kernel for 2D rotated?
>- How does backpropagation work for pooling layers?
# Alles
![[Pasted image 20250210134824.png]]
## Motivation
- we see the negihbouring data values. due hence CNN.
- They have multidimensional arrays, and ordering matters, several channels, typically high dimensional.
	- audio Signals (1D)
	- Images (2D)
	- medical Data (3d)
	- voxels changing in time(4D)
- spacial distribution is neglected. relation between channels are neglected. Fully connected ANN would require large number of weight ,hence storage.
- weight that are mostly zero, take neighbouring relation, not depending on absolute location, but the relation among them.
- It takes some kind of filter. Here d is the signal.![[Pasted image 20250210135823.png]]Kind like the sliding window.
## Convolutions
### 1D
- Cross-correlation and convolution are different from each other. ![[Pasted image 20250210140054.png]] in convolution is the inverted from on cross correlation.![[Pasted image 20250210140215.png]] made by *Flipping the entries*.
- in probabilistic sense cross-correlation  is the differnce of proba. and convolution give the sum of probabilities.![[Pasted image 20250210140435.png]]
- Toeplitz matrix ![[Pasted image 20250210140730.png]] since we are just moving in some sort of window, we make the input by padding it by zero and such that convolution be defined for completely overlap and partial overlap.
- ![[Pasted image 20250210140933.png]] in the middle are the complete overlap and other sides are just partial overlap. This is how we want to replace the weight matrix in CNN.
### 2D
- its the same for 2D too. correlation is same, convolution is flipping otherwise.![[Pasted image 20250210141401.png]]
- For overlaps we also pad with zeroes around the initial matrix.![[Pasted image 20250210141623.png]]
- Striding is just : how fast move, and combination is the combination of padding and striding. 
### EXAMPLE
- FILTErs
	- identical transformation : just the pixel in between otherwise 0 for all the outer ones.![[Pasted image 20250210141859.png]]
	- Sobel : Detecting lines. Two forms vertical and horizontal. lines.![[Pasted image 20250210141944.png]]![[Pasted image 20250210142002.png]]
	- Laplace : for edge detection. How large the outside than inside. Outerpart and inner part has the same weight -20 = sum of all the outer.!!! ![[Pasted image 20250210142125.png]]
	- Blur : ![[Pasted image 20250210142222.png]]
		- Often Blur than laplace : ![[Pasted image 20250210142243.png]]
	- Channel avegage : RGB -> greyscale.![[Pasted image 20250210142341.png]]
- ![[Pasted image 20250210142636.png]] this is what the convoution looks like in 2D.
- This is why we use convolution such that to reduce the weights.![[Pasted image 20250210142820.png]]
## Pooling
- it is the further reduction of data. after applying the activation function we just go 2x2 or higher non overlapping matrix which just reduces the after convolution by factor of 4.
- types :
	- Max pooling: maximum over the pooling matrix. Storing the winning entries for back propagation.
	- min pooling : taking the minimum of pooling matrix.
	- Avergaring : taking the average of pooling matrix.
	- dropping. : mostly done with convolution with strides and there is no need to compute the quanties that are dropped afterwards. 
## Feedforward and backpropagation
- Simple Feed forward , Backpropagation is just transposed teoplitz matrix.![[Pasted image 20250210143635.png]]
- Backpropagation. ![[Pasted image 20250210143728.png]]
- Kernal updates : ![[Pasted image 20250210143947.png]]![[Pasted image 20250210144205.png]]![[Pasted image 20250210144312.png]]
### Pooling Feed Forward and BackPropagation.
![[Pasted image 20250210144441.png]] So its just similar to FNN.


