---
title: "Efficient Privacy-Preserving Nonconvex Optimization"
authors:
- Lingxiao Wang
- admin
- David Evans
- Quanquan Gu

date: "2019-10-30T00:00:00Z"
doi: ""

math: true

# Schedule page publish date (NOT publication's date).
publishDate: "2020-07-11T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: In arXiv
publication_short: ""

abstract: While many solutions for privacy-preserving convex empirical risk minimization (ERM) have been developed, privacy-preserving nonconvex ERM remains under challenging. In this paper, we study nonconvex ERM, which takes the form of minimizing a finite-sum of nonconvex loss functions over a training set. To achieve both efficiency and strong privacy guarantees with efficiency, we propose a differentially-private stochastic gradient descent algorithm for nonconvex ERM, and provide a tight analysis of its privacy and utility guarantees, as well as its gradient complexity. We show that our proposed algorithm can substantially reduce gradient complexity while matching the best-known utility guarantee obtained by Wang et al. (2017). We extend our algorithm to the distributed setting using secure multi-party computation, and show that it is possible for a distributed algorithm to match the privacy and utility guarantees of a centralized algorithm in this setting. Our experiments on benchmark nonconvex ERM problems and real datasets demonstrate superior performance in terms of both training time and utility gains compared with previous differentially-private methods using the same privacy budgets.

# Summary. An optional shortened abstract.
summary: We propose novel differentially private algorithms for efficient non-convex empirical risk minimization that significantly improve the gradient complexity compared to the existing state-of-art differentially private algorithms. We also propose how to extend our algorithms to the distributed settings.

tags:
- Machine Learning
- Differential Privacy
- Multi-Party Computation

featured: true

url_pdf: https://arxiv.org/pdf/1910.13659.pdf
url_code: ''
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
- ppml

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---