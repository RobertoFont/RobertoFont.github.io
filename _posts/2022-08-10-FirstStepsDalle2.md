---
layout: post
title: My first steps with DALL-E 2
date: 2022-08-10
description: We create our first images using DALL-E 2 and recreate an old piece
img: DALLE2_first.png
fig-caption: 
tags: [Image generation, DALL-E, Text-to-image, Art generation]
---

A few days ago, I finally got access to [DALL-E 2](https://openai.com/dall-e-2/). The first thing I did was to turn to my partner and ask her for the most bizarre prompt she could think about. The output was:

### *A kangaroo with an eye patch playing castanets in front of the Eiffel Tower*

[![A kangaroo with an eye patch playing castanets in front of the Eiffel Tower]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Kangaroo_001.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Kangaroo_001.png)

Well, that was actually... **very disappointing**. I quickly tried a second one:

### *A wolf riding on a motorcycle through the desert*

[![A wolf riding on a motorcycle through the desert]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_motorcycle_001.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_motorcycle_001.png)

WTF! That looks even worse!

Was I using the *real* DALL-E 2 or some kind of toned-down version? I used a prompt from [the original paper](https://arxiv.org/abs/2204.06125) to check whether the results were comparable:

### *A shiba inu wearing a beret and black turtleneck*

[![A shiba inu wearing a beret and black turtleneck]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/ShibaInu_001.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/ShibaInu_001.png)

Well, that actually looks amazing, just like in the paper. Let's try to change the prompt a bit:

### *A wolf wearing a beret and black turtleneck*

[![A wolf wearing a beret and black turtleneck]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_001.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_001.png)

**What?!** How is that possible? How can quality drop so much by just swapping a single word? At this point, conspiracy theories started to form in my mind: could it be possible that the examples on the [DALL-E 2 paper](https://arxiv.org/abs/2204.06125) were so heavily cherry-picked that even the slightest change causes the model to fail? This is an academic scandal, I will expose them and win a Pulitzer!

And then I tried this:

### *A wolf wearing a beret and black turtleneck, digital art*

[![A wolf wearing a beret and black turtleneck, digital art]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_002.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_002.png)

and this:

### *A high-quality photograph of a wolf wearing a beret and black turtleneck, 4k*

[![A high-quality photograph of a wolf wearing a beret and black turtleneck, 4k]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_005.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Wolf_005.png)

Those look much better indeed. My theories were a bit less wild now: a dog wearing some clothes is something that you can find in real life. My other prompts, on the other hand, were highly implausible. It seems that when you ask for something really weird you need to provide DALL-E with some more guidance by adding modifiers (we covered modifiers in depth in a [previous post](https://robertofont.github.io/UsingDiffusionToPaintWithStyle/)).

Here is the digital art kangaroo just for your viewing pleasure:

[![A kangaroo with an eye patch playing castanets in front of the Eiffel Tower, digital art]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Kangaroo_003.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Kangaroo_003.png)

# Recreating a *classic*

That was fine to get a better grasp of how DALL-E 2 works. However, I'm not as interested in the ability of these kinds of models to generate memes as I am in their possibilities as creative tools. I decided to do a little experiment: a looong time ago, I used to play around with 3D rendering and made this piece (and trust me, I'm really embarrassed to share it now):

![A woman looking through a window on a rainy day]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/Ventana.jpg)

I tried to recreate it using DALL-E 2. It took some tinkering around with the prompt, but I ended up being quite happy with the result. It has some rainy day mood indeed:

[![DALL-E 2 recreation]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/DALLE2_first.png)]({{site.baseurl}}/assets/img/2022-08-10-FirstStepsDalle2/DALLE2_first.png)

# Conclusion

I like what DALL-E 2 can do, but I have not been utterly impressed by it. Some freely available models will likely improve upon DALL-E 2 in the near future.

What I find most fascinating about art-generating models are the endless possibilities they bring in the co-creation between the artist and the model. I think we have already reached the point where these models can be a really useful tool for any artist (digital or not). Think of the little experiment I did: it could be an easy way to quickly explore different compositions or color schemes, even if you were to later produce the final artwork using traditional media. You don't need to be a digital artist, or an AI artist, to benefit from DALL-E 2 and the like.
