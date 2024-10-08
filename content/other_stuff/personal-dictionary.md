---
title: "personal dictionary"
description: "A personal dictionary - maintain your own word list with ease"
date: 2024-07-22
tags: ["link sharing", "local"]
lang: svelte
cover:
  image: personal-dictionary-banner.png
  caption: Banner
  relative: true
accent: "#697cda"
---

This app lets you add your own words, and automatically gets their definitions, synonyms, antonyms and examples from the internet.

## Features
- `Add` words with fuzzy autocompletion from a list of 370k words
- `View` all meanings of a word at glance and select the one to display
- `Search` through your wordlist (does this need to be fuzzy?)
- `Export` your wordlist to a text file or using a link
- `Import` words in bulk from a variety of formats (by default {`,`,`\n`,`\r\n`,` `}-separated, with support for custom separators) or using a link
- Enter `Edit` mode to delete words
- Multiple amazing `themes` in both dark/light modes 
- Cute `backgrounds` 

## Techincal Details
This is made with Svelte + Vite in TypeScript, and uses the svelte-ux library. The `pages` branch is continuously deployed using cloudflare pages, whereas development happens in `main`.

It uses the [Dictionary API](https://dictionaryapi.dev/) to get meanings (which relies on Wiktionary).

The autocompletion wordlist is taken from the [dwyl/english-words](https://github.com/dwyl/english-words/) repo. I have also considered the aspell word lists but they have a lot of repitition (in the sense that almost every word has it's variant with an `'s` right after it, which is pointless for a dictionary).

For fuzzy search, the [EthanRutherford/fast-fuzzy](https://github.com/EthanRutherford/fast-fuzzy/) library is utilized which works quite well.

I use the [mtf be mine](https://misstiina.com/fonts/mtf-be-mine/) font, which is the cutest font ever. It is [free for non-profit use](https://misstiina.com/fonts/tou/), and this is an open source project.

Icons are from [SVGRepo](https://svgrepo.com/). The logo is a heavy edit of an AI-generated logo made from [recraft.ai](https://recraft.ai/).

## Screenshots:

### Themes
{{< focusimage name="Themes" src="https://i.ibb.co/r7nVjyz/image.png" >}}
### Multiple meanings, can choose which to display
{{< focusimage name="Multiple meanings, can choose which to display" src="https://i.ibb.co/HxWmRrt/image.png" >}}
### Light mode and different background
{{< focusimage name="Light mode and different background" src="https://i.ibb.co/S69BBqj/image.png" >}}