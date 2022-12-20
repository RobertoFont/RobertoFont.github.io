---
layout: post
title: Mi hijo charla con un pirata gracias a la IA
date: 2022-12-20
description: Lo mismo puede conseguirse con un parche y una barba postiza, pero ¿dónde está la diversión en eso?
img: Conversational.png
fig-caption: 
tags: [GPT-3, Whisper, Chatbot, Spanish]
---

Llega la Navidad, todos los niños se apresuran a escribir su carta a los Reyes Magos. ¿Todos? ¡No! Hay un niño llamado Tomás que confía más en los recientes avances de la Inteligencia Artificial y la increíble habilidad de su padre.

Bueno... a lo mejor esto no es exactamente así... pero, coges la idea, ¿no?

Ya en [posts anteriores](https://robertofont.github.io/IllustratedFairyTales/) he usado modelos de lenguaje como GPT-3 para jugar con mi hijo, escribiendo cuentos a medias con la IA. Esta vez, sin embargo, me apetecía hacer algo más interactivo y que pudiera tener una verdadera conversación. Mi hijo no se maneja con el teclado como para que un chatbot hubiera servido, así que la interfaz tenía necesariamente que ser la voz. Afortunadamente, la evolución que ha vivido la IA en los últimos años, hace posible lo que hace muy poco hubiera parecido ciencia ficción. Y mira que esto no es (solo) una frase grandilocuente: he trabajado mucho tiempo en reconocimiento de voz y, créeme, hace no tanto, intentar transcribir la voz de un niño, en español, y sin saber de antemano la temática, hubiera resultado en desastre.

# En qué consiste el invento

El invento en cuestión corre en un notebook de Colab que puedes clonar y ejecutar tú mismo (para GPT-3 necesitarás una cuenta en OpenAI e introducir tu API key):

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/RobertoFont/Blog/blob/main/notebooks/2022-12-18-ConversationalGame.ipynb)

El sistema consta de varias piezas, como puedes ver en la figura:

![Diagrama del invento]({{site.baseurl}}/assets/img/2022-12-20-MiHijoHablaConUnPirataIA/Diagrama.png)

- Una sencilla [app de Gradio](https://gradio.app/) nos permite tener un botón para grabar y otro para reproducir la respuesta. (Lo ideal hubiera sido poder hablar libremente, tipo Alexa, pero eso requeriría funcionalidades extra como detección de habla y de fin de habla, posibilidad de *barge-in*... Lo dejamos para otra Navidad).

- Utilizamos [Whisper](https://openai.com/blog/whisper/), de OpenAI, para transcribir la grabación de voz a texto.

- Esta transcripción, junto con los turnos de conversación anteriores y el contexto del personaje, se envía a GPT-3 a través de la [API](https://openai.com/api/) para que genere la respuesta.

- La respuesta generada por el modelo de lenguaje se convierte a voz utilizando [Coqui TTS](https://github.com/coqui-ai/TTS) y una de sus modelos en español. (Tener una voz que se adaptara a las características de cada personaje sería desde luego otra mejora interesante).

# Luces y acción

Aquí puedes ver el resultado. Diría que funciona bastante bien y mi hijo pasa un buen rato (y los demás con él):

{% include youtube.html id='Pxt6FLoMFBo' %}

**NOTA:** El audio del video está **editado** para eliminar las esperas entre que se le pide una respuesta al sistema y ésta está disponible. Estas pausas no son tan largas como para impedir *conversar* con el sistema, pero hubieran hecho el video muy lento.

# Despedida y cierre

Eso es todo. Las ilustraciones del video están hechas con [DALL-E 2](https://robertofont.github.io/FirstStepsDalle2/) -otra opción más que válida habría sido [Stable Diffusion](https://robertofont.github.io/GettingStartedStableDiffusion/), pero, en este caso, la inmediatez de DALL-E sin necesidad de demasiado *prompt engineering*, fue clave para terminar en un tiempo razonable.

Antes de terminar, un comentario sobre el idioma: como habréis visto, el contexto del personaje está en inglés, pero la conversación se mantiene en español. A pesar de que GPT-3 no es un modelo multi-idioma como tal, funciona bastante bien. Al inicio, llegué a implementar la interacción con GPT-3 en inglés: se utilizaba la capacidad de Whisper de convertir directamente audio en español en texto en inglés, se generaba la respuesta en inglés, y luego se traducía antes de generar la voz. Esto, que era rizar el rizo, al final lo abandoné, pero el simple hecho de que fuera factible da testimonio otra vez del punto en el que estamos...

Vale, ya no me flipo más, solo agradecer a Rafa García Amicis y Diego Redondo por las sugerencias para mejorar el video. Hacerlo fue una experiencia increíble :wink:
