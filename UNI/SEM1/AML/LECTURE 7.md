---
tags:
  - AML
  - UNI
  - SEM1
date: 2025-02-10
modified: 20:34
---
## Understanding CNN & Adversarial Attacks
# Wichtig
>[!danger] TO DO !!!
>• How does the first layer of a trained CNN look like?
• What can be said about higher layers?
• What is attribution?
• What is a saliency map?
• How do CAM and Grad-CAM work? When?
• What is a deconvolutional network?
• What is guided backpropagation?
• Can you describe the differences between backpropagation, deconvolution, and guided backpropagation?
• What is feature visualization?
• Which things are detected by which layers of a CNN?
• What does Deep Dream do?
• What is an activation atlas?
• What is an adversarial example?
• How do adversarial attacks work?
• What is BFGS, L-BFGS?
• What is the curvature condition?
• What is the secant condition?
• What is the fast gradient sign method? How does it work?
• How do images look like that are classified with high confidence?
• What kinds of adversarial attacks do you know?
• Do adversarial attacks work in the real world?
• Do we need knowledge about weights, biases, and filters of the CNN for an adversarial attack?
• What is adversarial training?
• What is XAI and why should you use it?
• Are humans susceptible to adversarial attacks?
# Alles
## FILTERS
### GAbor filters
![[Pasted image 20250210204907.png]]
these are the actual way our eyes see the world.
- Class activation mapping : changing the last layer to Global Avergae Pooling layers.![[Pasted image 20250210205211.png]] and then we use softmax.
## ATTRIBUTIONs
- Doing deconvolutions : during backpropagation we apply relu.**often highly oscillating artifacts.
- Guided backpropagation : so we combine the deconv. and turn the gradient where its is 0 to 0 combined.![[Pasted image 20250210205809.png]] better stable resutlts with this one.
## Feature Visualization.
- visualizing the featuers instead of the differnt layers.![[Pasted image 20250210210142.png]]
## Combination and extensions.
- basic ideas : select image which give maximal activation.
- deep dream : start with image and optimze for maximal activation; loss computed as sum over layers of mean of layer.
- activation atlas : look at patches and compute features, combine w/ dimensionality reduction.
## Adversarial Attacks
### Optmization of attacks
![[Pasted image 20250210211029.png]]
![[Pasted image 20250210211707.png]]![[Pasted image 20250210211646.png]]
### Black-box Attack
- mostly one pixel attack.![[Pasted image 20250210212026.png]]
### Learning From attacks
- adversial example are generated based on some of the aformentioned approaches. These are then using training examples.
- Does guarentee against one pixel attack, but better attacks are not guarenteed.
- slight rotation or other stuff distortation.
### Attacks on humans
