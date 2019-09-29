---
title: Analysis of Private ML Models
summary: Comparing the differential privacy implementations by quantifying their privacy leakage.
tags:
- Machine Learning
- Differential Privacy

date: "2018-08-22T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: ""
  focal_point: Smart

links:
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
Machine learning models are being extensively trained on sensitive human data (such as pictures, videos and patient health records) and are being publicly deployed as a service. With such systems in  place, privacy of the individuals involved in the model training becomes a real concern. While differential privacy provides a solution to this problem, there is always a privacy-utility trade-off when training models privately, which is not well understood. Often the practical deployments choose the model utility over privacy, that may lead to indiscernable privacy vulnerabilities. One such example of privacy vulnerability is whether an adversary can identify a particular individual in the training data. Also, what type of individuals are more vulnerable to such attacks? This question is also directly related to the problem of fairness. In light of such vulnerabilities, what privacy parameters should the ML deployments use to mitigate the risks? Our project tries to shed light on these questions.