---
layout: post
title: "MICCAI/MedIA: Dynamic MRI using Low-rank and Total Variation"
description: "Source codes of FTVNNR"
comments: true
---

#### Abstract
In this paper, we propose an efficient algorithm for dynamic magnetic resonance (MR) image reconstruction. With the total variation (TV) and the nuclear norm (NN) regularization, the TVNNR model can utilize both spatial and temporal redundancy in dynamic MR images. We propose an efficient algorithm by solving a primal-dual form of the original problem. We theoretically prove that the proposed algorithm achieves a convergence rate of O(1/N) for N iterations. In comparison with state-of-the-art methods, extensive experiments on single-coil and multi-coil dynamic MR data demonstrate the superior performance of the proposed method in terms of both reconstruction accuracy and time complexity.

#### Highlights

<br />
<img align="middle" width="500" src="{{ site.url }}/images/BCS_figure-eps-converted-to.png" alt="...">
<br />

#### Codes

[MATLAB Code](https://github.com/utayao/FTVNNR_Dynamic_MRI)

#### References
- Jiawen Yao, Zheng Xu, Xiaolei Huang, Junzhou Huang
<br/>
”An Efficient Algorithm for Dynamic MRI Using Low-Rank and Total Variation Regularizations”
<br/>*Medical image analysis*, Vol. 44, 14-27, 2018
- Jiawen Yao, Zheng Xu, Xiaolei Huang, Junzhou Huang
<br/>”Accelerated Dynamic MRI Reconstruction with Total Variation and Nuclear Norm Regularization”
<br/>*MICCAI 2015*