---
title: "Revisiting Membership Inference Under Realistic Assumptions"
authors:
- admin
- Lingxiao Wang
- Katherine Knipmeyer
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

abstract: We study membership inference in settings where some of the assumptions typically used in previous research are relaxed. First, we consider skewed priors, to cover cases such as when only a small fraction of the candidate pool targeted by the adversary are actually members and develop a PPV-based metric suitable for this setting. This setting is more realistic than the balanced priors setting typically considered by researchers. Second, we consider adversaries that select inference thresholds according to their attack goals and develop a threshold selection procedure that improves inference attacks. Since previous inference attacks fail under in imbalanced prior setting, we develop a new inference attack based on the intuition that inputs corresponding to training set members will be near a local minimum in the loss function, and show that an attack that combines this with thresholds on the per-instance loss can achieve high PPV even in settings where other attacks appear to be ineffective.

# Summary. An optional shortened abstract.
summary: We propose novel membership inference attack and a threshold selection procedure to improve the existing attacks.

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