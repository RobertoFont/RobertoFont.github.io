---
layout: post
title: The city at night. A Gothic horror tale written, illustrated, and narrated by AI (part II).
date: 2022-04-23
description: We use AI to write, illustrate and narrate a Gothic horror audiobook
img: CityAtNight_partII.png
fig-caption: 
tags: [Image generation, Text generation, Music generation Text-to-speech, Speech synthesis]
---

[Some time ago](https://robertofont.github.io/IllustratedFairyTales/), we used AI to write and illustrate fairy tales. This time, we are revisiting the idea to take it a few steps further:

- We will try to push the text-generation capabilities of [GPT-3](https://github.com/openai/gpt-3) to generate a horror tale with a proper plot, with its introduction, climax, and denouement.
- We will try to generate better-quality illustrations by using a different approach.
- We will add a new dimension by synthesizing voice and converting the tale into an audiobook.

In the [first part](https://robertofont.github.io/TheCityAtNight_partI/), we covered the first two points: we worked together with the GPT-3 language model to write a Gothic horror short tale and we used a [diffusion](https://arxiv.org/abs/2105.05233) model to create illustrations with the appropriate style.

In this second part, we will synthesize voice to transform the tale into an audiobook, synthesize some background music, and create a video with the illustrations, narration, and music.

Here is the final result.

# The city at night

{% include youtube.html id='CT6JRAEkLlA' %}

# Speech synthesis

For our narration, I wanted a high-quality speech synthesis (a low-quality robotic voice could spoil it all) and an expressive, nonneutral voice, appropriate for narrating a horror tale.

With that in mind, the first approach I tried was as follows:

- I found a narration I liked on YouTube and got the audio.

- I enhanced the audio/removed the background music using the models provided by the  [SpeechBrain](https://speechbrain.github.io/) project.

- I used that expressive speech sample together with [this technique](https://edresson.github.io/YourTTS/) which is capable of adapting a text-to-speech system to sound like the target voice with around a minute of untranscribed speech.

The result wasn't bad, and I encourage you to try it by yourself using [this Colab notebook](https://colab.research.google.com/drive/1ftI0x16iqKgiQFgTjTDgRpOM1wC1U-yS?usp=sharing) provided by the authors. You can try and *clone* your voice with just a couple of short recordings. However, the quality was just a bit behind what I was looking for and I felt it could end up spoiling the whole thing.

Plan B consisted in using the [Coqui TTS](https://github.com/coqui-ai/TTS) library, in particular, the [VITS](https://arxiv.org/pdf/2106.06103) model pretrained on the [VCTK corpus](https://datashare.ed.ac.uk/handle/10283/2950). This is a multi-speaker model that can generate speech for a total of 109 speakers. The process for this second approach was:

- Open up a casting process to select the voice I liked the most.

- Use the *tts* command-line tool to generate the voice from the text prompts.

- Adjust the speed to make our narrator speak at a slower pace. This was a suggestion of a good friend of mine, Rafa, who watched an early version of the video. (He does video editing for a living, so I **had** to take his suggestion.) The speed can not be adjusted using the *tts* command-line tool, but it can be done by adjusting the *length_scale* parameter in the configuration file.

With this approach, we indeed obtained state-of-the-art TTS quality, and the slower pace also went a long way. The second condition, having expressive, nonneutral speech, was not explicitly addressed, but I think that, by selecting among all the possible voices, the addition of the background music, and the text itself, the final result is very close to our objective.

[Coqui TTS](https://github.com/coqui-ai/TTS) is a deep learning library for text-to-speech research that ships with many pre-trained models. Most state-of-the-art models consist of two modules that are trained separately: one that generates a spectrogram from the text and a second one, called *vocoder*, that generates the audio from the spectrogram. [VITS](https://arxiv.org/pdf/2106.06103) (Conditional Variational Autoencoder with Adversarial Learning for End-to-End Text-to-Speech), on the other hand, is a recently proposed end-to-end model.

I'm thinking it would be cool, for a future post, to try and create a high-quality clone of my own voice by fine-tuning the VITS model.

![The city at dawn]({{site.baseurl}}/assets/img/2022-04-23-TheCityAtNight_partII/CityAtDawn.png)
*The city at dawn*

# Music generation

I know nothing about writing music, and by nothing I mean **N-O-T-H-I-N-G**, so I needed an off-the-shelf tool. Fortunately, there are several no-code tools available for AI-based music generation that offer a free trial. In particular, I considered the following three:

- [Boomy - Make Instant Music with Artificial Intelligence](https://boomy.com/)

- [AI Lyrics, Song, and Music Tool.  AUDOIR, LLC](https://www.audoir.com/)

- [AIVA - The AI composing emotional soundtrack music](https://aiva.ai/)

Among these, I preferred the last one, since it allowed for better customization to get closer to what I had in mind for our soundtrack. Note, however, that I know **N-O-T-H-I-N-G** about music writing, so it doesn't mean that it is the best tool of the three, just that I happened to take a better grasp of it. It's absolutely possible that the other two are as good or even better.

The video includes two different songs. For both of them, I selected the *20th century cinematic* category and slow pacing, but they differ in the instrumentation: *piano solo* in one case and *symphonic orchestra* in the other. Then the tool would assign something called *key*, something called *BPM*, and something called *meter*. I don't have the slightest idea what those are. Remember when I said I know nothing and all that? Wasn't kidding.

In any case, I generated a few songs of each type and selected the ones I thought were less *intrusive* as background music. I think we managed to get a nice effect.  It is worth noting that, although we selected the pacing and the orchestration, there was no way to let the system know that we were looking for something creepy. It's either an effect of all the different pieces put together or that classical music is by itself creepy. I'm more inclined towards the latter, but remember that I know **N-**... well... you know how it goes.

# Putting it all together

I created the video using [Canva](https://www.canva.com/). There is really not much to say: I imported the narration, selected a few images for each setting within the tale, tried to synchronize them with the narration, and added the background music. As I said, I used two different songs: the piano solo as the main theme, and the symphonic orchestra composition as *the monster song*.

All in all, I'm pretty happy with the result and had a lot of fun creating and putting together all the different pieces. Hope you like it also!
