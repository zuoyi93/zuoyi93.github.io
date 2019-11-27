---
layout: post
title: Winner solution for Data Science Bowl 2017 Challenge
description: "Breathe in the Future."
comments: true
---
I update it on Oct
This Challenge has past almost one month and finally [the golden](https://github.com/lfz/DSB2017) and [silver team](https://www.kaggle.com/c/data-science-bowl-2017/discussion/32544) released their solutions four days ago. Very grateful for their efforts and I will try to reproduce their results and understand their work in this post. 

<br /> I have conducted many work on histopathological images for lung cancer patients' survival prediction. Those are people who have been confirmed to be cancerous. As the same topic, this challenge is very attractive to me and I am very eager to learn things from other very smart people.

####  Background

Lung cancer is one of the most common types of cancer, with nearly 225,000 new cases of the disease expected in the U.S. in 2016. Early detection of lung cancer is very critical and Low-dose computed tomography (CT) is a potential breakthrough technology for early detection, with the ability to reduce deaths by 20%. Often, suspicious lesions identified in screening are initially assessed as high risk of cancer, but after additional follow-up tests, they turn out to be non-cancerous (false positives from the initial screening).

<br />
*Can machine learning reduce the number of radiology exams flagged for potentially unnecessary follow up and avoid patient anxiety ?*

<br />

Presented by Booz Allen and Kaggle, the competition will convene the data science and medical communities to develop cancer detection algorithms, and help end the disease as we know it.

#### Winner

So if you're into computer vision, you are likely dealing with some [deep-learning flavoured techniques]({{ site.url }}/deep-learning-takes-over-again/).

And the plot using XKCD style, as described in this [blog post]({{ site.url }}/xkcd-deep-learning/):
<br />
<br />
<img align="middle" width="500" src="{{ site.url }}/images/xkcd_deep2.png" alt="...">
<br />
<br />

[CPLEX](http://www.ibm.com/developerworks/downloads/ws/ilogcplex/) is a pretty awesome optimization toolbox from IBM, and it is free for academic use. It can be called from C++ (apart from Matlab, Python, etc.), but it's not the easiest library to compile...
You will encounter some problems for instance if your code has some C++11 functionalities from the C++ standard library.

<br />
Long story short, CPLEX requires the flag `-stdlib=libstdc++`, which *downgrades* the version of the standard library to a version where the C++11 functionalities where not available by default.
This way, your part of the code with C++11 won't compile.

<br />
The good part is that you can still use the C++11 code by including the *Technical Report 1* part of the library, that is, by adding `tr1/` to the files that the compiler does not found and changing `std::` by `std::tr1::` in the functions that are not found.    

