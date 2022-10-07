---
layout: post
title: Getting started with Stable Diffusion
date: 2022-10-07
description: Get started with Stable Diffusion, an Open Source text-to-image system
img: StormComing.png
fig-caption: 
tags: [Image generation, StableDiffusion, Text-to-image, Art generation]
---

In [our previous post](https://robertofont.github.io/FirstStepsDalle2/), we covered our first steps with DALL-E 2, the text-to-image system. As powerful as it is, OpenAI has received a lot of criticism for not sharing the model itself with the community, and we anticipated it could be soon matched or even surpassed by an Open Source initiative. Soon after, the most important Open Source text-to-image model to date was released: [Stable Diffusion](https://stability.ai/blog/stable-diffusion-public-release).

Stable Diffusion is a [latent diffusion model](https://arxiv.org/abs/2112.10752)  created by the [CompVis Machine Vision and Learning research group at the Ludwig Maximilian University of Munich](https://github.com/CompVis) with the financial support of [Stability AI](https://stability.ai/) and trained on the [LAION-Aesthetics dataset](https://laion.ai/blog/laion-aesthetics/), put together by the research collective [LAION](https://laion.ai/). LAION Aesthetics is a sub-set of [LAION-5B](https://laion.ai/blog/laion-5b/), a dataset of 5,85 billion text-image pairs scraped from the web, filtered by using a CLIP model trained to score how *aesthetic* a particular image is. Stable Diffusion was originally released for academic research on August 10th, was soon integrated into Hugging Face [Diffusers library](https://github.com/huggingface/diffusers), and a few weeks later was made generally available under a [CreativeML Open RAIL-M license](https://huggingface.co/spaces/CompVis/stable-diffusion-license).

Since then, an ecosystem has started growing around Stable Diffusion. For me, however, these have been busy weeks and I have not had the chance to give it a try yet, so I've decided to do a *first steps with Stable Diffusion post* just like I did with DALL-E 2. I hope you like it, but bear in mind that there are more up-to-date and deep analyses out there.

# Getting started

The first thing I did was look for easy ways to get started. Here are a few resources that can serve you as a starting point:

- [This demo](https://huggingface.co/spaces/stabilityai/stable-diffusion) lets you try Stable Diffusion for free without any coding.

- Stability AI has released [DreamStudio](https://beta.dreamstudio.ai), a GUI that allows for more advanced use, including tweaking parameters, inpainting, image-to-image, etc. You can try it out for free, but will eventually need to purchase credits to continue using it.

- [This notebook](https://colab.research.google.com/github/huggingface/notebooks/blob/main/diffusers/stable_diffusion.ipynb) illustrates how to use Stable Diffusion through Hugging Face Diffusers.

- [The official repo](https://github.com/CompVis/stable-diffusion)

- [Model card](https://github.com/CompVis/stable-diffusion/blob/main/Stable_Diffusion_v1_Model_Card.md)

# First generations

The next thing I did was try and reproduce some of the prompts we used in the [DALL-E 2 post](https://robertofont.github.io/FirstStepsDalle2/). I decided to use the Hugging Face notebook above since it is easy enough to use and it allows you to generate a batch of images from the same prompt.

### *A kangaroo with an eye patch playing castanets in front of the Eiffel Tower*

Weird... But still, better than [DALL-E 2 first try](https://robertofont.github.io/assets/img/2022-08-10-FirstStepsDalle2/Kangaroo_001.png).

![A kangaroo with an eye patch playing castanets in front of the Eiffel Tower]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/Kangaroo_01.png)

### *A shiba inu wearing a beret and black turtleneck*

This now classic prompt gives us some cool results.

![A shiba inu wearing a beret and black turtleneck]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/ShibaInu_001.png)

### *A high-quality photograph of a wolf wearing a beret and black turtleneck, 4k*

This gives us some successful renders...

![A high-quality photograph of a wolf wearing a beret and black turtleneck, 4k]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/Wolf_001.png)

...and other maybe less successful but equally interesting ones...

![A high-quality photograph of a wolf wearing a beret and black turtleneck, 4k]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/Wolf_002.png)

Later, I tried some prompts from our [DiscoDiffusion post](https://robertofont.github.io/UsingDiffusionToPaintWithStyle/):

### *A beautiful painting of a tumultuous sea crashing against the cliffs by Joaquin Sorolla.*

![A beautiful painting of a tumultuous sea crashing against the cliffs by Joaquin Sorolla]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/SeaSorolla_001.png)

### *A beautiful painting of a tumultuous sea crashing against the cliffs by John William Waterhouse*

![A beautiful painting of a tumultuous sea crashing against the cliffs by John William Waterhouse]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/SeaWaterhouse_001.png)

The results were not bad, but I would say these look a lot less like paintings than their Disco Diffusion counterparts.

# Something a bit more advanced

With a bit more work (although I'll leave advanced prompt design for a future post), we can get some cool storm-coming vibes:

[![Storm coming vibes]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/StormComingVibes.png)]({{site.baseurl}}/assets/img/2022-10-07-GettingStartedStableDiffusion/StormComingVibes.png)

# Comparison with other systems

Some general impressions on how Stable Diffusion compares with other systems we have worked with before:

## With respect to DALL-E 2

### Pros:

- Open and free to use

- No filters or limitations (well, actually, it comes with an NSFW filter enabled by default, but it is easy enough to disable it if you want)

### Cons:

- Needs more elaborate prompts. DALL-E 2 tends to work much better with simple prompts.

## With respect to DiscoDiffusion

### Pros:

- Generates globally coherent and plausible images. [As we saw earlier](https://robertofont.github.io/UsingDiffusionToPaintWithStyle/), DiscoDiffusion tends to generate repeating patterns at different scales or different parts of the image.

- Good with anatomy. In general, DiscoDiffusion sucks at generating people and animals (although some people have devoted a lot of work to this and come a long way).

### Cons:

- DiscoDiffusion generates more *fine arts-like* images. Not sure what is the reason for this, but it seems to me that it is easier to achieve a painting-like effect and the style of a particular painter with DiscoDiffusion.

# Foreword

I think this model represents a landmark. Not because of the model itself, but because of how it represents a new paradigm: independent researchers, generally available, trained on an open corpus that is the result of a collective effort. And it is, to some extent, a reaction to DALL-E 2 being kept private and including lots of filters and limitations. As Jack Clark wrote in his newsletter [ImportAI](https://jack-clark.net/): *StabilityDiffusion looks at a load of PR-friendly control systems laid over proprietary products and just openly laughs at them - that's a strange thing that will have big implications*.
