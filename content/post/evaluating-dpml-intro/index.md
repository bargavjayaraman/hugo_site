---
title: 'Why you should evaluate your private model'
subtitle: ''
summary: Always perform sanity check on your privacy parameters.
authors:
- admin
tags:
- Differential Privacy
- Machine Learning
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


Privacy concerns arise when training machine learning models over sensitive data such as personal information about individuals. These concerns become more serious when the trained models are publicly deployed as a service. While differential privacy can alleviate these privacy concerns, it is highly sensitive to the implementation choices such as the privacy budget and the type of differential privacy relaxation used. In our paper (to appear in USENIX Security’19), we experimentally evaluate the impact of these implementation choices on the privacy leakage. More concretely, we quantify how much information is leaked to the adversary.


The following fictional scenario illustrates the privacy concerns and the risks involved in publicly deploying models without properly analysing the differential privacy implementation choices.


# The QuickService Bank Scenario

When you go to a bank for a personal loan, the approval process often takes [from a day or two to a couple of weeks](https://studentloanhero.com/featured/how-long-does-it-take-to-get-approved-for-a-personal-loan/). However the QuickService Bank, living up to its name, launched an online service where you could enter your personal details and get an instant loan approval. The workhorse behind this quick service is their state-of-the-art machine learning model trained on the bank’s existing customer data.

{{< figure src="img/quickservicebank_scenario.png" >}}


## What went wrong?

The online loan approval service earned great popularity and brought in more business for QuickService Bank. But the bank’s joy didn’t last for long. Mandark, a notorious black-hat hacker, prowled on the online service and started leaking the identity of the bank’s customers. This type of attack is called [membership inference](https://ieeexplore.ieee.org/document/7958568) where the attacker identifies the presence or absence of a record in the training data.
{{< figure src="img/mandark_attack.png" >}}


## Differential privacy to the rescue!

Dismayed by the attack, QuickService Bank temporarily disabled the online service and hired Dexter who is a security expert. Dexter learns about <a href="https://www.microsoft.com/en-us/research/publication/differential-privacy/?from=http%3A%2F%2Fresearch.microsoft.com%2Fpubs%2F64346%2Fdwork.pdf">differential privacy</a> and decides to deploy it for privately training the bank’s loan approval model while still prioritizing the model’s accuracy. But due to the model’s complexity, the required privacy budget turned out to be 1000.
{{< figure src="img/dexter_dp.png" >}}

{{< figure src="img/dexter_rdp.png" >}}
Dexter, knowing that such a high budget might not be desirable for strong privacy, uses relaxed definitions (<a href="https://arxiv.org/abs/1603.01887">here</a>, <a href="https://arxiv.org/abs/1605.02065">here</a> and <a href="https://arxiv.org/abs/1702.07476">here</a>) to reduce the budget to 10 without compromising on the model accuracy. Happy with his privacy implementation, Dexter asked QuickService Bank to make the service online again.



## Again… what went wrong?

Though the differential privacy safeguard reduced Mandark’s attack success rate, he was still able to reveal the membership information of a few bank customers. Why did this happen? While the relaxed definitions allows the reduction in privacy budget, the amount of noise added in the model training remains the same. Thus, the effective privacy is the same as provided by differential privacy with high privacy budget.

In the next post, we will further explore this observation through empirical evaluation on real world data sets. 
