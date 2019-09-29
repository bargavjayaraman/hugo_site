---
title: Decentralized Certificate Authorities
summary: Allowing certificate authorities to sign digital certificates in a secure and distributed way.
tags:
- Multi-Party Computation
- Certificate Authority

date: "2017-03-27T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: https://oblivc.org/dca/

image:
  caption: ""
  focal_point: Smart
---
Certificate authorities have a single point of failure in signing the digital certificates -- what if their signing key gets stolen? This is possible if the signing key is stored on a single machine. Instead, we propose secret sharing of signing keys across multiple machines such that the certificate authorites can combine the secret shares within the multi-party computation protocol and sign the digital certificate in an encrypted way.  