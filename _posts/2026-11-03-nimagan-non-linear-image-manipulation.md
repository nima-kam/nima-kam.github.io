---
layout: post
title: "NIMaGAN: Non-linear image manipulation using iterative latent editing"
subtitle: "A sample-specific way to edit facial attributes in GAN latent space"
date: 2026-11-03 09:00:00 +0330
permalink: /2026-11-03-nimagan-non-linear-image-manipulation/
tags: [Generative Models, GANs, Image Editing]
cover-img:
  - "/assets/img/papers/nimagan-header.png": "Illustration of successive gradient steps in latent space and the resulting eyeglass edits."
thumbnail-img: "/assets/img/papers/nimagan-header.png"
share-img: "/assets/img/papers/nimagan-header.png"
---

Editing a face should change the attribute we choose without changing everything else. This is difficult when a single straight direction in a GAN's latent space does not describe the edit well. In NIMaGAN, we explore a more flexible direction that adapts to each input.

## The idea

A GAN maps a latent code to an image. Earlier editing methods often move that code along one shared, linear direction. This can work for some attributes. For others, it can also change identity or unrelated details.

We train a neural network to estimate an attribute from a latent code. The gradient of that estimate gives us an editing direction for that particular code. We then apply the direction repeatedly. This lets us move toward a chosen attribute value instead of relying on one fixed edit size.

We also vary the network's depth and activation functions. That gives us a way to adjust how non-linear the editing direction is. We evaluate edits to attributes such as age, gender, glasses, and smile.

<figure class="my-4">
  <img src="{{ '/assets/img/papers/nimagan-figure-1.png' | relative_url }}" alt="Examples of NIMaGAN edits for gender, glasses, and pose, shown from an original face through a series of controlled changes.">
<figcaption><small>Attribute-editing examples from Figure 1 of the NIMaGAN preprint. The edits illustrate changes to gender, glasses, and pose. See the <a href="https://doi.org/10.2139/ssrn.4768850">paper</a>.</small></figcaption>
</figure>

## What we found

We compare the method with InterfaceGAN using a face-identity measure on 250 latent codes. The non-linear directions generally preserve identity better across the tested attributes, especially in the more entangled Z space.

The examples above show what iterative editing looks like in practice. We can follow an edit in small steps, whether we are adding glasses or adjusting the angle of a face.

## Paper

Kambarani, N., Ahmadi, M. H., & Mohammadi, M. R. (2024). *NIMaGAN: Non-linear image manipulation using iterative latent editing*. SSRN. [https://doi.org/10.2139/ssrn.4768850](https://doi.org/10.2139/ssrn.4768850)
