---
layout: post
title: "Parameter efficient face frontalization in image sequences via GAN inversion"
subtitle: "Using a few views together to reconstruct a frontal face with fewer trainable parameters"
date: 2026-11-03 09:01:00 +0330
permalink: /2026-11-03-parameter-efficient-face-frontalization/
tags: [Computer Vision, GAN Inversion, Face Frontalization]
cover-img:
  - "/assets/img/papers/frontalization-header.png": "A sequence of adult face views flows through a feature-fusion pipeline to a frontal reconstruction."
thumbnail-img: "/assets/img/papers/frontalization-header.png"
share-img: "/assets/img/papers/frontalization-header.png"
---

A face image can hide details when it is turned away from the camera. A video can help because nearby frames show different parts of the face. In this paper, we ask how to use those extra views without training a large network from scratch.

## What we built

We generated a synthetic dataset specifically for face frontalization. Each identity has eight views: one frontal reference and seven views from different angles. These paired views let us train and evaluate the model across a range of face poses.

We built small trainable adapters on top of a pretrained GAN inversion model and kept its original weights fixed. For video sequences, we added an adapter that uses attention to combine information across frames. Different angles reveal different facial details, and bringing those details together helps preserve identity in the reconstructed frontal view.

<figure class="my-4">
  <img src="{{ '/assets/img/papers/frontalization-sequence-results.png' | relative_url }}" alt="An adult face across several angled input frames, followed by the frontalized output. The image is cropped to show the adult example only.">
  <figcaption><small>Adult multi-frame example from the authors' <a href="https://github.com/mhahmadi258/Face-frontalization-in-image-sequences-using-GAN-Inversion">companion results</a>, cropped to show this example only. Adapted from Ahmadi et al. (2025) under the <a href="https://creativecommons.org/licenses/by/4.0/">CC BY 4.0 license</a>. See the <a href="https://doi.org/10.1049/ipr2.70003">article</a> for the method and full evaluation.</small></figcaption>
</figure>

## What we found

Our single-image model used 11.7 million trainable parameters, over 91% fewer than either of the two GAN inversion baselines we compared. On the synthetic test set, identity similarity rose from 0.75 with pSp to 0.86 with our single-image model and reached 0.87 when we combined multiple frames.

## Paper and resources

Ahmadi, M., Kambarani, N., & Mohammadi, M. R. (2025). *Parameter efficient face frontalization in image sequences via GAN inversion*. *IET Image Processing, 19*(1), e70003. [https://doi.org/10.1049/ipr2.70003](https://doi.org/10.1049/ipr2.70003)

The article is open access under a Creative Commons Attribution license. The figure above is credited to the companion implementation and cropped to show the adult example. The [code and dataset](https://github.com/mhahmadi258/Face-frontalization-in-image-sequences-using-GAN-Inversion) are available from the project repository.
