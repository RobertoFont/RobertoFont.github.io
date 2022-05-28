---
layout: post
title: Using Diffusion models to paint with style.
date: 2022-05-28
description: We use AI to generate artworks in the style of different painters.
img: Painting_01.png
fig-caption: 
tags: [Image generation, Diffusion, Text-to-image, Art generation]
---

Several methods for conditional image generation have been proposed in the last few years. Based on techniques like [Generative Adversarial Networks](https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf), [discrete Variational Autoencoders](https://arxiv.org/pdf/1711.00937.pdf) or [diffusion](https://arxiv.org/abs/2105.05233), image-generation models are starting to achieve impressive results, with [DALL·E 2](https://openai.com/dall-e-2/) being probably the latest and better known of them. It would be very interesting to perform a comparison of some of these systems, but this is something that I will leave for an upcoming post; today I want to focus on a model that I have been lately having a lot of fun with: [Disco-diffusion](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb).

In a nutshell, Disco-diffusion allows us to synthesize an image from a text prompt. You write something like *A field of daisies in a mountain valley* and *voilà*, the model will generate the picture for you. I especially like this model for several reasons:

- Although the foundational models ([diffusion](https://arxiv.org/abs/2105.05233) and [CLIP](https://github.com/openai/CLIP)) were developed by OpenAI, the final result builds upon many open-source contributions (you can read the details in the Credits section of the [notebook](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb)). I really like how the community has expanded and improved the capabilities of the original system as developed by a *tech giant*.

- As we will see, it allows us to control not only the content but also the style of our creations.

- It even makes it very easy to create animations.

- It accepts an initialization image, allowing some sort of co-creation. This is something I find so interesting that I will probably delve deeper in a separate post.

Today, we'll see how to:

- Control which painting technique is used in our artwork.

- Control the style.

- Control the presence and style of specific elements.

- Generate animations.

# Baseline

These are our baseline results from the prompt

### *A beautiful painting of a tumultuous sea crashing against the cliffs.*

[![A beautiful painting of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Painting_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Painting_01.png)

[![A beautiful painting of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Painting_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Painting_02.png)

Not bad, huh? Here, and in all cases below, images have been manually chosen from a total of 20 generated samples. 

# Media

We can very easily control the medium or technique by specifying it in the prompt:

### *A beautiful watercolor of a tumultuous sea crashing against the cliffs*

[![A beautiful watercolor of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Watercolor_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Watercolor_01.png)

[![A beautiful watercolor of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Watercolor_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Watercolor_02.png)

### *A beautiful photograph of a tumultuous sea crashing against the cliffs*

[![A beautiful photograph of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Photograph_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Photograph_01.png)

[![A beautiful photograph of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Photograph_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Photograph_02.png)

I'm not sure if these look quite like photographs, but the result is very interesting. We can see (click on the image for the full-size version) that the system did try to render photorealistic textures on the rocks and water surface.

### *A pencil sketch of a tumultuous sea crashing against the cliffs*

[![A pencil sketch of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/PencilSketch_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/PencilSketch_01.png)

[![A pencil sketch of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/PencilSketch_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/PencilSketch_02.png)

### *An old engraving of a tumultuous sea crashing against the cliffs*

[![An old engraving of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Engraving_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Engraving_01.png)

[![An old engraving of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Engraving_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Engraving_02.png)

This is another very interesting result. I think these images really do look like illustrations on an old book. 

### *A cartoon of a tumultuous sea crashing against the cliffs*

[![A cartoon of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Cartoon_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Cartoon_01.png)

[![A cartoon of a tumultuous sea crashing against the cliffs]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Cartoon_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Cartoon_02.png)

In this case, I would not say these are really cartoons; they look more like naive paintings to me.

# Style

We can just as easily take the style of any painter by including it in the prompt. It has, however, the side effect of introducing common motifs in the work of that particular artist. This way, we'll see flowers and 19th Century people in our *Renoir* works and, if we select Edward Hopper as our reference, we will see cosmopolite gentlemen and houses at The Hamptons appearing everywhere.

I'm not sure if this can be avoided. Let me know in the comments if you know how to do it.

However, it does not happens for every artist. See for example John Constable and Egon Schiele below.

### *A beautiful painting of a tumultuous sea crashing against the cliffs by Edward Hopper.*

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Edward Hopper]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Hopper_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Hopper_01.png)

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Edward Hopper]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Hopper_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Hopper_02.png)

### *A beautiful painting of a tumultuous sea crashing against the cliffs by Joaquin Sorolla.*

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Joaquin Sorolla]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Sorolla_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Sorolla_01.png)

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Joaquin Sorolla]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Sorolla_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Sorolla_02.png)

### *A beautiful painting of a tumultuous sea crashing against the cliffs by Renoir*

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Renoir]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Renoir_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Renoir_01.png)

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Renoir]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Renoir_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Renoir_02.png)

### *A beautiful painting of a tumultuous sea crashing against the cliffs by John Constable*

[![A beautiful painting of a tumultuous sea crashing against the cliffs by John Constable]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Constable_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Constable_01.png)

[![A beautiful painting of a tumultuous sea crashing against the cliffs by John Constable]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Constable_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Constable_02.png)

### *A beautiful painting of a tumultuous sea crashing against the cliffs by John William Waterhouse*

[![A beautiful painting of a tumultuous sea crashing against the cliffs by John William Waterhouse]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Waterhouse_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Waterhouse_01.png)

[![A beautiful painting of a tumultuous sea crashing against the cliffs by John William Waterhouse]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Waterhouse_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Waterhouse_02.png)

### *A beautiful painting of a tumultuous sea crashing against the cliffs by Egon Schiele*

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Egon Schiele]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Schielle_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Schielle_01.png)

[![A beautiful painting of a tumultuous sea crashing against the cliffs by Egon Schiele]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Schielle_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/Schielle_02.png)

# Elements

You can also ask for specific elements and even specify a style for them. You can see in the example below that not only the house is included, but it also shows the style of a particular architect.

### *A beautiful watercolor of a singular house designed by Frank Lloyd Wright on top of a hill above a river*

[![A beautiful watercolor of a singular house designed by Frank Lloyd Wright on top of a hill above a river]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/House_01.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/House_01.png)

[![A beautiful watercolor of a singular house designed by Frank Lloyd Wright on top of a hill above a river]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/House_02.png)]({{site.baseurl}}/assets/img/2022-05-28-UsingDiffusionToPaintWithStyle/House_02.png)

# Animation

Finally, it is also possible to generate animations. We can zoom, pan, or rotate the initial image and the result will be used as initialization for the next frame. Then the process is repeated for the next frame and so on. We can specify both different prompts and different zoom/pan/rotate values for different points in time.

I think it is a cool feature, but the result is very hard to control.

Here is an example:

<iframe width="560" height="315" src="https://www.youtube.com/embed/zeh1E0NaWmw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

and these are the parameters that were used:

angle: 0:(0)

zoom: 0: (1), 10: (1.05), 180: (1)

translation_x: 0: (0)

translation_y: 0: (0), 180: (5.0)

translation_z: 0: (10.0), 180: (0)

rotation_3d_x: 0: (0)

rotation_3d_y: 0: (0)

rotation_3d_z: 0: (0)

text_prompts = { 0: ["A beautiful painting of a miniature rainforest contained inside a crystal ball resting in the sand of a desert."], 100: ["A beautiful painting of a magnificent oasis in the desert."],

200: ["A beautiful painting of a rainbow passing through a giant ruby floating in the sky above a desert."]

}

# Limitations

As much as I like this technique, it also has some limitations:

- As we have seen, sometimes it tends to repeat certain elements again and again.

- It is not physically grounded. You can obtain things like water at different levels or impossible constructions.

- It is terrible at generating human or animal figures. Try to generate a human face at your own risk.