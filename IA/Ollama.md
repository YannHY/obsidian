---
tags:
  - documentation
  - technology
  - ai
author: yann houry
date: 29-04-2024
Rating: ⭐️⭐️⭐️⭐️⭐️
---

[Ollama](https://ollama.com)

Fait tourner localement [Llama 3](https://ollama.com/library/llama3), [Phi 3](https://ollama.com/library/phi3), [Mistral](https://ollama.com/library/mistral) et [Gemma](https://ollama.com/library/gemma)...


# Utilisation

Sur Mac, il faut ouvrir le Terminal et taper

- `ollama` = connaître toutes les commandes
- `ollama run llama3` = lancer ou télécharger un modèle
- `ollama list` ou `ls` = avoir une liste de tous les modèles téléchargés
- `ollama run llama3.2` ou `ollama pull llama3.2` = mettre à jour les modèles
- `ollama rm llama3.2:latest` = supprimer un modèle
- `bye` = terminer la conversation

On peut faire un prompt sur plusieurs lignes :
- Insérer 3 guillemets `"""` au début et à la fin
- Appuyer sur shift + Entrée pour aller à la ligne

![[ollama-lignes.png]]

Taper `/bye` pour terminer la conversation.
# Mise à jour des modèles

Pour télécharger un modèle, dans le Terminal, taper le modèle désiré. Par exemple : `ollama run llama3:8b` (on peut aussi utiliser `pull` à la place de `run`).

![[téléchargement-llm.png]]

Cliquez sur les tags pour avoir les dernières versions. Par exemple `ollama run mistral:latest`

- Pour avoir une liste de tous les modèles téléchargés : `ollama list` ou `ollama ls`.
- Pour supprimer un modèle : `ollama rm llama2:latest`.

# Tutoriels
Pour connaitre les commandes, taper simplement `ollama`.

Voir vidéo de Korben. Voir en particulier comment créer son propre modèle.

Voir aussi comment utiliser des paramètres.

```
ollama run mistral:latest "Résume ce contenu:" "$(cat ~/Desktop/texte.rtf)"
```

GPT me conseille d'utiliser une variable pour faire la même chose :

```
content=$(cat ~/Desktop/texte.rtf)
ollama run mistral:latest "Résume en français ce contenu: $content"
```


<iframe width="560" height="315" src="https://www.youtube.com/embed/1aXPuFrPtr0?si=049EcyWHe-q4S0Ul" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


<iframe width="560" height="315" src="https://www.youtube.com/embed/90ozfdsQOKo?si=UpjLokNogCyIfAeR" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Installer un modèle

<iframe width="560" height="315" src="https://www.youtube.com/embed/-iJMVIT4PYE?si=u3AQMymOPUs_hbjK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

1. Aller sur Hugging face
2. Taper `GGUF` ou `GGUF 7B` dans la barre de recherche
3. Cliquer sur *See 69146 model results for "GGUF"*
4. Sélectionner un modèle et copier son nom
5. Par exemple, https://huggingface.co/OpenLLM-France/Lucie-7B-Instruct-gguf

Dans le terminal, taper

```
ollama run hf.co/OpenLLM-France/Lucie-7B-Instruct-gguf
```
# Autre

Malheureusement, Mistral ne se montre pas très fort dans les devinettes françaises.
![[réponse-mistral.png]]
# Ollama Vision

[Llama 3.2 Vision · Ollama Blog](https://ollama.com/blog/llama3.2-vision)

- `ollama run llama3.2-vision`
- `ollama run llama3.2-vision:90b`

---

# Utiliser Ollama avec une interface graphique

Avec https://msty.app/ (à comparer avec [Jan]())

- [Msty Docs](https://docs.msty.app/getting-started/onboarding)
- [Msty blog](https://msty.app/blog)
- [Chaîne Youtube](https://www.youtube.com/@mstyapp)

<iframe width="560" height="315" src="https://www.youtube.com/embed/cdAb5CigAgQ?si=ijKNlyRXoOnlKOwI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Installe automatiquement tous les LLM déjà téléchargé avec Ollama

On peut utiliser les API de 
- [Claude](https://console.anthropic.com/settings/keys)
- [OpenAI](https://platform.openai.com/settings/profile?tab=api-keys)
- [Gemini](https://aistudio.google.com/app/apikey)
- Grocq

# Utiliser Ollama dans Obsidian
Voir [plugins Obsidian](https://obsidian.md/plugins?search=ollama)

## Obsidian Copilot

<iframe width="560" height="315" src="https://www.youtube.com/embed/9YYB8a_ehc4?si=5iVQaQ-747Lvb8al" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

1. Télécharger Obsidian copilot
2. Installer le plugin
3. Rentrer éventuellement ses clés API
4. Taper dans le Terminal :

```
OLLAMA_ORIGINS=app://obsidian.md* ollama serve
```

Il faudra probablement quitter Ollama auparavant (menu bar > Quit). Lire

> When I run `ollama serve` I get
> `Error: listen tcp 127.0.0.1:11434: bind: address already in use`
> After checking what's running on the port with `sudo lsof -i :11434`
> 
> I see that ollama is already running
> 
> `ollama 2233 ollama 3u IPv4 37563 0t0 TCP localhost:11434 (LISTEN)`
> 
> I killed the process and ran the serve command again and got the same error. So it seems that it tries to start the server twice.
>
> [Lien](https://github.com/ollama/ollama/issues/707)

Lire aussi
- [3-ways to Set up LLaMA 2 Locally on CPU (Part 2 — Ollama)](https://medium.com/@fradin.antoine17/3-ways-to-set-up-llama-2-locally-on-cpu-part-2-ollama-c9d5d71612c9)

## Ollama dans Obsidian (autre possibilité avec Copilot)

<iframe width="560" height="315" src="https://www.youtube.com/embed/tC9wegnRyZk?si=kbuUjMqn6wdTtB8v" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

1. Installer le modèle voulu dans Ollama
2. Augmenter la fenêtre contextuelle. Taper : `/set parameter num_ctx 128000`
3. Taper `/save` puis `/save deepseek-r1:14b` (ajouter le nom du modèle)
4. Si on tape `/show parameters`, on peut vérifier que la fenêtre est bien à 128000.
5. Lier Ollama à Obsidian : `launchctl setenv OLLAMA_ORIGINS "app://obsidian.md*"`
6. Quitter Ollama (dans la barre de menu)
7. Taper `Ollama serve`
8. Relancer Ollama
9. Dans Obsidian, aller dans *Model*. Cliquer sur *Add custom model*. Installer le modèle (deepseek-r1:14b) et l'embedding model (bge-m3) en cliquant également sur *Add custom model*. Ne pas oublier de cliquer sur *Add Model*.
 
![[Add Model.png|400]]