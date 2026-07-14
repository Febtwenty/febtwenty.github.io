---
layout: post
title:  "Parenting and Coding"
date:   2026-03-24 15:19:00 +0200
categories: [coding, claudecode]
---
Parenting full time and learn to code on the side? It is a bit harder than I have initially thought. So for the time being I switched tactics to get more hands on experience with vibe coding (essentially coding with claude code). It is stunning to see what is possible with a few prompts and I still learn a lot about the modern work place. It will be quite different. More on that later.

I'd like to introduce to you my new sideproject, ArtSlaw.

### Introducing ArtSlaw
Artslaw is a personal project I built to make contemporary art more accessible — a conversational AI guide that you can bring with you to any exhibition. The idea is simple: paste a link to an exhibition page, and artslaw researches the artist, the works on show, the genre, and related figures, then chats with you about all of it. Think of it as having a knowledgeable friend available on demand, one who has done their homework before you even walk through the gallery door.

Under the hood, artslaw is a full-stack TypeScript application — a React/Vite frontend paired with an Express backend — powered by Anthropic's Claude. What makes it more than a simple chatbot is the agentic loop: the backend can reach out to the web in real time to look up current exhibitions and living artists, so the information it gives you is fresh rather than frozen at a training cutoff. The project is open source and very much a work in progress, but fun!
