---
layout: page
permalink: /posts/information
title: Notes on MLE, Fisher's information and robust SE
tags: [code]
modified: 4-15-2021
comments: false
includes: math.html
---







Let `$X_1,...,X_n\sim$` i.i.d. Exp(`$\theta$`) (Exponential distribution with mean `$1/\theta$`).

The likelihood function for a sample of size `$n$` is  

`$$L(\theta)=\prod_{i=1}^n\theta\exp(-\theta x_i)=\theta^n\exp(-\theta\sum_{i=1}^nx_i) $$`

The log-likelihood function is   

`$$\ell_n(\theta)=\log L(\theta) = n\log\theta-\theta\sum_{i=1}^n x_i $$`

The score function is  

`$$S_n=\frac{\partial l_n(\theta)}{\partial\theta}=\frac{n}{\theta}-\sum_{i=1}^n x_i $$`

The second derivative of the log-likelihood function is 

`$$\frac{\partial^2\ell(\theta)}{\partial\theta^2}=\frac{-n}{\theta^2} $$`

