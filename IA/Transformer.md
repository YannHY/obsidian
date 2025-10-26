---
tags:
  - documentation
  - ai
  - gpt
author: yann houry
date: 28/11/2023
---
https://ig.ft.com/generative-ai/

![[llm.mp4]]

(la vidéo est aussi disponible en gif animé dans le dossier Images)

Transformers process an entire sequence at once (a sentence, paragraph, an entire article), analysing all its parts and not just individual words.
This allows the software to capture context and patterns better.
It's a technology invented by AI researchers at Google in June 2017.

A key concept of the transformer architecture is self-attention. This is what allows LLMs to understand relationships between words.

![[llm1.png|600]]

Self-attention looks at each token in a body of text and decides which others are most important to understanding its meaning. The transformer computes all the words in a sentence at the same time.

![[llm2.png|600]]

Rather than focusing only on the next word in a sequence, it looks at the probability of larger set of tokens as a whole.

![[llm3.png|600]]
Dans cet article, comparaison intéressante :

> À titre d’illustration, voyez à quel point vous êtes capables de lire une BD des Schtroumpfs et de remplacer chaque « schtroumpf » par un mot issu de l’analyse attentionnelle des autres mots.

[Comment fonctionne ChatGPT ? Décrypter son nom pour comprendre les modèles de langage](https://theconversation.com/comment-fonctionne-chatgpt-decrypter-son-nom-pour-comprendre-les-modeles-de-langage-206788?utm_source=linkedin&utm_medium=bylinelinkedinbutton)
