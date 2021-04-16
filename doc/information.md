---
layout: page
permalink: /code/information
title: Notes on MLE, Fisher's information and robust SE
tags: [code]
modified: 4-15-2021
comments: false
---

<script src="//yihui.org/js/math-code.js"></script>
<!-- Just one possible MathJax CDN below. You may use others. -->
<script async
  src="//mathjax.rstudio.com/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

Let `$X_1,...,X_n\sim$` i.i.d. Exp(`$\theta$`) (Exponential distribution with mean `$1/\theta$`).

The likelihood function for a sample of size `$n$` is  

$$L(\theta)=\prod_{i=1}^n\theta\exp(-\theta x_i)=\theta^n\exp(-\theta\sum_{i=1}^nx_i) $$
The log-likelihood function is   

$$\ell_n(\theta)=\log L(\theta) = n\log\theta-\theta\sum_{i=1}^n x_i $$
The score function is  

$$S_n=\frac{\partial l_n(\theta)}{\partial\theta}=\frac{n}{\theta}-\sum_{i=1}^n x_i $$

The second derivative of the log-likelihood function is  

$$\frac{\partial^2\ell(\theta)}{\partial\theta^2}=\frac{-n}{\theta^2} $$

The MLE $\hat\theta$ can derived from letting the score function equal to 0:  

$$\hat\theta=\frac{n}{\sum_{i=1}^n x_i}=\frac{1}{\bar x_n} $$
The expected Fisher's information $\mathcal I(\theta)$ under the true model is  

$$\mathcal I_n(\theta)=Var(S_n)=\mathbb E(S_n^2)=-\left (\frac{\partial^2\ell(\theta)}{\partial\theta^2}\right)=\frac{n}{\theta^2} $$
An estimate of the expected Fisher's information is  

$$\widehat{\mathcal I_n(\theta)}=\frac{n}{\hat\theta^2}=n\bar x^2_n $$
The limiting distribution of $\sqrt n(\hat\theta-\theta)$ is  

$$
\begin{aligned}
\sqrt n(\hat\theta-\theta)&\stackrel{d}{\rightarrow}N(0,\frac{1}{\mathcal I(\theta)}) \\
&\stackrel{d}{\rightarrow}N(0,\theta^2)
\end{aligned}
$$

The limiting distribution of $\sqrt n(\hat\theta-\theta)$ $\color{red}{\text{IS NOT}}$


$$
\color{red}{
\begin{aligned}
\sqrt n(\hat\theta-\theta)&\stackrel{d}{\rightarrow}N(0,\frac{1}{\widehat {\mathcal I(\theta)} }) \\
&\stackrel{d}{\rightarrow}N(0,\hat\theta^2) \\
&\stackrel{d}{\rightarrow}N(0,\frac{1}{\bar x_n^2})
\end{aligned}
}
$$
Because there is no sample average in the limit; it turns into the population average.  
 
An asymptotically valid 95\% confidence interval for $\hat\theta$ is  

$$\hat\theta\pm 1.96\sqrt{\frac{\hat\theta^2}{n}} $$

When $\hat\theta$ is replaced with MLE, we can write the confidence interval as  

$$\frac{1}{\bar x_n}\pm \sqrt{\frac{1}{n\bar x_n^2}} $$

When a robust estimate is of interest, we can write down $a$ as  

$$a=-\mathbb E\left(\frac{\partial^2\ell(x_i;\theta)}{\partial\theta^2}\right)=\frac{1}{\theta^2} $$

An estiamte for $a$ would be  

$$\hat a =-\frac{1}{n}\sum_{i=1}^n \frac{\partial^2\ell(x_i;\hat\theta)}{\partial\theta^2} =\frac{1}{1/\bar x_n^2}=\bar x_n^2  $$
Meanwhile, $b$ is 

$$b=\mathbb E(S_i^2)=\mathbb E(\frac{1}{\theta}-\bar x_n)^2=\frac{1}{\theta^2}+\mathbb E(x_i^2)-\frac{2\mathbb E(x_i)}{\theta}=\frac{1}{\theta^2}+Var(x_i)+(\mathbb E(x_i))^2-\frac{2}{\theta^2}=\frac{1}{\theta^2} $$

An estiamte for $b$ would be  

$$\hat b =  \frac{1}{n}\sum_{i=1}^n \left(\frac{\partial\ell(x_i;\hat\theta)}{\partial\theta}\right)^2= \frac{1}{n}\sum_{i=1}^n \left(\frac{1}{\hat\theta}-x_i\right)^2=\frac{1}{n}\sum_{i=1}^n (x_i-\bar x_n)^2 $$

Therefore,  

$$\frac{\hat b}{\hat a^2}=\frac{\sum_{i=1}^n(x_i-\bar x_n)^2}{n\bar x _n^4} $$
