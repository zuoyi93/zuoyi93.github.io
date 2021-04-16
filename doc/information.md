---
layout: page
permalink: /posts/information
title: Notes on MLE, Fisher's information and robust SE
tags: [code]
modified: 4-15-2021
comments: false
customjs: 
	- http://yihui.org/js/math-code.js
	- http://mathjax.rstudio.com/latest/MathJax.js?config=TeX-MML-AM_CHTML
---


Let `$X_1,...,X_n\sim$` i.i.d. Exp(`$\theta$`) (Exponential distribution with mean `$1/\theta$`).

The likelihood function for a sample of size `$n$` is  

`$$L(\theta)=\prod_{i=1}^n\theta\exp(-\theta x_i)=\theta^n\exp(-\theta\sum_{i=1}^nx_i) $$`

The log-likelihood function is   


