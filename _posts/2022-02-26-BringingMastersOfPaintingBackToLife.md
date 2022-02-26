---
layout: post
title: Bringing the masters of painting back to life
date: 2022-02-26
description: We create realistic photographs of the great masters of painting using their own self-portraits as input.
img: Greco.png
fig-caption: 
tags: [GANs, StyleGAN, Time-travel rephotography, Image generation, Art] 
---

In a recent work titled [Time-Travel Rephotography](https://time-travel-rephotography.github.io/){:target="\_blank"}, researchers from the University of Washington, Adobe, and Google Research proposed a method to take an antique photograph and recreate how it would look if it had been taken with a modern camera. Note that this is not a photo restoration procedure; a new image is synthesized using [StyleGAN2](https://github.com/NVlabs/stylegan2){:target="\_blank"} (more on this later).

For many historical figures of the 19th and early 20th century, we only have old, low-quality, and degraded photographs. [Time-Travel Rephotography](https://time-travel-rephotography.github.io/){:target="\_blank"} allows us to get a better sense of what they really looked like.

But, what about **earlier** historical figures? Today, we will try to take a step further and bring back to life some masters of painting using their own self-portraits.

# Durer

[![Durer]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/Durer.png)]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/Durer.png)

**Original painting:** [Albrecht Dürer - 1500 self-portrait](https://commons.wikimedia.org/wiki/File:Albrecht_D%C3%BCrer_-_1500_self-portrait_(High_resolution_and_detail).jpg){:target="\_blank"}

**Date:** 1500

**Location:** Alte Pinakothek, Munich, Germany

Albrecht Dürer, usually known as Durer, was born in Nuremberg, current Germany, in 1471 and died in 1528. He is one of the most prominent figures of the Northern Reinassance. Here, we see an enigmatic Durer, in a full-frontal view, something that, at the time, was usually associated with medieval religious art and, in particular, with images of Christ. 

# El Greco

[![El Greco]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/Greco.png)]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/Greco.png)

**Original painting**: [El Greco - Portrait of a Man](https://commons.wikimedia.org/wiki/File:El_Greco_-_Portrait_of_a_Man_-_WGA10554.jpg){:target="\_blank"}

**Date:** 1595-1600

**Location:** Metropolitan Museum of Art, New York City, USA

Doménikos Theotokópoulos, better known as El Greco (the Spanish for *The Greek*), was born in 1541 in the modern Crete, at the time part of the Republic of Venice. After training in Venice and Rome, he moved to Toledo, in Spain, in 1577 where he lived until his death in 1614. One of the most prominent figures of the Spanish Reinassance, his extremely personal style was not fully appreciated until the 20th century.

# Rembrandt

[![Rembrandt]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/Rembrandt.png)]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/Rembrandt.png)

**Original painting:** [Rembrandt van Rijn - Self-Portrait](https://es.m.wikipedia.org/wiki/Archivo:Rembrandt_van_Rijn_-_Self-Portrait_-_Google_Art_Project.jpg){:target="\_blank"}

**Date:** 1659

**Location:** National Gallery of Art, Washington DC, USA

Rembrandt Harmenszoon van Rijn was born in Leiden, Dutch Republic, in 1606 and died in Amsterdam in 1669. A master of the Dutch Golden Age, he painted nearly 100 self-portraits, like this one, creating almost a movie of his own life.

# Vincent van Gogh

[![Van Gogh]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/VanGogh.png)]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/VanGogh.png)

**Original painting:** [Vincent van Gogh - Self-Portrait](https://commons.wikimedia.org/wiki/File:Vincent_van_Gogh_-_Self-Portrait_-_Google_Art_Project.jpg){:target="\_blank"}

**Date:** 1889

**Location:** Musée d'Orsay, Paris, France

Vincent Willem van Gogh was born in Zundert, Netherlands, in 1853. It wasn't until he moved to France in 1886 that his personal approach to painting began to develop. Most of his works were painted during the last two years of his life, before his death in 1890.

Unappreciated during his life, he is now one of the most famous painters of all time and represents in our collective imagination, better than anyone else, the idea of the misunderstood and tragic genius.

# Frida Kahlo

[![FridaKahlo]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/FridaKahlo.png)]({{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/FridaKahlo.png)

**Original painting**: [Frida Kahlo - Self-Portrait with Thorn Necklace and Hummingbird](https://www.flickr.com/photos/libbyrosof/2267022653){:target="\_blank"} Photo by [libby rosof](https://www.flickr.com/photos/libbyrosof/){:target="\_blank"} on [Flickr](https://www.flickr.com/){:target="\_blank"}. Released under CC BY 2.0 license.

**Date:** 1940

**Location:** The University of Texas at Austin, USA

Magdalena Carmen Frida Kahlo y Calderón was born in 1907 in Coyoacán, Mexico, and died in 1954. Her self-portraits combine auto-biographic, symbolic, and Mexican popular culture elements. Although her work was admired by contemporaries like Picasso or Kandinski, it was relatively unknown to the great public until it was rediscovered in the late 70s. Now, Frida Kahlo has become a true icon.

# How does it work

I will try to provide a high-level overview of the method. You can skip this section if you are not interested in the technical side or if you know, as I do, that it is much better explained at the official [project site](https://time-travel-rephotography.github.io/){:target="\_blank"}, [GitHub repo](https://github.com/Time-Travel-Rephotography/Time-Travel-Rephotography.github.io){:target="\_blank"} and [paper](https://arxiv.org/abs/2012.12261){:target="\_blank"}.

[StyleGAN2](https://github.com/NVlabs/stylegan2){:target="\_blank"} is a generative model that can synthesize a high-resolution face image from a vector in a latent space *w*. Several methods, like [e4e](https://arxiv.org/abs/2102.02766){:target="\_blank"}, allow us to encode an input image into this space. So, one could think that the only thing we need to do is to take the original image, project it to the latent space using the e4e encoder, and then use the StyleGAN decoder to generate our output high-resolution image. This, however, would recover the original artifacts and degradations and generate a black and white image. We need a more elaborate solution:

- Two encoders are combined: the [e4e](https://arxiv.org/abs/2102.02766){:target="\_blank"} encoder, which aims at generating a faithful representation of the original image, and a second encoder, *E*, which is a ResNet18 model trained to predict the projection in the latent space of a color image given a black and white image. The outputs of both encoders are combined to obtain the **latent codes**.

- These latent codes and the StyleGAN generator are used to generate the **sibling image**. The sibling image maintains the general features and appearance of the original subject while showing a different identity. However, it is artifact-free and has fine details.

- When we generate our **output image**, the trick is to use only the coarser latent codes, that provide the identity, and transfer the finer details, like skin tone and texture, from the sibling.

- With all that in place, the main step is to **optimize the latent codes** combining several criteria:
  
  - *Reconstruction loss*: the output image, after passing through a degradation module which is kind of the reverse process of what we want to do, must be as similar as possible to the input image. This is done using features computed using [VGG](https://arxiv.org/abs/1409.1556){:target="\_blank"} and [VGG Face](https://www.robots.ox.ac.uk/~vgg/publications/2015/Parkhi15/){:target="\_blank"} with a special focus on the eye region.
  
  - *Color transfer loss:* the color distribution of the output must be similar to that of the sibling image.
  
  - *Contextual loss:* the VGG features that correspond to high-frequency details must be similar for sibling and output images.

<figure>
    <img src="{{site.baseurl}}/assets/img/2022-02-26-BringingMastersOfPaintingBackToLife/PaperFigure.png"
         alt="Flow diagram of Tme-travel Rephotography">
    <figcaption><em>Flow diagram. Image taken from the original paper. https://arxiv.org/abs/2012.12261</em></figcaption>
</figure>

And that's all. Easy. Or maybe not, considering that, not so long ago, [VGG](https://arxiv.org/abs/1409.1556){:target="\_blank"} was **the** deep learning model, and a few years later we are using it to compute some auxiliary losses...

# Conclusions

The *photographs* were created using the awesome [Colab notebook](https://github.com/Time-Travel-Rephotography/Time-Travel-Rephotography.github.io){:target="\_blank"} provided by the authors. Overall, I think the results are quite good, particularly considering that the tool was designed for photographs, not paintings. I found however some difficulties (some of them already highlighted by the authors in the [original paper](https://arxiv.org/abs/2012.12261){:target="\_blank"}):

- The system struggles with outdated clothing or hairstyles. This is normal since those are not present in the StyleGAN2 training data. El Greco will have to wait for ruffs to become trendy again to get back his clothing.

- The system tends to make people look younger. This is likely for two reasons:
  
  - Older photographic techniques exaggerated wrinkles and creases, and the rephotography process accounts for that. Since this is not our case, the system is probably softening wrinkles that should be there.
  
  - There is a known bias towards younger people in the dataset that was used to train the StyleGAN system.

- Results are much worse for highly stylized paintings, like the case of Van Gogh. But this is something that could be expected. After all, we are using a system designed for photographs. It includes a degradation model for antique photographs. Could it be replaced by a brushstroke model?
