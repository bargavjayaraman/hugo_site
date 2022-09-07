---
title: "Are Attribute Inference Attacks Just Imputation?"
authors:
- admin
- David Evans

date: "2022-09-02T00:00:00Z"
doi: ""

math: true

# Schedule page publish date (NOT publication's date).
publishDate: "2022-09-06T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: In arXiv
publication_short: ""

abstract: Models can expose sensitive information about their training data. In an attribute inference attack, an adversary has partial knowledge of some training records and access to a model trained on those records, and infers the unknown values of a sensitive feature of those records. We study a fine-grained variant of attribute inference we call sensitive value inference, where the adversary's goal is to identify with high confidence some records from a candidate set where the unknown attribute has a particular sensitive value. We explicitly compare attribute inference with data imputation that captures the training distribution statistics, under various assumptions about the training data available to the adversary. Our main conclusions are--- (1) previous attribute inference methods do not reveal more about the training data from the model than can be inferred by an adversary without access to the trained model, but with the same knowledge of the underlying distribution as needed to train the attribute inference attack; (2) black-box attribute inference attacks rarely learn anything that cannot be learned without the model; but (3) white-box attacks, which we introduce and evaluate in the paper, can reliably identify some records with the sensitive value attribute that would not be predicted without having access to the model. Furthermore, we show that proposed defenses such as differentially private training and removing vulnerable records from training do not mitigate this privacy risk.

# Summary. An optional shortened abstract.
summary: We propose a white-box attribute inference attack that is able to extract distribution information from the model.

tags:
- Machine Learning
- Differential Privacy

featured: true

url_pdf: https://arxiv.org/abs/2209.01292
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