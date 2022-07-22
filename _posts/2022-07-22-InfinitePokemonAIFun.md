---
layout: post
title: Infinite Pokemon AI fun for kids
date: 2022-07-17
description: We use AI to generate infinite Pokémon drawings and cards for my kids
img: drawings_01.png
fig-caption: 
tags: [Image generation, Pixel art, Pokémon, DALL-E, Worksheet]
---

In the last few weeks, my older son has become completely obsessed with Pokémon and, although I'm not a Pokémon fan by any means, I have happily taken the opportunity to share some AI-powered fun with him.

In this post, I will present two ways in which we have been doing this. Both of them are based on the same underlying Machine Learning model: the [ruDALLE](https://github.com/ai-forever/ru-dalle) model fine-tuned on Pokémon images by [minimaxir](https://github.com/minimaxir/ai-generated-pokemon-rudalle).

Let's see what we've been doing:

# 1. Infinite imaginary Pokémon color-by-number

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/RobertoFont/Blog/blob/main/pixel-art-color-by-number-generator/Infinite-Pokemon-pixel-art-color-by-number-generator.ipynb)

In [a previous post](https://robertofont.github.io/InfiniteColor-by-numberWorksheetsForYourKids/) we developed a system to automatically generate color-by-number worksheets like the ones in [this website](https://www.coloringsquared.com/) from any input image. The original idea was to use the [ruDALLE](https://github.com/ai-forever/ru-dalle) model fine-tuned on Pokémon images we already mentioned as input to the system so that, instead of providing an input image, we could generate a new Pokémon image each time, thus having an infinite stream of Pokémon images at our disposal. At the time, I did not like the result. That's why we finally settled on starting from an input image. However, two things have changed since then:

- First of all, a very good friend of mine contributed some improvements that enhance the result we can obtain. This -having other people contributing to this blog- is something that makes me very happy.

- Second, as I said, my son has become Pokémon-obsessed so he doesn't really need that much to get excited. I found that he was actually enjoying what we were getting.

So, this time I connected the *AI Pokémon generator* with the color-by-number thing and created a Colab notebook that allows the generation of a worksheet with a single click. Since Pokémon are generated on the fly, you can generate infinite, always different coloring drawings.

You can find the project [here](https://github.com/RobertoFont/Blog/tree/main/pixel-art-color-by-number-generator) or just click the *Open in Colab* button above.

![Two of the color-by-number Pokémons]({{site.baseurl}}/assets/img/2022-07-22-InfinitePokemonAIFun/drawings_01.png)

# 2. "This Pokémon does not exist". Infinite imaginary Pokemon cards

The second one was even easier, as it is already done and ready to use. [This demo](https://huggingface.co/spaces/ronvolutional/ai-pokemon-card) hosted in the Hugging Face Hub lets you create imaginary Pokémon cards. It is based on the same model we used above and works within seconds with a single click.

Once you have generated a few cards, you can arrange them in A4 format, print them, hand a pair of scissors, and let the kid have fun.

<figure>
    <img src="{{site.baseurl}}/assets/img/2022-07-22-InfinitePokemonAIFun/cards_01.png"
         alt="AI-generated Pokemon trading cards" height="600">
</figure>

# 1+2

Although I have presented these two possibilities as different activities, my son has managed to close the circle and turn the color-by-number worksheets into his own Pokémon TCG cards :joy:

![Home-made Pokemon trading cards]({{site.baseurl}}/assets/img/2022-07-22-InfinitePokemonAIFun/pseudo_cards_01.png)

# Foreword

These two use-cases we've seen are, on the one hand, very simple, and, on the other hand, based on cutting-edge research: a DALLE model. The fact that I have been able to use it to have some silly fun with my kids is something that I have enjoyed and has made me think.

I have enjoyed it because, when you work on AI research, you do not often have the opportunity to share the thing you love with others. Just as an example, my mother does not have a single clue about what I do for a living.

And it has made me think because, usually, when you work doing research, you work on things that are quite unimpressive or just do not work at all. That's the essence of research: work on things that do not work **yet**. If something works, then it is not an area of research anymore; you go to Amazon and buy it. This is something that I have talked about sometimes with junior research scientists: the need to accept that you'll work on unimpressive things and not be frustrated by not being able to show your work with pride to your friends and family.

Nowadays, however, cutting-edge research is doing amazing things, like GPT-3, DALLE 2, or silly Pokémon drawings. This shows the degree of maturity that Machine Learning is achieving as a field.

Note that some people think that DALLE-like research is like doing circus tricks instead of focusing on the many fundamental problems that are still open. I do not disagree with this view, but I think both lines of thought are compatible.
