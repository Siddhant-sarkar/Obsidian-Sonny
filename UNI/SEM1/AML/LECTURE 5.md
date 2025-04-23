---
tags:
  - AML
  - SEM1
  - UNI
date: 2025-02-10
modified: 15:06
---
# [Implementation of CNN, History, & DFT](https://webcast.tu-harburg.de/Mediasite/Play/54217356dd14414fb62c205c96d8abaa1d)

# Wichtig
>[!imp] TO DO !!!
>- Which CNN mark important steps in the development? Why?
 >- What is data augmentation? Why do we need this?
 >- Which types of data chunks do we have to combine in the training of a CNN when using mini batches and filter banks? 1D/2D/3D/4D/5D/...?
 >- What is a circulant matrix?
 >- What is the relation between convolution and multiplication by a (block) circulant?
 >- What are the eigenvalues and eigenvectors of a circulant?
 >- What is the DFT/IDFT?
 >- What is the relation between convolutions and the DFT/IDFT?
 >- Why do we obtain a block circulant with circulant blocks in the 2D convolution case?
 >- What are the eigenvalues and eigenvectors of such a matrix?
 >- How do DFT/IDFT change in 2D? dD?
# Alles
## 1D : Toeplitz to circulant 
![[Pasted image 20250210174903.png]]
![[Pasted image 20250210174926.png]]
Proof : 
![[Pasted image 20250210175231.png]]![[Pasted image 20250210175059.png]]
## How to make convolutions faster.
![[Pasted image 20250210175434.png]]![[Pasted image 20250210190131.png]]

