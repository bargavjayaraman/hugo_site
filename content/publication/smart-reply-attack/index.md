---
title: "Combing for Credentials: Active Pattern Extraction from Smart Reply"
authors:
- admin
- Esha Ghosh
- Melissa Chase
- Sambuddha Roy
- Huseyin Inan
- Wei Dai
- David Evans

date: "2022-07-14T00:00:00Z"
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

abstract: With the wide availability of large pre-trained language models such as GPT-2 and BERT, the recent trend has been to fine-tune a pre-trained model to achieve state-of-the-art performance on a downstream task. One natural example is the "Smart Reply" application where a pre-trained model is tuned to provide suggested responses for a given query message. Since these models are often tuned using sensitive data such as emails or chat transcripts, it is important to understand and mitigate the risk that the model leaks its tuning data. We investigate potential information leakage vulnerabilities in a typical Smart Reply pipeline and introduce a new type of active extraction attack that exploits canonical patterns in text containing sensitive data. We show experimentally that it is possible for an adversary to extract sensitive user information present in the training data. We explore potential mitigation strategies and demonstrate empirically how differential privacy appears to be an effective defense mechanism to such pattern extraction attacks.

# Summary. An optional shortened abstract.
summary: We propose black-box and gray-box active pattern extraction attacks that extract sensitive data patters from the Smart Reply model.

tags:
- Machine Learning
- Differential Privacy

featured: true

url_pdf: https://arxiv.org/abs/2207.10802
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
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---