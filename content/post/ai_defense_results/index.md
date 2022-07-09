---
title: 'Defense Against Attribute Inference'
subtitle: ''
summary: Results for the ongoing work on attribute inference defense.
authors:
- admin
tags:
- Machine Learning
- Differential Privacy

categories: []
date: "2022-06-27T00:00:00Z"
lastmod: "2022-07-05T00:00:00Z"
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

## [Jun 27, 2022] Vanilla Model Training

----

### Predicting *Hispanic* ethnicity on Texas-100X (I)

> **Threat Setting:** <br>
> Training distirbution is general data set distribution except the most populous hospitals.

> *<u>Adversarial Knowledge</u>:*

> - *High:* Adversary knows all but one record from training set.
> - *Medium:* Adversary knows the training distribution (i.e. can sample records with no intersection with training set).
> - *Low:* Adversary knows a skewed distribution (that has records from hospitals with highest number of patients).

<center><img src="img/texas-100x.jpg" width="100%"></center>
<center>**Figure 1:** Patient records distribution in Texas-100X, sorted with respect to hospital population.</center>

#### Model uses *race* as a training feature

As reported in the paper draft, the model trained on Texas-100X data set uses the race attribute as a feature which could have a positive correlation with the ethnicity attribute. Regardless of this, it is still useful to compare the attribute inference attacks with the imputation (IP) attack in this setting.

<details>
    <summary>**Hypothesis:** Passing WB$\cdot$IP as a feature to WB$\diamondsuit$IP's decision tree should improve the attack.</summary>
    **Remark:** The result is a mixed bag. WB$\square$IP attack does better than WB$\diamondsuit$IP attack in many (but not all) cases. Still for most cases, WB$\square$IP doesn't do better than WB$\cdot$IP.
</details>

<details>
    <summary>**Hypothesis:** There should be no gap between attribute inference and imputation with knowledge of train set.</summary>
    **Remark:** There is a considerable gap, even though this gap is reduced when imputation is trained with class label.
</details>


> WB$\cdot$IP multiplies the outputs of WB and IP <br>
> WB$\diamondsuit$IP uses a decision tree model to combine WB and IP <br>
> WB$\square$IP uses a decision tree model to combine WB, IP and WB$\cdot$IP <br>
> IP$^\dagger$ is the imputation with access to class label

> *<u>Candidate Sets</u>:*

> - *Train:* Subset of 10,000 candidate records drawn from the training set.
> - *Test:* Subset of 10,000 candidate records randomly sampled from the training distribution.
> - *OOD:* Subset of 10,000 candidate records randomly sampled from a distribution different from the training distribution.

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | High (Train) | High (Test) | Med (Train) | Med (Test) | Low (Train) | Low (Test) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Random | 29 $\pm$ 0 | 28 $\pm$ 0 | 29 $\pm$ 0 | 28 $\pm$ 0 | 29 $\pm$ 0 | 28 $\pm$ 0 |
| IP | 81 $\pm$ 2 | 79 $\pm$ 2 | 79 $\pm$ 4 | 75 $\pm$ 2 | 76 $\pm$ 3 | 80 $\pm$ 4 |
| IP$^\dagger$ | 83 $\pm$ 2 | 82 $\pm$ 2 | 82 $\pm$ 2 | 80 $\pm$ 5 | 80 $\pm$ 4 | 79 $\pm$ 4 |
| WB | 88 $\pm$ 3 | 86 $\pm$ 3 | 88 $\pm$ 3 | 87 $\pm$ 1 | 89 $\pm$ 3 | 90 $\pm$ 3 |
| WB$\cdot$IP | 86 $\pm$ 4 | 86 $\pm$ 3 | 88 $\pm$ 4 | 87 $\pm$ 3 | 86 $\pm$ 2 | 89 $\pm$ 3 |
| WB$\diamondsuit$IP | 86 $\pm$ 2 | 85 $\pm$ 4 | 86 $\pm$ 2 | 82 $\pm$ 5 | 74 $\pm$ 6 | 75 $\pm$ 7 |
| WB$\square$IP | 87 $\pm$ 3 | 84 $\pm$ 4 | 87 $\pm$ 3 | 85 $\pm$ 4 | 79 $\pm$ 8 | 78 $\pm$ 8 |
| WB$\cdot$IP$^\dagger$ | 86 $\pm$ 2 | 85 $\pm$ 2 | 89 $\pm$ 3 | 87 $\pm$ 3 | 88 $\pm$ 3 | 89 $\pm$ 3 |
| WB$\diamondsuit$IP$^\dagger$ | 86 $\pm$ 6 | 80 $\pm$ 4 | 86 $\pm$ 3 | 84 $\pm$ 5 | 79 $\pm$ 9 | 74 $\pm$ 8 |
| WB$\square$IP$^\dagger$ | 88 $\pm$ 3 | 85 $\pm$ 3 | 88 $\pm$ 2 | 84 $\pm$ 5 | 83 $\pm$ 9 | 77 $\pm$ 9 |
<center>**Table 1:** PPV (%) for predicting top-100 records on Texas-100X. Model is trained on general distribution.</center>


#### Model doesn't have access to *race*

Here we study the impact of removing race from the model training. Since race and ethnicity have implicit correlation, it would be more realistic to assume the adversary trying to infer ethnicity would not know the race of the query record.

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | High (Train) | High (Test) | Med (Train) | Med (Test) | Low (Train) | Low (Test) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Random | 29 $\pm$ 0 | 28 $\pm$ 0 | 29 $\pm$ 0 | 28 $\pm$ 0 | 29 $\pm$ 0 | 28 $\pm$ 0 |
| IP | 44 $\pm$ 5 | 40 $\pm$ 4 | 47 $\pm$ 8 | 47 $\pm$ 3 | 36 $\pm$ 4 | 39 $\pm$ 4 |
| IP$^\dagger$ | 45 $\pm$ 2 | 41 $\pm$ 3 | 44 $\pm$ 4 | 43 $\pm$ 4 | 38 $\pm$ 5 | 43 $\pm$ 5 |
| WB | 55 $\pm$ 3 | 52 $\pm$ 4 | 54 $\pm$ 3 | 53 $\pm$ 4 | 55 $\pm$ 4 | 54 $\pm$ 5 |
| WB$\cdot$IP | 60 $\pm$ 3 | 57 $\pm$ 5 | 63 $\pm$ 6 | 59 $\pm$ 2 | 52 $\pm$ 6 | 51 $\pm$ 6 |
| WB$\diamondsuit$IP | 61 $\pm$ 3 | 61 $\pm$ 6 | 61 $\pm$ 3 | 57 $\pm$ 5 | 47 $\pm$ 6 | 49 $\pm$ 4 |
| WB$\square$IP | 61 $\pm$ 6 | 57 $\pm$ 5 | 61 $\pm$ 4 | 56 $\pm$ 7 | 48 $\pm$ 7 | 49 $\pm$ 5 |
| WB$\cdot$IP$^\dagger$ | 61 $\pm$ 3 | 57 $\pm$ 4 | 61 $\pm$ 3 | 58 $\pm$ 4 | 51 $\pm$ 5 | 50 $\pm$ 3 |
| WB$\diamondsuit$IP$^\dagger$ | 58 $\pm$ 4 | 55 $\pm$ 6 | 56 $\pm$ 2 | 55 $\pm$ 7 | 48 $\pm$ 8 | 46 $\pm$ 8 |
| WB$\square$IP$^\dagger$ | 57 $\pm$ 3 | 55 $\pm$ 2 | 57 $\pm$ 3 | 58 $\pm$ 4 | 48 $\pm$ 6 | 45 $\pm$ 7 |
<center>**Table 2:** PPV (%) for predicting top-100 records on Texas-100X. Model is trained on general distribution.</center>

**Remark:** From the results in Table 2, we can see the impact of removing race attribute on ethnicity inference. The imputation PPV drops from ~80% to ~40%.


#### Results on out-of-distribution candidate set
    
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;High <br>(with Race) | &nbsp;&nbsp;&nbsp;&nbsp;Med <br>(with Race) | &nbsp;&nbsp;&nbsp;&nbsp;Low <br>(with Race) | &nbsp;&nbsp;&nbsp;&nbsp;High <br>(w/o Race) | &nbsp;&nbsp;&nbsp;&nbsp;Med <br>(w/o Race) | &nbsp;&nbsp;&nbsp;&nbsp;Low <br>(w/o Race) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Random | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 |
| IP | 70 $\pm$ 3 | 71 $\pm$ 5 | 81 $\pm$ 2 | 37 $\pm$ 10 | 32 $\pm$ 3 | 52 $\pm$ 4 |
| IP$^\dagger$ | 73 $\pm$ 3 | 73 $\pm$ 4 | 78 $\pm$ 4 | 37 $\pm$ 5 | 30 $\pm$ 2 | 61 $\pm$ 4 |
| WB | 84 $\pm$ 6 | 86 $\pm$ 5 | 91 $\pm$ 4 | 60 $\pm$ 7 | 62 $\pm$ 7 | 65 $\pm$ 3 |
| WB$\cdot$IP | 78 $\pm$ 5 | 85 $\pm$ 4 | 91 $\pm$ 3 | 55 $\pm$ 9 | 61 $\pm$ 7 | 85 $\pm$ 2 | 
| WB$\diamondsuit$IP | 86 $\pm$ 3 | 86 $\pm$ 3 | 91 $\pm$ 2 | 63 $\pm$ 4 | 54 $\pm$ 3 | 82 $\pm$ 4 |
| WB$\square$IP | 86 $\pm$ 3 | 87 $\pm$ 4 | 93 $\pm$ 1 | 56 $\pm$ 5 | 55 $\pm$ 3 | 85 $\pm$ 2 |
| WB$\cdot$IP$^\dagger$ | 77 $\pm$ 4 | 84 $\pm$ 4 | 88 $\pm$ 3 | 66 $\pm$ 5 | 61 $\pm$ 4 | 82 $\pm$ 5 |
| WB$\diamondsuit$IP$^\dagger$ | 83 $\pm$ 6 | 84 $\pm$ 4 | 90 $\pm$ 3 | 56 $\pm$ 5 | 60 $\pm$ 9 | 83 $\pm$ 2 |
| WB$\square$IP$^\dagger$ | 87 $\pm$ 1 | 86 $\pm$ 3 | 90 $\pm$ 2 | 54 $\pm$ 5 | 60 $\pm$ 7 | 82 $\pm$ 1 |
<center>**Table 3:** PPV (%) for predicting top-100 records from out-of-distributon candidate set (Texas-100X). Model is trained on general distribution.</center>



### Predicting *Hispanic* ethnicity on Texas-100X (II)

Here we consider the scenario where the training data comes from skewed distribution, while an adversary (in low adversarial knowledge setting) might have access to the general pupulation distribution.

> **Threat Setting:** <br>
> Training distirbution is a skewed distribution limited to records from most populous hospitals.

> *<u>Adversarial Knowledge</u>:*

> - *High:* Adversary knows all but one record from training set.
> - *Medium:* Adversary knows the training distribution (i.e. can sample records with no intersection with training set).
> - *Low:* Adversary knows the general data set distribution except the most populous hospitals.

#### Model uses *race* as a training feature

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | High (Train) | High (Test) | Med (Train) | Med (Test) | Low (Train) | Low (Test) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Random | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 |
| IP | 86 $\pm$ 3 | 83 $\pm$ 3 | 88 $\pm$ 3 | 87 $\pm$ 3 | 72 $\pm$ 4 | 65 $\pm$ 4 |
| IP$^\dagger$ | 84 $\pm$ 2 | 85 $\pm$ 1 | 87 $\pm$ 2 | 82 $\pm$ 2 | 73 $\pm$ 4 | 67 $\pm$ 6 |
| WB | 92 $\pm$ 2 | 90 $\pm$ 4 | 93 $\pm$ 2 | 90 $\pm$ 4 | 84 $\pm$ 6 | 81 $\pm$ 6 |
| WB$\cdot$IP | 95 $\pm$ 3 | 89 $\pm$ 3 | 96 $\pm$ 1 | 93 $\pm$ 3 | 79 $\pm$ 3 | 78 $\pm$ 4 |
| WB$\diamondsuit$IP | 90 $\pm$ 3 | 90 $\pm$ 3 | 92 $\pm$ 3 | 92 $\pm$ 2 | 81 $\pm$ 5 | 79 $\pm$ 7 |
| WB$\square$IP | 90 $\pm$ 1 | 89 $\pm$ 3 | 92 $\pm$ 2 | 91 $\pm$ 2 | 80 $\pm$ 4 | 77 $\pm$ 7 |
| WB$\cdot$IP$^\dagger$ | 95 $\pm$ 3 | 89 $\pm$ 4 | 95 $\pm$ 1 | 90 $\pm$ 4 | 81 $\pm$ 5 | 79 $\pm$ 4 |
| WB$\diamondsuit$IP$^\dagger$ | 90 $\pm$ 3 | 90 $\pm$ 3 | 92 $\pm$ 4 | 91 $\pm$ 1 | 82 $\pm$ 5 | 80 $\pm$ 5 |
| WB$\square$IP$^\dagger$ | 92 $\pm$ 4 | 89 $\pm$ 3 | 91 $\pm$ 3 | 90 $\pm$ 1 | 80 $\pm$ 6 | 78 $\pm$ 6 |
<center>**Table 4:** PPV (%) for predicting top-100 records on Texas-100X. Model is trained on *skewed* distribution.</center>

**Remark:** As shown in Table 3, IP$^\dagger$ performs slightly worse than IP. Hence the class label seems to have a negative correlation with the Hispanic ethnicity in this setting where training records come from a skewed distribution.

#### Model doesn't have access to *race*

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | High (Train) | High (Test) | Med (Train) | Med (Test) | Low (Train) | Low (Test) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Random | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 | 24 $\pm$ 0 ||
| IP | 65 $\pm$ 4 | 61 $\pm$ 4 | 70 $\pm$ 6 | 72 $\pm$ 5 | 32 $\pm$ 4 | 32 $\pm$ 6 |
| IP$^\dagger$ | 64 $\pm$ 5 | 62 $\pm$ 6 | 70 $\pm$ 3 | 68 $\pm$ 4 | 37 $\pm$ 2 | 36 $\pm$ 4 |
| WB | 57 $\pm$ 6 | 57 $\pm$ 8 | 56 $\pm$ 4 | 56 $\pm$ 7 | 57 $\pm$ 4 | 56 $\pm$ 6 |
| WB$\cdot$IP | 89 $\pm$ 5 | 86 $\pm$ 5 | 90 $\pm$ 2 | 88 $\pm$ 4 | 58 $\pm$ 3 | 58 $\pm$ 5 |
| WB$\diamondsuit$IP | 84 $\pm$ 5 | 85 $\pm$ 4 | 82 $\pm$ 2 | 85 $\pm$ 3 | 58 $\pm$ 6 | 58 $\pm$ 5 |
| WB$\square$IP | 84 $\pm$ 7 | 84 $\pm$ 5 | 85 $\pm$ 2 | 85 $\pm$ 4 | 60 $\pm$ 6 | 59 $\pm$ 5 |
| WB$\cdot$IP$^\dagger$ | 83 $\pm$ 3 | 85 $\pm$ 4 | 88 $\pm$ 3 | 87 $\pm$ 4 | 67 $\pm$ 4 | 65 $\pm$ 5 |
| WB$\diamondsuit$IP$^\dagger$ | 81 $\pm$ 5 | 84 $\pm$ 4 | 82 $\pm$ 4 | 85 $\pm$ 2 | 60 $\pm$ 4 | 60 $\pm$ 4 |
| WB$\square$IP$^\dagger$ | 84 $\pm$ 4 | 86 $\pm$ 3 | 84 $\pm$ 4 | 86 $\pm$ 2 | 59 $\pm$ 6 | 58 $\pm$ 3 |
<center>**Table 5:** PPV (%) for predicting top-100 records on Texas-100X. Model is trained on *skewed* distribution.</center>

**Remark:** Similar to previous case, race's correlation to ethnicity has a huge impact on the inference task.


#### Results on out-of-distribution candidate set
    
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;High <br>(with Race) | &nbsp;&nbsp;&nbsp;&nbsp;Med <br>(with Race) | &nbsp;&nbsp;&nbsp;&nbsp;Low <br>(with Race) | &nbsp;&nbsp;&nbsp;&nbsp;High <br>(w/o Race) | &nbsp;&nbsp;&nbsp;&nbsp;Med <br>(w/o Race) | &nbsp;&nbsp;&nbsp;&nbsp;Low <br>(w/o Race) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Random | 28 $\pm$ 0 | 28 $\pm$ 0 | 28 $\pm$ 0 | 28 $\pm$ 0 | 28 $\pm$ 0 | 28 $\pm$ 0 |
| IP | 76 $\pm$ 5 | 76 $\pm$ 4 | 80 $\pm$ 2 | 37 $\pm$ 2 | 43 $\pm$ 4 | 41 $\pm$ 2 |
| IP$^\dagger$ | 81 $\pm$ 2 | 75 $\pm$ 2 | 80 $\pm$ 3 | 42 $\pm$ 3 | 40 $\pm$ 3 | 38 $\pm$ 7 |
| WB | 87 $\pm$ 2 | 87 $\pm$ 2 | 81 $\pm$ 3 | 51 $\pm$ 5 | 52 $\pm$ 4 | 50 $\pm$ 3 |
| WB$\cdot$IP | 86 $\pm$ 4 | 89 $\pm$ 2 | 85 $\pm$ 2 | 53 $\pm$ 2 | 53 $\pm$ 2 | 63 $\pm$ 3 |
| WB$\diamondsuit$IP | 74 $\pm$ 5 | 74 $\pm$ 2 | 85 $\pm$ 2 | 45 $\pm$ 2 | 47 $\pm$ 3 | 59 $\pm$ 4 |
| WB$\square$IP | 75 $\pm$ 1 | 81 $\pm$ 6 | 83 $\pm$ 3 | 46 $\pm$ 2 | 46 $\pm$ 3 | 58 $\pm$ 4 |
| WB$\cdot$IP$^\dagger$ | 88 $\pm$ 2 | 90 $\pm$ 2 | 84 $\pm$ 1 | 56 $\pm$ 4 | 53 $\pm$ 4 | 61 $\pm$ 4 |
| WB$\diamondsuit$IP$^\dagger$ | 78 $\pm$ 7 | 74 $\pm$ 5 | 85 $\pm$ 2 | 44 $\pm$ 2 | 46 $\pm$ 3 | 58 $\pm$ 4 |
| WB$\square$IP$^\dagger$ | 81 $\pm$ 5 | 78 $\pm$ 7 | 85 $\pm$ 3 | 45 $\pm$ 3 | 45 $\pm$ 2 | 57 $\pm$ 5 |
<center>**Table 6:** PPV (%) for predicting top-100 records from out-of-distributon candidate set (Texas-100X). Model is trained on *skewed* distribution.</center>



### Comments

- In all the above settings, the white-box attacks perform similar on both training and test candidates, unlike the membership inference case where the attacks perform dissimilar across training and test candidate sets.
- White-box attack outperforms even the imputation attack that has access to the class label. Thus, the model is leaking something beyond what an imputation can learn from the same data that the model is trained on. Is this because the imputation model is not learning effectively?
