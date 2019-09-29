---
title: "Privacy Preserving String Matching for Cloud Computing"
authors:
- Bruhadeshwar Bezawada
- Alex X. Liu
- admin
- Ann L. Wang
- Rui Li
date: "2015-06-29T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2019-07-14T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *International Conference on Distributed Computing Systems 2015*
publication_short: In *ICDCS 2015*

abstract: Cloud computing has become indispensable in providing highly reliable data services to users. But, there are major concerns about the privacy of the data stored on cloud servers. While encryption of data provides sufficient protection, it is challenging to support rich querying functionality, such as string matching, over the encrypted data. In this work, we present the first ever symmetric key based approach to support privacy preserving string matching in cloud computing. We describe an efficient and accurate indexing structure, the PASS tree, which can execute a string pattern query in logarithmic time complexity over a set of data items. The PASS tree provides strong privacy guarantees against attacks from a semi-honest adversary. We have comprehensively evaluated our scheme over large real-life data, such as Wikipedia and Enron documents, containing up to 100000 keywords, and show that our algorithms achieve pattern search in less than a few milliseconds with 100% accuracy. Furthermore, we also describe a relevance ranking algorithm to return the most relevant documents to the user based on the pattern query. Our ranking algorithm achieves 90%+ above precision in ranking the returned documents.

# Summary. An optional shortened abstract.
summary: We use MPC to allow certificate authorities to sign digital certificates in a secure and distributed way.

tags:
- Searchable Encryption

featured: false

url_pdf: https://ieeexplore.ieee.org/abstract/document/7164946
url_code: https://github.com/bargavjayaraman/SecureStringPatternSearch
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: 'files/searchable_encryption_presentation.pdf'
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/s9CC2SKySJM)'
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
