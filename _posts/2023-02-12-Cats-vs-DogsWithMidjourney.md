---
layout: post
title: Cats vs Dogs with Midjourney
date: 2023-02-11
description: An illustrated cats vs dogs chess game using the text-to-image system Midjourney AI
img: Cats_queen.png
fig-caption:
tags: [Art generation, Image generation, Midjourney, Text-to-image, English]
---

We have already talked here a few times about text-to-image models. From [ru-dalle](https://robertofont.github.io/IllustratedFairyTales/) and [Disco Diffusion](https://robertofont.github.io/UsingDiffusionToPaintWithStyle/) to [DALL-E 2](https://robertofont.github.io/FirstStepsDalle2/) and [Stable Diffusion](https://robertofont.github.io/GettingStartedStableDiffusion/) (and it looks like several years worth of innovation, but it all happened in just a few months). Despite my love for these models, however, I had yet to test one of the best-performing ones: [Midjourney](https://www.midjourney.com/). Recently the fourth version of Midjourney was released and I had heard great things so I decided to finally take it for a ride.

I will use it to imagine a cats vs. dogs chess game. Let's first see the results and then talk a bit about Midjourney and the creation process for these particular illustrations. Let the game begin!

# 1. The players

## 1.1 Team cats

Led by their serene queen, Snow Leopard III, and Prince Consort Lion XIV, the heart of Cat Empire is Castle Claw, a huge stronghold with fortified walls without any ground-level entrance. Only cats dare to climb to their doors. Tabby soldiers guard its walls and the elite Tiger Riders patrol the surroundings, making it almost unassailable.

### Queen

![Team cats queen]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Cats_queen.png)

### King

![Cat king]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Cats_king.png)

### Bishop

![Cats bishop]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Cats_bishop.png)

### Knight

![cat horse]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Cats_knight.png)

### Castle

![Cats castle]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Cats_castle.png)

### Pawn

![cat pawn]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Cats_pawn.png)

## 1.2 Team dogs

Many think that King Saint Bernard IV and Queen Cocker VII are mere puppets in the hands of Bishop Lupus XXIII, the true ruler of the Dog Kingdom. Whether it is true or not, the fact is that they have passed the last few years preparing to take over Cat Empire. Indeed, they have formed a huge army with well-trained german shepherd infantry, elite wolf rider knights, and giant bulldogs ready to ram through Castle Claw's walls.

### King

![Dogs king]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Dogs_king.png)

### Queen

![Dogs queen]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Dogs_queen.png)

### Bishop

![Dogs bishop]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Dogs_bishop.png)

### Knight

![Dog knight]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Dogs_knight.png)

### Castle

![Dogs castle]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Dogs_castle.png)

### Pawn

![Dog pawn]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Dogs_pawn.png)

# 2. About Midjourney

According to [their website](https://www.midjourney.com/#about), *Midjourney is an independent research lab exploring new mediums of thought and expanding the imaginative powers of the human species* and *a small self-funded team focused on design, human infrastructure, and AI with 11 full-time staff and an incredible set of advisors*.

Their text-to-image model was initially launched in July 2022. To use it, you must join their [Discord channel](https://discord.gg/midjourney), go to one of the *newbie* channels, and enter the command */imagine* followed by your text prompt. Your generation will be queued and start in a few seconds.

This means your generated image can easily get lost amidst a million other users' images which is close to the worst user experience ever. Once you get a paid subscription, you can private-message the bot, and the experience improves quite a bit, but having to use Discord still feels weird. You can access your personal gallery through the Midjourney webpage. I guess it would make sense to be able to generate images from there also.

![Midjourney gallery]({{site.baseurl}}/assets/img/2023-02-12-Cats-vs-DogsWithMidjourney\Gallery.png)
**Midjourney gallery feature is pretty cool**

# 3. Making of

I used the same template prompt for all images:

*Anthropomorphic {character} wearing {accessories} by tiziano, dungeons and dragons, hyperdetailed, cinematic, dramatic lighting, raking light, rim light, symmetric portrait, 8k*

with just small modifications, like removing the *symmetric portrait* part if that was not what I wanted.

The process was surprisingly fast and not much trial and error was needed. Most of the time, I liked one of the first 4 samples. The more challenging illustrations were the knights and the castles. Indeed Tiziano is not the best choice for an artist for these fantasy-like illustrations, but choosing the best artist was not what I was interested in at this time. On the plus side, the portraits, especially the one of the snow leopard queen, got an amazing Tiziano feel to them.

# 4. Foreword

Judging by the above results and how little tinkering around was needed, I would say that Midjourney V4 is by far the best-performing text-to-image model right now. In particular, it excels at generating coherent anatomy and handling multiple characters.

Although one could argue that part of the effort and resources put into text-to-image models would have been better used to solve more fundamental AI problems, the usefulness of these models is now beyond any doubt. For real artists, those that go beyond writing a prompt and hitting enter, open new avenues for experimentation. For the layperson, they are an amazing tool to create personalized illustrations for blog posts, presentations, etc. In my case, for example, I have already used Dall-E a couple of times to create illustrations for presentations at work.

There is, however, a dark side to these models. They have been trained on artwork created by artists that do not receive any compensation, did not provide their consent or were given the ability to opt out, and, in some instances, it seems that this use could be against the license terms of those artworks. Currently, there are two legal actions taking place: [one by a collective of artists against Stability AI, DeviantArt, and Midjourney](https://stablediffusionlitigation.com/) and the other [by Getty Images against Stability AI](https://newsroom.gettyimages.com/en/getty-images/getty-images-statement). We'll need to wait for the dust to settle to see how we can use these technologies in a fair and responsible way.
