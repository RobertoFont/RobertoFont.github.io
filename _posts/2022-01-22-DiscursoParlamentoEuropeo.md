---
layout: post
title: Mi intervención ante el Parlamento Europeo
date: 2022-01-22
description: We fine-tune a GPT-2 model to address the European Parliament
img: european-parliament.jpg # Add image post (optional)
fig-caption: Photo by Marius Oprea on Unsplash. # Add figcaption (optional)
tags: [GPT-2, Language Models, Spanish, Text generation]
---

La situación es la siguiente: es domingo por la tarde y acabas de recordar que mañana a primera hora debes intervenir ante el Parlamento Europeo. ¿A quién no le ha pasado esto cientos de veces? Vale... a lo mejor no es tan común. Pero es divertido.

Nada hay que temer; la Inteligencia Artificial está ahí para ayudarnos. Usaremos un modelo de lenguaje para que nos ayude a redactar nuestra intervención. Hace ya un tiempo, hice [un ejercicio similar](https://medium.com/biometric-vox/addresing-the-european-parliament-with-recurrent-neural-networks-59a1c59cedfd) empleando char-RNN, una red neuronal recurrente. Me pareció buena idea abrir este nuevo blog actualizando este ejercicio a los nuevos modelos de lenguaje.

En los últimos años, los grandes modelos de lenguaje, como [GPT](https://openai.com/blog/language-unsupervised/), [BERT](https://arxiv.org/abs/1810.04805), [GPT-2](https://openai.com/blog/better-language-models/) o [GPT-3](https://github.com/openai/gpt-3), han supuesto un auténtico cambio de paradigma en el campo del Procesamiento del Lenguaje Natural. Estos modelos de lenguaje son grandes redes neuronales (generalmente basadas en la arquitectura [transformer](https://arxiv.org/abs/1706.03762)) entrenadas sobre un conjunto enorme de textos para adquirir la capacidad de modelar las relaciones entre las diferentes palabras que aparecen en un texto. Una vez entrenado uno de estos modelos masivos, puede ser ajustado -o _fine tuned_- para realizar tareas específicas como, por ejemplo, generar un resumen a partir de un texto más largo. La razón por la que esto ha supuesto un cambio de paradigma es doble:

- Estos modelos de lenguaje exhiben capacidades impensables hace solo unos años, como la habilidad de [GitHub Copilot](https://copilot.github.com/) para generar código fuente o la de GPT-3 para generar texto como el de [este ensayo](https://www.theguardian.com/commentisfree/2020/sep/08/robot-wrote-this-article-gpt-3) publicado por The Guardian.

- Si bien entrenar uno de estos modelos desde cero está al alcance de muy pocos, por la dificultad técnica y el coste asociado, el ajuste fino, para nuestra tarea de interés, requiere pocos recursos. Esto nos permite tomar uno de estos modelos y, a la vez, beneficiarnos de ese pre-entrenamiento masivo, fuera de nuestro alcance, y adaptarlo a nuestras necesidades. Es como si esos gigantes tecnológicos que generaron el modelo original nos hubieran hecho todo el trabajo difícil. Pero mira que son majos.

Eso último es justamente lo que vamos a hacer hoy. Tomaremos el modelo [GPT2-base](https://huggingface.co/PlanTL-GOB-ES/gpt2-base-bne), en español, entrenado por el Barcelona Supercomputing Center (*paper* [aquí](https://arxiv.org/abs/2107.07253)), lo adaptaremos a nuestro objetivo empleando un conjunto de transcripciones de sesiones del Parlamento Europeo, y lo usaremos para escribir nuestra intervención por nosotros.

Los detalles técnicos, y todo el código necesario para reproducir este post, podéis encontrarlos en estos dos *notebooks*:

- [AQUÍ](https://github.com/RobertoFont/Blog/blob/main/notebooks/2022-01-22-PlanTL_GPT2_base_finetune_Europarl.ipynb) podéis ver cómo adaptar el modelo preentrenado con nuestro conjunto de datos.

- [AQUÍ](https://github.com/RobertoFont/Blog/blob/main/notebooks/2022-01-22-EuropeanParliament_DiscourseGeneration.ipynb) tenéis cómo se generó el discurso, paso a paso.

Escribamos.

# Escribiendo nuestra intervención

Como es importante ser agradecido, he decido empezar con un: *"Muchas gracias Señora Presidenta. Con su permiso, me gustaría comenzar dando las gracias..."*. Eso nunca puede ir mal. Sin embargo, no tengo ni la menor idea de a quién podría darle las gracias ni por qué, así que dejaré que sea mi ayudante robot el que continúe de la siguiente manera:

- Le pediremos que genere 5 alternativas para continuar la intervención y elegiremos la que más nos guste.

- Incorporaremos a la intervención esta alternativa, pero podemos elegir si la tomamos completa o una parte.

- Repetiremos el proceso sucesivamente para ir redactando nuestra intervención.

- Si la cosa se tuerce, podremos escribir un pequeño fragmento a mano, pero intentaremos hacerlo lo menos posible: la cosa es que sea nuestro ayudante quien lo haga y, además, yo tengo que descansar, que mañana me espera un día duro en el Parlamento.

Bien, veamos a quién nos sugiere nuestro ayudante que agradezcamos:

- *a todos los presentes por sus aportaciones positivas y constructivas durante la elaboración del informe sobre el Libro Verde de esta directiva que hoy nos ocupa: es un texto extremadamente importante para garantizar una mayor competencia leal con relación al abastecimiento eléctrico en toda Europa; constituye*

- *a sus Señorías por este debate tan importante y estimulante sobre los derechos de la mujer en el mundo moderno: "Todo lo que he aprendido es absolutamente fundamental para nuestro futuro". Creo necesario reconocer aquí algunos principios importantes cuya importancia se refleja principalmente hoy cuando*

- *al señor Marinescu por haber presentado un informe tan rápido y de una importancia capital sobre la iniciativa «Todo menos armas» en el que pedimos a los diputados del Parlamento Europeo (al contrario quizás) -que usted sabe- qué papel desempeñar dentro*

- *al Comisario por todo el trabajo que ha hecho en relación con la propuesta de un reglamento relativo a los servicios aéreos y marítimos para todos sus pasajeros; pero creo firmemente -y le rogaría recalcarlo- también coincido totalmente con usted*

- *a la Sra Doyle por el interesante informe y al Sr Whitehead que ha preparado una exposición tan amplia sobre este tema importante: no solo en relación con lo expuesto hoy aquí sino también haciendo uso del tiempo de palabra necesario para exponer un excelente*

Me gusta la primera. Sería mucha casualidad que la sesión de mañana trate sobre un Libro Verde, pero el abastecimiento energético es un tema demasiado candente para dejarlo escapar. No creo que nadie se dé cuenta de que me desvío del tema y, si alguien se da cuenta, seguro que no dice nada por vergüenza. Así que tomo hasta el ';' y de momento tenemos:

*Muchas gracias Señora Presidenta. Con su permiso, me gustaría comenzar dando las gracias a todos los presentes por sus aportaciones positivas y constructivas durante la elaboración del informe sobre el Libro Verde de esta directiva que hoy nos ocupa: es un texto extremadamente importante para garantizar una mayor competencia leal con relación al abastecimiento eléctrico en toda Europa*

Pido a nuestro asistente que continúe un poco más y me quedo con lo siguiente (en el [notebook](https://github.com/RobertoFont/Blog/blob/main/notebooks/2022-01-22-EuropeanParliament_DiscourseGeneration.ipynb) podéis ver el resto de alternativas):

 *; supone establecer unos límites superiores comunes entre productos distintos -en particular nuevos competidores como Japón- pero también normas mínimas aplicables más allá donde haya escasez geográfica o tecnológica imperante desde hace muchos años ¿Cómo definiría mejor lo bien conocido?*

Me gusta el toque retórico que nos da ese *¿Cómo definiría mejor lo bien conocido?* Empiezo a sentir que este asunto puede darme un buen rédito político, así que añado manualmente la frase: *En el último año, los ciudadanos europeos han experimentado una subida de los precios de la electricidad que resulta insoportable* para marcarle el camino a nuestro asistente, que nos sugiere

*Por eso hay más gente en situación precaria y están menos protegidos frente a las subidas injustas del precio único eléctrico.*

y luego

*La Unión Europea debería elaborar medidas prácticas para garantizar su suministro energético sostenible e impedir mayores costes al consumidor sobre todo mediante un acceso mayor gratuito garantizado tanto por parte nacional como transfronterizo (acceso general o indirecto).*

Empiezo a pensar que esta intervención puede ser el espaldarazo que mi carrera política necesitaba. Mi profesor de marketing decía que siempre hay que incluir una llamada a la acción, así que escribo *Señorías, debemos* y dejo que el político robot complete la frase con *tomar esta decisión política sin diluirla*. Genial; contundente a la vez que vacío.

Es hora de retirarse ahora que vamos ganando. Escribo *Me gustaría concluir mi intervención agradeciendo nuevamente* y me sugiere *sus esfuerzos*. Suficiente. La Inteligencia Artificial no solo me ha sacado de un apuro; me va a hacer subir como la espuma dentro de mi partido.

| ![The White House](https://upload.wikimedia.org/wikipedia/commons/e/e1/White_House_Washington.JPG) |
|:--------------------------------------------------------------------------------------------------:|
| *Mi siguiente destino. Cezary Piwowarczyk, CC BY-SA 4.0, via Wikimedia Commons*                    |

# Resultado final

Así queda finalmente nuestra intervención de mañana (el texto introducido manualmente en cursiva):

*Muchas gracias Señora Presidenta. Con su permiso, me gustaría comenzar dando las gracias* a todos los presentes por sus aportaciones positivas y constructivas durante la elaboración del informe sobre el Libro Verde de esta directiva que hoy nos ocupa: es un texto extremadamente importante para garantizar una mayor competencia leal con relación al abastecimiento eléctrico en toda Europa; supone establecer unos límites superiores comunes entre productos distintos -en particular nuevos competidores como Japón- pero también normas mínimas aplicables más allá donde haya escasez geográfica o tecnológica imperante desde hace muchos años ¿Cómo definiría mejor lo bien conocido?

*En el último año, los ciudadanos europeos han experimentado una subida de los precios de la electricidad que resulta insoportable.* Por eso hay más gente en situación precaria y están menos protegidos frente a las subidas injustas del precio único eléctrico. La Unión Europea debería elaborar medidas prácticas para garantizar su suministro energético sostenible e impedir mayores costes al consumidor sobre todo mediante un acceso mayor gratuito garantizado tanto por parte nacional como transfronterizo (acceso general o indirecto). *Señorías, debemos* tomar esta decisión política sin diluirla. 

*Me gustaría concluir mi intervención agradeciendo nuevamente* sus esfuerzos.

*Muchas gracias.*

# Concluyendo

A la vista tanto del resultado final como de las alternativas que hemos ido generando durante el camino, parece que nuestro modelo genera texto bastante decente, en general, si bien le falta coherencia a largo plazo (aunque esto, estando en el ámbito de la política, casi es el comportamiento esperado). A medida que vamos generando más texto, el resultado se vuelve menos coherente. Hacia la mitad del proceso, tuve que *archivar* lo que se había generado hasta ese momento y empezar de cero con el *prompt* *"En el último año, los ciudadanos europeos han experimentado una subida de los precios de la electricidad que resulta insoportable.*"

A nivel cualitativo, diría que la calidad de los textos es algo peor que con el modelo GPT-2 de OpenAI, en inglés. En cualquier caso, es genial disponer de modelos preentrenados en español y la gente del Barcelona Supercomputing Center ha hecho un gran trabajo.

Me despido recordando que podéis encontrar todo el detalle en los *notebooks*, tanto para el [fine-tuning](https://github.com/RobertoFont/Blog/blob/main/notebooks/2022-01-22-PlanTL_GPT2_base_finetune_Europarl.ipynb) como para la [generación del discurso](https://github.com/RobertoFont/Blog/blob/main/notebooks/2022-01-22-EuropeanParliament_DiscourseGeneration.ipynb).
