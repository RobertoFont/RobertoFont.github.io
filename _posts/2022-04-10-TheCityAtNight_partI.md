---
layout: post
title: The city at night. A Gothic horror tale written, illustrated, and narrated by AI (part I).
date: 2022-04-10
description: We use AI to write, illustrate and narrate a Gothic horror audiobook
img: CityAtNight_4.png
fig-caption: 
tags: [Image generation, Text generation, GPT-3, Diffusion]
---

In a [previous post](https://robertofont.github.io/IllustratedFairyTales/), we used AI to write and illustrate fairy tales. Now, we will go back to that idea to take it a few steps further:

- We will try to push the text-generation capabilities of [GPT-3](https://github.com/openai/gpt-3) to generate a horror tale with a proper plot, with its introduction, climax, and denouement.
- We will try to generate better-quality illustrations by using a different approach.
- We will add a new dimension by synthesizing voice and converting the tale into an audiobook.

Today we will cover the first two points: we will work together with the GPT-3 language model to write a Gothic horror short tale and we will use a [diffusion](https://arxiv.org/abs/2105.05233) model to create illustrations with the appropriate style.

In the second part, we will synthesize voice to transform the tale into an audiobook, synthesize some background music, and create a video with the illustrations, narration, and music.

But that will be in the next post. For now, let's focus on writing and illustrating our Gothic horror tale. First, let's take a look at the result. Then, we can talk a bit about the process and the tools used.

# The city at night

[![The city at night]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/CityAtNight_1.png)]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/CityAtNight_1.png)

No one knows when it started happening, but for as long as anyone could remember, the city had a dark secret. 
At night, when the sun set and the moon rose, something would happen to the city. The lights would dim, the air would grow cold, and a feeling of dread would settle over the city. 
No one knew what caused it, but everyone knew to avoid the city at night. **If you lived there, you followed three simple rules:**

- Stay indoors after dark.

- Don’t go out alone at night.

- Never, ever go into the old city hall.

**Thomas was educated in these three rules since he was a child and he always strictly followed them. And yet, one day, he found himself alone at dusk** in the old city hall. He doesn’t know what led him there, but he knows that he needs to get out before night falls.

[![The old city hall]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/CityHall_1.png)]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/CityHall_1.png)

He’s about to leave when he hears a noise coming from the other side of the hall. It’s a voice, a voice that seems to be coming from the very depths of the building. The voice is chanting something, something in a language that Thomas doesn’t understand. And then he realizes that the voice is coming from the room that he’s been told never to enter.
Thomas knows that he should leave, that he should run away as fast as he can. But something is drawing him towards the room, something that he can’t resist. He walks towards the room, his heart pounding in his chest. He knows that he’s breaking the first rule, that he’s going into the room alone. But he can’t help it. He has to know what’s inside.
As he enters the room, he’s met with a sight that he’ll never forget. There, in the center of the room, is a creature unlike anything he’s ever seen. It’s large, its body writhing and twisting in a way that Thomas can’t understand. And its eyes, its eyes are staring straight at him.
The creature opens its mouth, and the chanting starts again. This time, Thomas can understand the words. 
“I am the city’s darkest secret. I am the thing that you fear. I am the monster that lurks in the shadows. I am the night.”

**Thomas awakened in his room. Was that real? He could not remember what made him stay outside after sunset or how he escaped from the city hall. Did that really happen?** He looked out the window. The sun was setting. **He went outside. The streets were dark and empty.** He walked towards the old city hall. The doors were open. He went inside. The room was dark and empty. There was no creature. Thomas was alone. **He continued going out each night, looking for the truth**, but he never saw the creature again. The streets would be empty, except for the occasional rat running through the garbage. The only sound would be the wind howling through the narrow alleys.

One night, a young woman who had recently moved to the city decided to break the rules. She was going to explore the city at night. 
She had heard the stories, but she didn’t believe them. Surely there was a rational explanation for what happened at night.

[![A woman walking alone at night]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/WomanWalking_1.png)]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/WomanWalking_1.png)

**Thomas saw her and followed her through the empty alleys of the old town.** He wanted to warn her, to tell her to go back before it was too late. But he couldn’t. He knew that she was heading towards the city hall. He could see the fear in her eyes, but she continued walking. She entered the building. Thomas hesitated for a moment, but then he followed her. He had to know if the creature was real. 
As he entered the room, he saw the woman standing in the center of the room, her back to him. The woman turned around, and she saw Thomas. **Thomas spoke, but he did not recognize his own voice. It was like hundreds of people speaking at once:** “I am the city’s darkest secret. I am the thing that you fear. I am the monster that lurks in the shadows. I am the night.”

# Text generation

[![The city at night]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/CityAtNight_2.png)]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/CityAtNight_2.png)
*The city at night*

To write the tale, I followed the same procedure that we used for [The Secret Garden](https://robertofont.github.io/IllustratedFairyTales) (although this time without the *help* from my son).  First, I provided the prompt

*Write a short terror tale in the style of Edgar Allan Poe.
At first sight, the city could look like any other. Visitors even find it beautiful, with its historic buildings and its old stone-paved streets.
The locals knew that the city, at night, belonged to something we could not describe, an evil older than the city itself.*

And then I used [GPT-3](https://github.com/openai/gpt-3) through the [OpenAI API](https://openai.com/api/) to generate 10 alternatives to choose from. I did not include this initial prompt in the tale, since I liked better how the selected continuation started. I think GPT-3 succeeded at providing a good starting point. However, I had to face two difficulties:

1. The constant desire of GPT-3 to finish the tale as soon as possible.

2. A tendency to pulp-style teenagers that go to the graveyard to drink beer and are dismembered by a monster, despite my request for an Edgar Alan Poe approximation.

Both were easily taken care of by adding a bit of text here and there to provide some guidance. The next portion, from *...in the old city hall* to *...I am the night*, was generated by the language model in one go, which is quite remarkable. After that, however, problem 1 became so unsurmountable that I had to pretty much *reset* the narration. Then I cheated just a little bit: the part about the woman that just moved to the city was generated by the language model, but not at that point; it was one of the continuations generated from the initial prompt. You can call the text-generation police on me if you want, but I think it was worth it, considering that it led to what I think is a very nice ending and a reasonably well-rounded tale (at least for a dumb language model and a dumber data scientist).

Overall, I like the result, and it can only get better once we add the appropriate Gothic horror-style illustrations.

# Image generation

[![A woman walking alone at night]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/WomanWalking_2.png)]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/WomanWalking_2.png)
*The young woman, walking through the old town streets at night*

For image generation, I used [this notebook](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb). It's based on the original work by Open AI on guided diffusion (see [paper here](https://arxiv.org/abs/2105.05233) and [GitHub repo here](https://github.com/openai/guided-diffusion)), but it includes models, contributions and tweaks from many different people, so I refer you to the *Credits* section on the notebook for the full details.

Since I plan on delving deeper into this model and image generation in an upcoming post, I won't go into any technical detail now. Let's just say that I absolutely loved the results from the first time I tried it.

The basic idea is to provide a text description of the desired image and use a [CLIP model](https://github.com/openai/CLIP) (or several of them) to guide the image-generation process by aligning the image to the text. What is great about this approach is that it allows controlling not only the content but also the style, from an illustration or painting to an antique engraving. Indeed, I think we absolutely managed to get the Gothic horror look we were looking for.

[![The lost souls]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/LostSouls_1.png)]({{site.baseurl}}/assets/img/2022-04-10-TheCityAtNight_partI/LostSouls_1.png)
*The lost souls*
