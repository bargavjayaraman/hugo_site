---
title: 'Evaluating differentially private machine learning in practice'
subtitle: ''
summary: What seems safe, might not be safe in practice.
authors:
- admin
tags:
- Machine Learning
- Differential Privacy

categories: []
date: "2019-07-08T00:00:00Z"
lastmod: "2019-07-14T00:00:00Z"
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 1
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects:
- evaluating-dpml
---


In the previous post, we discussed a motivational scenario about why we need to check for privacy vulnerability of differentially private machine learning models. In this post, we will quantify this privacy vulnerability in terms of leakage of membership information through experimental evaluation on [CIFAR-100](https://www.cs.toronto.edu/~kriz/cifar.html) data set. This work has been accepted at [USENIX Security'19](https://www.usenix.org/conference/usenixsecurity19) and the full manuscript can be found [here](https://www.cs.virginia.edu/~evans/pubs/usenix2019/evaluatingdp.pdf).


## Brief introduction of evaluation procedure
We train logistic regression and two-layer neural network models with differential privacy over 10,000 training instances, and separate 10,000 instances are used for testing.  Comparison of model utility and privacy leakage is made for various differential privacy approaches that differ in the composition of privacy budget. These are namely, na&#x00EF;ve composition (NC), advanced composition (AC), zero concentrated differential privacy (zCDP) and R&#x00E8;nyi differential privacy (RDP). RDP and zCDP have stricter composition property which allows them to add much less noise in comparison to NC for a given privacy budget. Thus, they achieve better model utility but at the cost of privacy leakage, which we show in our experimental results. We calculate the model utility as accuracy loss relative to a non-private baseline model. For privacy leakage, we evaluate the advantage of membership inference attacker, which is given as the difference between true positive rate (TPR) and false positive rate (FPR) of detecting whether a given instance is a part of the training set. We implement the membership inference attacks of [Shokri et al.](https://ieeexplore.ieee.org/document/7958568) and [Yeom et al](https://ieeexplore.ieee.org/document/8429311) for this purpose.

For brevity, we stick to the results of Yeom et al. membership inference attack on neural network s trained with NC and RDP in this post. Interested readers are referred to the [full paper](https://www.cs.virginia.edu/~evans/pubs/usenix2019/evaluatingdp.pdf) for a discussion on other experimental results.


## Experimental observations

- utility-privacy plot of NC and RDP

- how many members being revealed

- leakage is amplified across intersection of multiple runs


## What's more in the paper

- results on Purchase-100 data set

- logistic regression results

- membership inference attack of shokri et al.

- attribute inference attack of yeom et al.


## Conclusion

