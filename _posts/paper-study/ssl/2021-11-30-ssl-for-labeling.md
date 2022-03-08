---
layout: post
title: "Self-supervised Semi-supervised Learning for Data Labeling and Quality Evaluation"
categories: study self-supervised learning
---
Paper link: [Self-supervised Semi-supervised Learning for Data Labeling and Quality Evaluation](https://arxiv.org/pdf/2111.10932.pdf)
<!-- What topic of paper / hypothesis / objectives -->
### What
Tackle the problems of efficient data labeling and annotation verification under the human in the loop setting. Propose a unigying framework by leveraging self-supervised semi supervised learning and use it to construct workflows for data labeling and annotation verification tasks.
 
### Why 
There are many industrial applications that do not have readily available labels. As a result a large part of the machine learning life cycle is data engineering which often requires painstaking manual annotation and inspection that are expensive and time-consuming.
 
To reduce the amount of human effort it is necessary to automate the data curation process and reduce the number of labels needed for good performance. Active learning can reduce.

### How
Leverage self-supervised learning, specifically contrastive learning methods to obtain and unsupervised representation for the unlabeled data. Then construct a nearest neighbor graph over data samples based on th learned representations. Finally we can use the nearest neighbor graph for various downstream tasks.

Used BYOL which allows to retrieve a representation in a latent space. Then a graph nearest enighbor graph is built. Nearby nodes are likely to have the same label, we can perform label propagation on the nearest neighbor graph to propagate information from samples with known labels to samples without label or with noisy labels.

<!-- results -->
<!-- ### Results -->

### Conclusion
In summary leveraging the latest advances in sef supervised learning, we developed a nearest neighbor graph-based approach that can perform versatile downstram tasks and quickly incoporate new information in a semi-supervised mannel, suitable for integration with real time human in the loop systems.
