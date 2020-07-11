---
title: "Revisiting Membership Inference Under Realistic Assumptions"
authors:
- admin
- Lingxiao Wang
- David Evans
- Quanquan Gu

date: "2020-05-11T00:00:00Z"
doi: ""

math: true

# Schedule page publish date (NOT publication's date).
publishDate: "2020-06-21T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: In arXiv
publication_short: ""

abstract: Membership inference attacks on models trained using machine learning have been shown to pose significant privacy risks. However, previous works on membership inference assume a balanced prior distribution where the adversary randomly chooses target records from a pool that has equal numbers of members and non-members. Such an assumption of balanced prior is unrealistic in practical scenarios. This paper studies membership inference attacks under more realistic assumptions. First, we consider skewed priors where a non-member is more likely to occur than a member record. For this, we use metric based on positive predictive value (PPV) in conjunction with membership advantage for privacy leakage evaluation, since PPV considers the prior. Second, we consider adversaries that can select inference thresholds according to their attack goals. For this, we develop a threshold selection procedure that improves inference attacks. We also propose a new membership inference attack called Merlin which outperforms previous attacks. Our experimental evaluation shows that while models trained without privacy mechanisms are vulnerable to membership inference attacks in balanced prior settings, there appears to be negligible privacy risk in the skewed prior setting.

# Summary. An optional shortened abstract.
summary: We propose novel membership inference attack and a threshold selection procedure to improve existing threshold based membership inference attacks. We further explore membership inference attack in more realistic settings of skewed priors.

tags:
- Machine Learning
- Differential Privacy

featured: true

url_pdf: https://arxiv.org/pdf/2005.10881.pdf
url_code: https://github.com/bargavj/EvaluatingDPML
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

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