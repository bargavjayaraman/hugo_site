---
title: "Distributed Learning without Distress: Privacy-Preserving Empirical Risk Minimization"
authors:
- admin
- Lingxiao Wang
- David Evans
- Quanquan Gu
date: "2015-9-12-04T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2019-07-14T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *Neural Information Processing Systems 2018*
publication_short: In *NeurIPS 2018*

abstract: Distributed learning allows a group of independent data owners to collaboratively learn a model over their data sets without exposing their private data. We present a distributed learning approach that combines differential privacy with secure multi-party computation. We explore two popular methods of differential privacy, output perturbation and gradient perturbation, and advance the state-of-the-art for both methods in the distributed learning setting. In our output perturbation method, the parties combine local models within a secure computation and then add the required differential privacy noise before revealing the model. In our gradient perturbation method, the data owners collaboratively train a global model via an iterative learning algorithm. At each iteration, the parties aggregate their local gradients within a secure computation, adding sufficient noise to ensure privacy before the gradient updates are revealed. For both methods, we show that the noise can be reduced in the multi-party setting by adding the noise inside the secure computation after aggregation, asymptotically improving upon the best previous results. Experiments on real world data sets demonstrate that our methods provide substantial utility gains for typical privacy requirements.

# Summary. An optional shortened abstract.
summary: We combine differential privacy and MPC for privacy preserving distributed learing of strongly-convex ERM algorithms.

tags:
- Machine Learning
- Differential Privacy
- Multi-Party Computation

featured: false

url_pdf: http://papers.nips.cc/paper/7871-distributed-learning-without-distress-privacy-preserving-empirical-risk-minimization
url_code: https://github.com/bargavj/distributedMachineLearning
url_dataset: ''
url_poster: 'files/dp_erm_poster.pdf'
url_project: ''
url_slides: 'files/dp_erm_presentation.pdf'
url_source: ''
url_video: https://www.youtube.com/watch?time_continue=4&v=rwyWiDyVmjE

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/jdD8gXaTZsc)'
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
{{< youtube rwyWiDyVmjE >}}