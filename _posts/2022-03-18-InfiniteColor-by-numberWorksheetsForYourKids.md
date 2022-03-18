---
layout: post
title: Infinite color-by-number worksheets for your kids
date: 2022-03-18
description: We build a system to automatically generate a color-by-number worksheet for kids. We also try some image-generation models.
img: color-by-number-generator.png
fig-caption: 
tags: [Image generation, Pixel art, Worksheet] 
---

My older son loves coloring the worksheets in [this website](https://www.coloringsquared.com/) -his younger brother also likes it, although he is more of a [freestyler]({{site.baseurl}}/assets/img/2022-03-18-InfiniteColor-by-numberWorksheetsForYourKids/freestyle.jpg)-. He likes it so much that it is becoming increasingly difficult to find worksheets that he likes and has not done before. Since I'm one of the 2 or 3 coolest dads in the world (five at most), I decided to build a system to automatically generate a new worksheet whenever it's needed. Take that, Santa Claus!

# The project

![Color-by-number worksheet generator]({{site.baseurl}}/assets/img/2022-03-18-InfiniteColor-by-numberWorksheetsForYourKids/color-by-number-generator.gif)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/RobertoFont/Blog/blob/main/pixel-art-color-by-number-generator/Pixel-art-color-by-number-generator.ipynb)

You can find the project at [Blog/pixel-art-color-by-number-generator at main · RobertoFont/Blog · GitHub](https://github.com/RobertoFont/Blog/tree/main/pixel-art-color-by-number-generator) or simply click the *Open in Colab* button above.

The project allows the creation of a color-by-number worksheet from any image. The code automatically performs the following steps:

- Crop a square region in the center of the image.

- Resize the image to 24x24.

- Limit the number of colors to a predefined quantity.

- Create a ready-to-print worksheet.

Note, however, that the input image should be already a pixel-art image. Otherwise, the resulting image will lack any well-defined details.

The worksheet can be generated in any of three variants:

- Each cell displays the number of the corresponding color.

- Each cell displays an addition that must be solved to obtain the corresponding color.

- Each cell displays a subtraction that must be solved to obtain the corresponding color.

<img src="{{site.baseurl}}/assets/img/2022-03-18-InfiniteColor-by-numberWorksheetsForYourKids/modes.png" title="" alt="Different modes" data-align="center">

# What went wrong and how

Note that *what went wrong and why* would be a more productive question but then this would be a serious blog.

If you have read until here, I can tell you the truth: I'm not one of the coolest dads in the world. This is a post about failure. Manually choosing and uploading an image is *meh* at best; the original idea was to use an image-generation system to automatically generate infinite worksheets. I did not succeed at this, however, which strikes me, considering that we are just a tiny step away from General Artificial Intelligence, robots could dominate the world any minute now, GPT-3 is more dangerous than Ultron and all that.

My first try was with [this cool notebook](https://colab.research.google.com/drive/1A3t2gQofQGeXo5z1BAr1zqYaqVg3czKd) that allows the generation of infinite Pokemon. Which I did (click on the image to see the 1000+ Pokemon):

[![Sample of the generated Pokemon]({{site.baseurl}}/assets/img/2022-03-18-InfiniteColor-by-numberWorksheetsForYourKids/pokemon_sample.jpg)]({{site.baseurl}}/assets/img/2022-03-18-InfiniteColor-by-numberWorksheetsForYourKids/pokemons_l.png)

This notebook uses a [ru-dalle](https://github.com/sberbank-ai/ru-dalle) model (we have already talked about ru-dalle in [previous posts](https://robertofont.github.io/IllustratedFairyTales/)) fine-tuned on Pokemon images. The code can be found [here](https://github.com/minimaxir/ai-generated-pokemon-rudalle). As cool as it is, the thing is that images do not look good once you pixelate them. To be successfully pixelated to such a low resolution, the image should have been designed as pixel art from the outset, with very salient features. Otherwise, you just get a bunch of meaningless pixels.

![Pixelated image]({{site.baseurl}}/assets/img/2022-03-18-InfiniteColor-by-numberWorksheetsForYourKids/ex_pok_pix.png)

My second option was another ru-dalle variant, [Emojich](https://github.com/sberbank-ai/ru-dalle/blob/master/Emojich.md), to try and generate simpler images. The resulting images, however, suffered from the same problem and they were often a bit weird (look at that clown saying 'hi'...):

<figure>
    <img src="{{site.baseurl}}/assets/img/2022-03-18-InfiniteColor-by-numberWorksheetsForYourKids/emojich.png"
         alt="Emojich weird results">
    <figcaption><em>Text prompts: "A clown saying hi", "Lego Hulk", "Iron Man wearing a cowboy hat", "Pixel-art dog", "Superman smiling", "Spiderman".</em></figcaption>
</figure>

The solution is probably to explicitly generate pixel art, but, at this point, I decided to give up. Don't look at me like that; I told you from the beginning (of the section) that I'm not one of the coolest dads in the world.
