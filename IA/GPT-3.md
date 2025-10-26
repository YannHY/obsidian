---
tags:
  - documentation
  - ia
  - gpt-3
author: yann houry
date: 30-12-2022
---

<img src=“https://github.com/YannHY/obsidian/blob/main/IA/Images/ai.jpg“ width=400 />

> [!example]+ Plan
> - [[#Definition|Definition]]
>	- [[#Definition#Generative Pre-trained Transformer|Generative Pre-trained Transformer]]
> - [[#Neural Network|Neural Network]]
>	- [[#Neural Network#Language Models|Language Models]]
>	- [[#Neural Network#La probabilité conditionnelle des mots|La probabilité conditionnelle des mots]]
> - [[#Parameters|Parameters]]
>	- [[#Parameters#Improve your prompt by adding an example|Improve your prompt by adding an example]]
>	- [[#Parameters#Add some examples|Add some examples]]
>	- [[#Parameters#Adjust your settings|Adjust your settings]]
>		- [[#Adjust your settings#Temperature|Temperature]]
>		- [[#Adjust your settings#Tokens|Tokens]]
> - [[#Ajout du 08-10-2023]]
> - [[#Ressources]]
> 	- [[#GPT 3 & Google Sheets|GPT 3 & Google Sheets]]
> 	- [[#GPT 3 & SIRI|GPT 3 & SIRI]]
> 	- [[#GPT-3 & WhatsApp|GPT-3 & WhatsApp]]
> 	- [[#GPT & VS Code|GPT & VS Code]]
> 	- [[#GPT on Mac OS]]
> 	- [[#À essayer|À essayer]]

# Definition
## Generative Pre-trained Transformer
> _Generative Pre-trained Transformer 3_ (**GPT-3**) is a language model that leverages deep learning to generate human-like text (output). Not only can it produce text, but it can also generate code, stories, poems, etc ([OpenAI GPT-3: Everything You Need to Know](https://www.springboard.com/blog/data-science/machine-learning-gpt-3-open-ai/))

## Neural Network
> GPT-3 is a neural network ML model that can generate any type of text from internet data. It was created by OpenAI, and it only needs a tiny quantity of text as an input to produce huge amounts of accurate and complex machine-generated text. ([What are GPT-3 Parameters?](https://www.analyticsinsight.net/what-are-gpt-3-parameters/))

## Language Models
> [...] language models are statistical tools to predict the next word(s) in a sequence. In other words, language models are probability distribution over a sequence of words. ([OpenAI GPT-3: Everything You Need to Know](https://www.springboard.com/blog/data-science/machine-learning-gpt-3-open-ai/))

### La probabilité conditionnelle des mots
> Le nom GPT-3 est un acronyme qui signifie "generative pre-training (préformation générative)". Et nous en sommes à la troisième version. Il est génératif car, contrairement aux autres réseaux de neurones qui répondent oui ou non, GPT-3 peut générer de longues séquences du texte original. Il est préformé en ce sens qu'il n'a pas été construit avec une connaissance de domaine, même s'il peut accomplir des tâches spécifiques à un domaine, comme la traduction en langue étrangère.
> Un modèle linguistique, dans le cas de GPT-3, est un programme qui calcule la probabilité qu'un mot apparaisse dans un texte par rapport aux autres mots du texte. C'est ce que l'on appelle ==la probabilité conditionnelle des mots==.
> Par exemple, dans la phrase, Je voulais faire une omelette, alors *je suis allé au frigo et j'en ai sorti des ...*, le blanc peut être rempli avec n'importe quel mot, même du charabia, étant donné l'infinie composabilité du langage. Mais le mot "œufs" a probablement un score assez élevé pour remplir ce vide dans la plupart des textes normaux, plus élevé que, disons, "éléphants". La probabilité de présence d'œufs dans le texte est donc plus élevée que la probabilité de présence d'éléphants. ([Qu'est-ce que GPT-3 ? Tout ce que votre entreprise doit savoir sur le programme de langage d'IA d'OpenAI](https://www.zdnet.fr/pratique/qu-est-ce-que-gpt-3-tout-ce-que-votre-entreprise-doit-savoir-sur-le-programme-de-langage-d-ia-d-openai-39908563.htm))

5 jours pour atteindre le million d'utilisateurs.

![[utilisateurs.png | 500]]

## Parameters
Previous Language Models had way less parameters.

![[trainable-parameters.jpg]]

GPT-3 [compared](https://twitter.com/LinusEkenstam/status/1607102506336911360?s=20) to its successor. The former has 175 billion parameters, the latter will have 100 trillion parameters (As it turned out, this was not the case).

![[gpt-3-4.png]]

> In general, the more parameters a model has, the more data is required to train the model. As per the creators, the OpenAI GPT-3 model has been trained about 45 TB text data from multiple sources which include Wikipedia and books. ([OpenAI GPT-3: Everything You Need to Know](https://www.springboard.com/blog/data-science/machine-learning-gpt-3-open-ai/))

- [CommonCrawl](https://commoncrawl.github.io/cc-crawl-statistics/plots/languages.html) (en gros, internet) est composé à 45% de textes anglais. La langue française représente 4,7% de l'ensemble.
- Wikipedia represents ==only 3%== of the data (corpus) used to train GPT-3.

![[dataset.png]]

https://beta.openai.com/docs/quickstart

### Improve your prompt by adding an example
`Suggest one name for a *black* horse` instead of `Suggest one name for a horse`.

### Add some examples

```
Suggest three names for an animal that is a superhero.

Animal: Cat
Names: Captain Sharpclaw, Agent Fluffball, The Incredible Feline
Animal: Dog
Names: Ruff the Protector, Wonder Canine, Sir Barks-a-Lot
Animal: Horse
Names:
```

Voir aussi https://youtu.be/bB7xkRsEq-g ➝ *Prompt engineering*
- poser une question ("On average, joe asks 35 questions to ChatGPT per hour. How many questions does he answer in a standard work day?")
- poser la même question en demandant la formule mathématique ("On average, joe asks 35 questions to ChatGPT per hour. How many questions does he answer in a standard work day? Show answer as a math formula as a code snippet.")
- poser la même question en utilisant JavaScript ("On average, joe asks 35 questions to ChaGPT per hour. How many questions does he answer in a standard work day? Show answer as a math formula as a code snippet using JavaScript.")

### Adjust your settings
#### Temperature
If you submit the same prompt multiple times, the model would always return identical or very similar completions. ==This is because your temperature was set to 0==.
When temperature is above 0, submitting the same prompt results in different completions each time.

Remember that the model predicts which text is most likely to follow the text preceding it. ==Temperature is a value between 0 and 1 that essentially lets you control how confident the model should be when making these predictions==. Lowering temperature means it will take fewer risks, and completions will be more accurate and deterministic. Increasing temperature will result in more diverse completions.

As stated below, ==it’s usually best to set a low temperature for tasks where the desired output is well-defined. Higher temperature may be useful for tasks where variety or creativity are desired==, or if you'd like to generate a few variations for your end users or human experts to choose from.

#### Tokens
You can think of tokens as pieces of words used for natural language processing. ==For English text, 1 token is approximately 4 characters or 0.75 words==. As a point of reference, the collected works of Shakespeare are about 900,000 words or 1.2M tokens. ([FAQ](https://openai.com/api/pricing/#faq-token))

➝ [Tokenizer](https://beta.openai.com/tokenizer) (tool to understand how a piece of text would be tokenized by the API, and the total count of tokens in that piece of text.)

See also:
https://beta.openai.com/docs/quickstart

![[3. Documentation/IA/Images/tokens.png]]

Sur les différences entre la langue française et anglaise en termes de token, de quantité et de coût, lire [ce post LinkedIn](https://www.linkedin.com/posts/mazancourt_llm-ia-activity-7140837365710761984-kK4l?utm_source=share&utm_medium=member_desktop).

> [!info]+
> Pour comprendre la notion de token et d'embedding, voir [Maîtriser l'art du prompt pour être créatif et productif avec chatgpt](https://youtu.be/aKEr_cuvUbo?si=2C-mLN6UrCtJ7hYK&t=630) (à partir de 10:30) (démonstration ci-dessous inspirée de [Comment les I.A. font-elles pour comprendre notre langue ?](https://youtu.be/CsQNF9s78Nc?si=HjzI0T6mQgZR4uS2)).
> 1. L'IA transforme votre texte (votre prompt) en nombres = Tokenisation (découpage des mots en nombres)
> 2. Position de mots (de concepts) dans un espace à plusieurs dimensions afin de déterminer le sens que ces mots ont les uns par rapport aux autres = mathématiser le sens (➝ algorithme Word2Vec ou GloVe) = embedding (représentatin géométrisé du sens)
> 
> ![[tokenisation.png]]
> 
>On peut se reporter aussi à [Comment fonctionne chatGPT de la requête à la réponse](https://miro.com/app/board/uXjVMAp7-zg=/)
>
![[Comment fonctionne ChatGPT.png]]

Utiliser également le site [Tiktokenizer](https://tiktokenizer.vercel.app/) pour expliquer la notion de tokens (vue dans cette [très intéressante vidéo](https://youtu.be/7xTGNNLPyMI?si=o1byOuwYzEztULbQ)). Ajoute la notion de conversation encadrée par

```
<|im_start|>...<|im_end|>
```

Signalant le début et la fin d'une prise de parole (soit par l'utilisateur, soit par l'assistant).

```cardlink
url: https://tiktokenizer.vercel.app/
title: "Tiktokenizer"
host: tiktokenizer.vercel.app
favicon: https://tiktokenizer.vercel.app/favicon.ico
```

![[Tiktokenizer.png]]
# Ajout du 08-10-2023
[Generative AI and the transformer](https://ig.ft.com/generative-ai/)

The LLM is underpinned by a scientific development known as ==the transformer model==, made by Google researchers in 2017.

➝ [[Transformer]]

![[llm1.png|600]]

[A jargon-free explanation of how AI large language models work](https://arstechnica.com/science/2023/07/a-jargon-free-explanation-of-how-ai-large-language-models-work/)

## Ressources

> [!info]+
> Trouver de nombreux articles, podcasts ou vidéos sur [[Octobre 2022 à Mars 2023]]

### GPT 3 & Google Sheets
- [=GPT3() Demo Template](https://docs.google.com/spreadsheets/d/17y_oAaDq2ycCh_1LomxrK2_1QgATckZAKC_bAv002xc/edit#gid=0) (vu sur Twitter)
- [=GPT3() Demo Template : Sheet1](https://docs.google.com/spreadsheets/u/1/d/1csVtmpf_nXEtwUoR8ZkxhkIGxdlCAJMVfSsOUUxbI-Q/htmlview)
- Voir aussi [mon adaptation de ce fichier](https://docs.google.com/spreadsheets/d/1GYwiJxOHLtQOzDaiPaJwTX46lCV2F3QhwnQfLGrAO2w/edit#gid=1998526213) pour produire des bulletins ou [GPT3-Exercice](https://docs.google.com/spreadsheets/d/1cTCXhY8TeaUEkQgxoq8RmVhXT0K5r0igHov9Fb6UAao/edit#gid=783039671)
- [excelformulabot](https://excelformulabot.com) (fonctionne avec Google Sheets aussi)

### GPT 3 & SIRI/Shortcut
- [Comment utiliser ChatGPT sur votre iPhone avec un seul raccourci iOS](https://www.numerama.com/tech/1201292-comment-utiliser-chatgpt-sur-votre-iphone-avec-un-seul-raccourci-ios.html)
- [Le Raccourci SiriGPT sur iCloud](https://www.icloud.com/shortcuts/18cd4aad0abe4b4ebcc03ef3b4d0dc40)
- [Siri GPT-3 combo aims to create a truly smart voice assistant](https://9to5mac.com/2023/01/19/siri-gpt-3/)
- [ChatGPT in an iOS Shortcut — Worlds Smartest HomeKit Voice Assistant](https://matemarschalko.medium.com/chatgpt-in-an-ios-shortcut-worlds-smartest-homekit-voice-assistant-9a33b780007a) (➝ [Shortcut link]([https://www.icloud.com/shortcuts/e5d4033cf8024b5796e270c8fed9e478](https://www.icloud.com/shortcuts/e5d4033cf8024b5796e270c8fed9e478)))
- [I've replaced Siri with the ChatGPT AI on my iPhone thanks to this simple shortcut](https://www.imore.com/iphone/ive-replaced-siri-with-chatgpt-ai-on-my-iphone-thanks-to-this-simple-shortcut)
- [Introducing S-GPT, A Shortcut to Connect OpenAI’s ChatGPT with Native Features of Apple’s Operating Systems](https://www.macstories.net/ios/introducing-s-gpt-a-shortcut-to-connect-openais-chatgpt-with-native-features-of-apples-operating-systems/)

### GPT-3 & WhatsApp
- [Mentionned on Twitter](https://twitter.com/danielgross/status/1598735800497119232?s=20)
- [whatsapp-gpt (Github)](https://github.com/danielgross/whatsapp-gpt)
- [Send GPT with WhatsApp](https://chrome.google.com/webstore/detail/send-gpt-with-whatsapp/mgkahgmfkhcgadggaaobdbbmabbhhibk)
- [God in a box](https://godinabox.co/)
- [Comment utiliser ChatGPT sur WhatsApp ?](https://www.presse-citron.net/comment-utiliser-chatgpt-sur-whatsapp/) (-> [Shmooz.ai](https://shmooz.ai/), [WizAI](https://www.getwiz.xyz/))

### GPT & VS Code
- [GPT3 extension for VSCode](https://marketplace.visualstudio.com/items?itemName=timkmecl.codegpt3) (marketplace VS Code)
- [CodeGPT](https://marketplace.visualstudio.com/items?itemName=DanielSanMedium.dscodegpt&ssr=false) (marketplace VS Code)
- [CodeGPT: The VSCode Extension with ChatGPT-Like Functionalities](https://medium.com/geekculture/codegpt-the-vscode-extension-with-chatgpt-like-functionalities-783323a916c3)

### GPT on Mac OS
- [MacGPT](https://goodsnooze.gumroad.com/l/menugpt) (voir aussi [MacWhisper](https://goodsnooze.gumroad.com/l/macwhisper?layout=profile) et [les autres apps du développeur](https://goodsnooze.gumroad.com/))
- Voir également [Poe](https://apps.apple.com/app/id1640745955?platform=iphone)
- [GPT présent n'importe où dans macOS avec cette intégration astucieuse](https://www.macg.co/logiciels/2023/03/gpt-present-nimporte-ou-dans-macos-avec-cette-integration-astucieuse-135147) (voir en particulier [Blog Series: #1 ChatGPT + BetterTouchTool = ❤️](https://folivora.ai/blog/post/13300))
- https://apps.apple.com/us/app/whisper-transcription/id1668083311?mt=12

## GPT & Chrome
- Merlin
- [Comment créer une extension Chrome avec ChatGPT, le guide complet](https://pandia.pro/guide/comment-creer-une-extension-chrome-avec-chatgpt-le-guide-complet/)

### À essayer
- [x] [GPT-2 Output Detector Demo](https://huggingface.co/openai-detector/)
- [ ] [ChatGPT for Google](https://github.com/wong2/chat-gpt-google-extension)

>![](https://twitter.com/joekndy/status/1598874918422450176?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1598874918422450176%7Ctwgr%5E735c44d2d87c88406a511f5d0705cd9da0f972ea%7Ctwcon%5Es1_c10&ref_url=https%3A%2F%2Ftwitframe.com%2Fshow%3Furl%3Dhttps%3A%2F%2Ftwitter.com%2Fjoekndy%2Fstatus%2F1598874918422450176%3Fs%3D20t%3DILQci1ItQDwKEXuEX5_OOg)