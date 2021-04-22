---
layout: post
permalink: /posts/pdas
title: Key ideas on primal dual active set (PDAS)
tags: [blog]
modified: 4-21-2021
comments: false
---
<div style="line-height: 2"> 
The key ideas of primal dual active set (PDAS) algorithm for solving the best subset selection problem are summarized here. The original paper can be found <span style="color:blue;"> here </span>(https://www.jstatsoft.org/article/view/v094i04). They also have a very nice R package on <span style="color:blue;"> CRAN </span>(https://cran.r-project.org/web/packages/BeSS/index.html). 
<br>
</div>

Let `$\boldsymbol X\in\mathbb R^{n\times p}$` denote the design matrix, `$\boldsymbol y\in\mathbb R^n$` denote the outcome vector, and `$\boldsymbol\beta\in\mathbb R^p$` is the coefficient vector. The best subset selection problem with the subset size `$k$` is given by the following optimization problem:  

`$$ 
\underset{\boldsymbol\beta\in\mathbb R^p}{\min} l(\boldsymbol\beta)\: \text{ s.t. } \left\Vert \boldsymbol\beta \right\Vert_0 = k 
$$`

where `$l(\boldsymbol\beta)$` is a convex loss function of `$\boldsymbol\beta$` and `$\left\Vert \boldsymbol\beta \right\Vert_0=\sum_{j=1}^p\left\vert\beta_j\right\vert_0=\sum_{j=1}^p 1_{\beta_j\neq 0}$` counts the number of nonzeros in `$\boldsymbol\beta$`. The best subset selection problem admits non-unique local optimal solutions, so coordinate-wise minimizers `$\boldsymbol\beta^\diamond$` would be used in this case. The vectors of gradient and Hessian diagonal are  

`$$
\boldsymbol g^\diamond = \nabla l(\boldsymbol \beta^\diamond),\: \boldsymbol h^\diamond=\text{diag}(\nabla^2 l(\boldsymbol\beta^\diamond))
$$`

respectively. For each coordinate `$j=1,...,p$`, the loss can be rewritten as `$l_j(t)=l(\beta^\diamond_1,...,\beta^\diamond_{j-1}, t, \beta^\diamond_{j+1},...,\beta^\diamond_p)$` while fixing the other coordinates. `$l_j(t)$` can be approximated by a second-order Taylor expansion (local quadratic approximation `$l_j(t)^Q$`) around `$\beta_j^\diamond$`, which is  

`$$
\begin{aligned}
l_j(t)\approx l_q(t)^Q&=l_j(\beta_j^\diamond)+g_j^\diamond(t-\beta_j^\diamond)+\frac{1}{2}h_j^\diamond(t-\beta_j^\diamond)^2 \\
&= \frac{1}{2}h_j^\diamond(t-\beta_j^\diamond+g_j^\diamond/h_j^\diamond)^2 + l_j(\beta_j^\diamond) -\frac{1}{2}(g_j^\diamond)^2/h_j^\diamond \\
&= \frac{1}{2}h_j^\diamond(t-(\beta_j^\diamond+\gamma_j^\diamond)^2 + l_j(\beta_j^\diamond) -\frac{1}{2}(g_j^\diamond)^2/h_j^\diamond
\end{aligned} 
$$`

The equation above gives rise to the scaled gradient `$\gamma_j^\diamond$`, which has the form 

`$$
\gamma_j^\diamond = -g_j^\diamond/h_j^\diamond
$$`

Note that `$l^Q_j(t)$` is minimized at `$t^*=\beta_j^\diamond+\gamma_j^\diamond$` for `$j=1,...,p$`. When `$t$` is switched from `$t^*$` to 0, the change/sacrifice of `$l^Q_j(t)$`, denoted as `$\Delta_j^\diamond$`, is given by  

`$$
\Delta_j^\diamond = \frac{1}{2}h_j^\diamond(\beta_j^\diamond+\gamma_j^\diamond)^2, \: j=1,...,p
$$`

Best subset selection requires that `$p-k$` components of the coefficient vector are zero. To determine which `$p-k$`components, we can rank all the sacrifices `$\Delta_j^\diamond$` and enforce coefficients to zero if they contribute the least total sacrifice to the overall loss. Let `$\Delta_{[1]}^\diamond\geq \cdot\cdot\cdot\geq\Delta_{[p]}^\diamond$` denote the decreasing rearrangement of `$\Delta_j^\diamond$` for `$j=1,...,p$`. Best subset selection then truncates the ordered sacrifice vector at position `$k$`. In other words, the coordinate-wise minimizers are  

`$$
\beta_j^\diamond = \begin{cases}
\beta_j^\diamond+\gamma^\diamond_j,\text{ if }\Delta_j^\diamond\geq \Delta_{[k]}^\diamond\\
0,\text{ otherwise}
\end{cases}
$$`

In the equation above, `$\boldsymbol\beta^\diamond=(\beta_1^\diamond,...,\beta_p^\diamond)$` are primal variables, `$\boldsymbol\gamma^\diamond=(\gamma_1^\diamond,...,\gamma_p^\diamond)$` are dual variables, and `$\boldsymbol\Delta^\diamond=(\Delta_1^\diamond,...,\Delta_p^\diamond)$` are reference sacrifices. 


