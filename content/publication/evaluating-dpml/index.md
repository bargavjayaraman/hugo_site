---
title: "Evaluating Differentially Private Machine Learning in Practice"
authors:
- admin
- David Evans
date: "2019-08-14T00:00:00Z"
doi: ""

math: true

# Schedule page publish date (NOT publication's date).
publishDate: "2019-07-14T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *USENIX Security 2019*
publication_short: ""

abstract: Differential privacy is a strong notion for privacy that can be used to prove formal guarantees, in terms of a privacy budget, $\epsilon$, about how much information is leaked by a mechanism. When used in privacy-preserving machine learning, the goal is typically to limit what can be inferred from the model about individual training records. However, the calibration of the privacy budget is not well understood. Implementations of privacy-preserving machine learning often select large values of $\epsilon$ in order to get acceptable utility of the model, with little understanding of the impact of such choices on meaningful privacy. Moreover, in scenarios where iterative learning procedures are used, relaxed definitions of differential privacy are often used which appear to reduce the needed privacy budget but present poorly understood trade-offs between privacy and utility. In this paper, we quantify the impact of these choices on privacy in experiments with logistic regression and neural network models. Our main finding is that there is no way to obtain privacy for free -- relaxed definitions of differential privacy that reduce the amount of noise needed to improve utility also increase the measured privacy leakage. Current mechanisms for differentially private machine learning rarely offer acceptable utility-privacy trade-offs for complex learning tasks$:$ settings that provide limited accuracy loss provide little effective privacy, and settings that provide strong privacy result in useless models.

# Summary. An optional shortened abstract.
summary: We compare the privacy leakage of ML models trained with different differential privacy relaxations and different privacy budgets.

tags:
- Machine Learning
- Differential Privacy

featured: true

url_pdf: https://arxiv.org/pdf/1902.08874.pdf
url_code: https://github.com/bargavj/EvaluatingDPML
url_dataset: ''
url_poster: 'files/evaluating_dpml_poster.pdf'
url_project: ''
url_slides: 'files/evaluating_dpml_presentation.pdf'
url_source: ''
url_video: https://www.youtube.com/watch?v=JAGhqbY_U50

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
- evaluating-dpml

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---
{{< youtube JAGhqbY_U50 >}}
