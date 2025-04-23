---
tags:
  - AML
  - SEM1
  - UNI
date: 2025-02-10
modified: 20:01
---
# FFT, im2col, & Winograd
# Wichtig
>[!danger] TO DO 
• What is a separable kernel?
• Can you describe the DFT/IDFT for dD?
• What is the FFT?
• How would you derive an FFT for n = n1· n2?
• How can you implement the FFT recursively? How many operations do you need?
• How do the indices in the radix2 DIT FFT change?
• What is the Cooley-Tuckey Factorization?
• What is the scrambled DFT space? Why is this useful for convolutions?
• How do you perform convolution using padding, FFT, and IFFT?
• What is the NCHW format?
• What is a filter bank?
• How does convolution in the NCHW format look like?
• What is im2col? Why do we use it? What is the disadvantage of im2col?
• How can we implement im2col in Python?
• How does Winograd’s minimal algorithm look like?
• Are there similarities with the FFT?
• Why do Winograd convolutions speed up CNN? When?
• How would you implement Winograd convolutions?

# Alles
## SEPERABLE KERNELS
- doing 2 1d dft to rows and columns seperately.
- like th soble kernels![[Pasted image 20250210200828.png]]
## DFT to FFT
- ![[Pasted image 20250210201446.png]]
### IM2COL
- we are just transposing image and feature map to columns such that It will get be converted to 1D convolution and taking the inverse operation we will be able to get back to our result in the form of 2D. ![[Pasted image 20250210204315.png]]
- It redueces to Matrix- matrix multiplication such that which is handeled blissfully by BLASS.
- And Feed forward and backpropagation is carried out as follows.![[Pasted image 20250210204600.png]]
- 