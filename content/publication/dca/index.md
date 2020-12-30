---
title: "Decentralized Certificate Authorities"
authors:
- admin
- Hannah Li
- David Evans
date: "2017-06-11T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2019-07-14T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: In *arXiv 2017*
publication_short: ""

abstract: The security of TLS depends on trust in certificate authorities, and that trust stems from their ability to protect and control the use of a private signing key. The signing key is the key asset of a certificate authority (CA), and its value is based on trust in the corresponding public key which is primarily distributed by browser vendors. Compromise of a CA private key represents a single point-of-failure that could have disastrous consequences, so CAs go to great lengths to attempt to protect and control the use of their private keys. Nevertheless, keys are sometimes compromised and may be misused accidentally or intentionally by insiders. We propose splitting a CA’s private key among multiple parties, and producing signatures using a generic secure multi-party computation protocol that never exposes the actual signing key. This could be used by a single CA to reduce the risk that its signing key would be compromised or misused. It could also enable new models for certificate generation, where multiple CAs would need to agree and cooperate before a new certificate can be generated, or even where certificate generation would require cooperation between a CA and the certificate recipient (subject). Although more efficient solutions are possible with custom protocols, we demonstrate the feasibility of implementing a decentralized CA using a generic two-party secure computation protocol with an evaluation of a prototype implementation that uses secure two-party computation to generate certificates signed using ECDSA on curve `secp192k1`.

# Summary. An optional shortened abstract.
summary: We use MPC to allow certificate authorities to sign digital certificates in a secure and distributed way.

tags:
- Multi-Party Computation
- Certificate Authority

featured: false

url_pdf: https://arxiv.org/pdf/1706.03370.pdf
url_code: https://github.com/hainali/decentralizedca
url_dataset: ''
url_poster: 'files/dca_poster.pdf'
url_project: ''
url_slides: 'files/dca_presentation.pdf'
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
projects:
- dca

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---
