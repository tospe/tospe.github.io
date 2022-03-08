---
layout: post
title: "Do GANs actually learn the distribution? An empirical study"
categories: study gans
---
Paper link: [Do GANs actually learn the distribution? An empirical study](https://arxiv.org/pdf/1706.08224.pdf)
<!-- What topic of paper / hypothesis / objectives -->
### What
The question has been raised whetehr or not gans actually learn the distribution they are trained with. Now that gans differ from many previous methods for learning distributions in that they do not provide na estimate of some measure of distribution fit.

Researchers have been using surrogate quality tests, which were designed to rule out the most obvious failure mode of training. One test checks the similarity of each generated image to the nearest images in the training set. Another takes two random seeds, s1,s2 that produce realistic images and checks the images produced using seed lying in the line joining s1,s2, if such "interpolating" images are reasomnable and original.


### Why
Recently a new theoretical analysis of GANs with finite sample sizes and finite discriminator size revealed the possibility that training may sometimes appear to succeed even if the generator is far from having actually learnt the distribution. 

Specifically, if the discriminator has size n, then the training objective could be ε from optimal even though the output distribution is supported on only O(nlogn/ε2) images. By contrast one imagines that the target distribution usually must have very large support.

This can relates to the Birthday paradox: there are k people in a room, how large must k be bedore we have a high likedlihood of having two people with the same birthday.

<!-- Metodology -->
### How
Gan setting the distribution is continuous not discrete. When support size is infinite then in a finite sample, we should not expexta exat duplcuate images where every pixel is identical. Thus a priori one imagines the birthday paradox test to completely not work. But it still works if we llook for near-duplicates.
 
20 pairs were selected to some heuristic metric, thsu obtaining a candidate pool of potential near-duplicates inspect.
 
Two datasets used:
- Celeb: celebrity images --> heuristic used was a euclidean distance in pixel space
- Cifar-10: 60k 32x32 color images in 10 classes --> trained a convnet to generate embeddings then the heuristic is the euclidean distance in the embedding space
 


<!-- results -->
### Results
CelebA:
- DCGAN, MIX+GAN, Adversarily Learned Inference
- DCGAN and  MIX+GAN: Prob >= 50% a batch of 400 samples contains at least one pair of duplicates --> distribution is less than 400^2 ~ 160k which is lower than the diversity of the training set
- ALI/BIG GAN --> 50% prob with a batch of 1000, size of 1Million 5x dataset, but smaller than the diversity one would expect among human faces

Cifar-10:
- Pretrained CONVNET to retrieve the embeddings since the euclidean distance in pixel space is not informative.
- The result of the test is affected by the quality of samples. Training uses noised samples then the generated samples are also quite noisy
- DCGAN generated mostly blobs, stacked GAN was able to generate the most real-looking images, since the model is trained by conditionaing on class label, we measure its diversity within each class separately
- Closest image is quite different from the duplicate detected which suggests the issue with the GANs is indeed lack of diversity (low support size) instead of memorizing training set

![Gans Distribution Close](/assets/images/gans_distribution.png)

<!-- thoughts? conclusion -->
### Conclusion
Experiments using this test suggest that current GANs approaches, specifically, the ones that produce images of higher visual quality, fall significantly short of learning the target distribution, and in fact the support size of the generated distribution is rather low (mode collapse).
 
Our rough experiments also suggest —again in line with the theoretical analysis—that the size of the distribution’s support scales near-linearly with discriminator capacity; though this conclusion needs to be rechecked with more extensive experiments.