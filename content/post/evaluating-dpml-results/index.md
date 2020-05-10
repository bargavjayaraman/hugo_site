---
title: 'Evaluating Differentially Private Machine Learning in Practice'
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

With the recent advancements in composition of differential private mechanisms, the research community has been able to achieve meaningful deep learning with privacy budgets in single digits<sup>[1](#myfootnote1)</sup>. The present notions of R&#x00E8;nyi differential privacy (RDP) and Gaussian differential privacy (GDP)<sup>[2](#myfootnote2)</sup> are considered state-of-the-art for providing tight composition. But the central question that remains to be answered is: how private are these methods in practice? In this blog post, we answer this question by empirically evaluating the privacy leakage of differential private neural networks via membership inference attacks. This work appeared in [USENIX Security'19](https://www.usenix.org/conference/usenixsecurity19) (full manuscript can be found [here](https://www.cs.virginia.edu/~evans/pubs/usenix2019/evaluatingdp.pdf)).

## Differential private training
We train two-layer neural network models using a training procedure similar to the popular [DPSGD](https://dl.acm.org/doi/pdf/10.1145/2976749.2978318) procedure. The training and test sets consist of seperate 10,000 instances randomly sampled from the [CIFAR-100](https://www.cs.toronto.edu/~kriz/cifar.html) data set. 

Figure below shows the accuracy loss of private models trained with na&#x00EF;ve composition (NC) and R&#x00E8;nyi differential privacy (RDP) with respect to a non-private model. As expected, model trained with RDP achieves much better utility when compared to the model trained with NC. To give a comparison, model trained with RDP achieves 53% accuracy loss at \\(\epsilon = 10\\), whereas the model trained with NC achieves the same utility at \\(\epsilon = 500\\). Due to the tighter composition, RDP mechanism adds much lesser noise when compared to NC mechanism for the same privacy budget. This is great, but what about the privacy leakage?
{{< figure src="img/acc_loss.jpg" >}}

## Privacy comes at a cost
For evaluating the privacy leakage, we implement the membership inference attack of [Yeom et al](https://ieeexplore.ieee.org/document/8429311) and use their membership advantage metric, which is given as the difference between true positive rate (TPR) and false positive rate (FPR) of detecting whether a given instance is a part of the training set. This metric lies between 0 and 1, where 0 signifies no privacy leakage. As the figure below depicts, there is a clear trade-off between privacy and utility. While RDP mechanism achieves higher utility, it also suffers from higher privacy leakage. The attack achieves around 0.40 membership advantage score against model trained with RDP at \\(\epsilon = 1000\\), with a positive predictive value (PPV) of 74%. While this is lesser than the privacy leakage of non-private model (highlighted in the figure below), it is still not an acceptable amount of privacy leakage in practice. On the other hand, the model has almost no utility at lower privacy budgets where the privacy leakage is low.
{{< figure src="img/priv_leak.jpg" >}}
A more interesting observation is that we only have tight theoretical worst case guarantees on membership advantage for \\(\epsilon < 1\\), at which point the models neither have any utility nor have any empirical privacy leakage. While the attacks only give a lower bound on the privacy leakage, the huge gap between the theoretical upper bound and the empirical lower bound suggests that there could be stronger attacks  in practice.

## Leakage is amplified across multiple runs
While we have shown above that the membership inference attack can be effective against a model trained with RDP at \\(\epsilon = 1000\\), things get worse when the attacker is allowed to run the attack multiple times. More specifically, the attacker gets more and more confident in predicting the membership of the individual records which are repeatedly identified across multiple runs. As the figure below shows, the attacker can identify almost a quarter of the training records with more than 82% PPV across five runs.
{{< figure src="img/multi_run.jpg" >}}

## Conclusion
The differential privacy research community has come a long way to realize practical mechanisms for deep learning. However, as shown in our work, we still require significant improvements to achieve meaningful utility for privacy budgets where we have strong theoretical guarantees. Concurrently, the huge gap between the empirical privacy leakage and the theoretical bounds opens the possibility for more powerful inference attacks in practice.

## What's more in the paper
While we only discussed selected results in this blog post, the [full paper](https://www.cs.virginia.edu/~evans/pubs/usenix2019/evaluatingdp.pdf) has more experimental results across different settings as listed below:

- Results on Purchase-100 data set, derived from [Kaggle](https://www.kaggle.com/c/acquire-valued-shoppers-challenge/data) website.

- Results for logistic regression model.

- Membership inference attack of [Shokri et al.](https://ieeexplore.ieee.org/document/7958568).

- Attribute inference attack of [Yeom et al](https://ieeexplore.ieee.org/document/8429311).

---
<a name="myfootnote1">1</a>: with some caveats such as model pre-training and adding less noise at each private training epoch with early stopping when the privacy budget exceeds the limit.

<a name="myfootnote2">2</a>: GDP wasn't published at the time our paper came, and hence we donot consider it in our evaluation.