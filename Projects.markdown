---
layout: page
title: Projects
permalink: /projects/
---
I'm a process engineer by training. I wrote my first real code in 2022, to automate a report at my own company. In late 2025 I started the [Full Stack Open](https://fullstackopen.com/en/) course to learn web development properly ([post]({% post_url 2025-12-01-Full-Stack %})). In spring 2026, parenting almost full time with only a few hours a week to spare, I switched to building with Claude Code ([post]({% post_url 2026-03-24-Parenting-and-Coding %})).

<div class="glance">
  <p class="glance-lead">Process engineer turned builder. Co-founder of a sustainability consultancy, now shipping AI products with Claude Code.</p>
  <ul class="glance-list">
    <li><strong>2022</strong> <a href="#umweltbuchhaltung">Umweltbuchhaltung</a> · energy report for municipalities, hand-written Python</li>
    <li><strong>2026</strong> <a href="#artslaw">ArtSlaw</a> · live AI exhibition guide with an LLM eval suite, built with Claude Code</li>
    <li><strong>2026</strong> <a href="#cv-pipeline">CV Pipeline</a> · Claude Code skills that turn a job posting into a one-page CV</li>
  </ul>
  <p class="badges">
    {% include badge.html name="Claude Code" icon="claude" %}
    {% include badge.html name="Python" icon="python" %}
    {% include badge.html name="TypeScript" icon="typescript" %}
    {% include badge.html name="React" icon="react" %}
    {% include badge.html name="Express" icon="express" %}
    {% include badge.html name="MongoDB" icon="mongodb" %}
    {% include badge.html name="Anthropic API" icon="anthropic" %}
    {% include badge.html name="Mistral API" icon="mistralai" %}
    {% include badge.html name="LLM evals" %}
    {% include badge.html name="Power BI" icon="powerbi" %}
    {% include badge.html name="LaTeX" icon="latex" %}
    {% include badge.html name="Git" icon="git" %}
  </p>
</div>

These three projects mark the way, oldest first.

<section class="project" id="umweltbuchhaltung">
<p class="project-year">2022</p>
<h2 class="project-title">Umweltbuchhaltung</h2>
<p class="project-links"><a href="https://umweltbuchhaltung.at/">umweltbuchhaltung.at</a> · code is closed, it belongs to Sustainability&amp; GmbH</p>
<div class="project-body">
<a class="project-image" href="https://umweltbuchhaltung.at/"><img src="{{ '/assets/images/20261006_Umweltbuchhaltung.jpg' | relative_url }}" alt="Umweltbuchhaltung.at landing page"></a>
<div class="project-text" markdown="1">
At Sustainability&amp;, the consultancy I co-founded, municipalities kept asking the same questions: what do our buildings consume, what does it cost, and how much CO₂ does it emit? Umweltbuchhaltung is our answer, an automated energy report for municipalities. A handful of Austrian municipalities have used it.

**How it was built.** I wrote all of the code myself, by hand, in Python: reading the municipalities' Excel data, the calculations, and generating the PDF report. The key figures fed a Power BI dashboard, which I embedded in a WordPress site where customers could also download their report. API calls came later, and later still an LLM step that analyses the data and writes passages of the report.

**What I learned.** It took me months. With Claude Code it would take days today, and that gap is what pulled me into building with AI.

<p class="badges">
{% include badge.html name="Python" icon="python" %}
{% include badge.html name="Excel" icon="microsoftexcel" %}
{% include badge.html name="Power BI" icon="powerbi" %}
{% include badge.html name="WordPress" icon="wordpress" %}
{% include badge.html name="OpenAI API" icon="openai" %}
</p>
</div>
</div>
</section>

<section class="project" id="artslaw">
<p class="project-year">2026</p>
<h2 class="project-title">ArtSlaw</h2>
<p class="project-links"><a href="https://www.artslaw.io/">artslaw.io</a> · <a href="https://github.com/Febtwenty/artslaw">GitHub</a></p>
<div class="project-body">
<a class="project-image" href="https://www.artslaw.io/"><img src="{{ '/assets/images/20260416_Frontpage.png' | relative_url }}" alt="ArtSlaw start page"></a>
<div class="project-text" markdown="1">
An AI guide for art exhibitions. Paste the link to a museum or gallery show, and ArtSlaw researches it live and walks you through the artist, the works and what to look for. It's my first live web app.

**How it was built.** With Claude Code, since March 2026, about 140 commits so far. It's a TypeScript app (React and Vite in front, Express behind) with an agentic tool loop: Claude Haiku or Mistral Small, switchable per conversation, call a Tavily web search tool whenever they need facts. Around that: Clerk login, tour history in MongoDB, per-user token caps, discovery of upcoming shows, an AI-drafted blog, and a gamified collection of the exhibitions you've visited.

The part I'm proudest of is the eval suite. An LLM judge checks every factual claim in a tour against the evidence the model actually saw, and code checks tool use, structure, language, latency and cost against a baseline. It turned prompt tweaking from gut feeling into numbers: groundedness went from 79% to 93% for Claude and from 69% to 91% for Mistral.

**What I learned.** Knowing the basics paid off. Full Stack Open is what lets me steer Claude Code: I can read what it writes, give it precise prompts, and notice when it's heading the wrong way.

<p class="badges">
{% include badge.html name="Claude Code" icon="claude" %}
{% include badge.html name="TypeScript" icon="typescript" %}
{% include badge.html name="React" icon="react" %}
{% include badge.html name="Express" icon="express" %}
{% include badge.html name="MongoDB" icon="mongodb" %}
{% include badge.html name="Clerk" icon="clerk" %}
{% include badge.html name="Anthropic API" icon="anthropic" %}
{% include badge.html name="Mistral API" icon="mistralai" %}
{% include badge.html name="Tavily" %}
{% include badge.html name="Render" icon="render" %}
</p>

Read more: [ArtSlaw, my first webapp]({% post_url 2026-04-16-Artslaw-my-first-webapp %}) · [How do I know that ArtSlaw actually tells the truth?]({% post_url 2026-07-21-Eval-system-for-llm-artslaw %})
</div>
</div>
</section>

<section class="project" id="cv-pipeline">
<p class="project-year">2026</p>
<h2 class="project-title">CV Pipeline</h2>
<p class="project-links"><a href="https://github.com/Febtwenty/cv-pipeline">GitHub: cv-pipeline</a></p>
<div class="project-body">
<a class="project-image" href="https://github.com/Febtwenty/cv-pipeline"><img src="{{ '/assets/images/20261006_cv_pipeline_example.jpg' | relative_url }}" alt="Example CV rendered by cv-pipeline"></a>
<div class="project-text" markdown="1">
Two Claude Code skills that turn a job posting into a tailored one-page CV. `/check` is the cheap first pass: does the role fit, and which requirements can't I back up? `/apply` writes the tailored CV as a finished PDF, plus a match report listing everything the posting asks for that I can't honestly claim.

**How it was built.** My whole CV lives in one YAML master. An application never edits it. Instead it writes an overlay with only the fields it changed, and a Python script merges the two into a LaTeX template and compiles the PDF. The model does the judgement work, choosing which bullets fit and how to phrase them. Python enforces the rules that must hold every time: the CV must be exactly one page, and an English CV with a single untranslated field is refused.

cv-pipeline is the public, cleaned-up version of Jobzeugs, the private repo I run my own job search from. That one also has an n8n rebuild of `/check`, a sync to Notion, and a write-up comparing skills with a purpose-built harness.

**What I learned.** Rules written in prose get broken. Everything that only lived in a skill's instructions, like banned punctuation or never moving a skill between tiers, slipped now and then. What's enforced in code held every time.

<p class="badges">
{% include badge.html name="Claude Code" icon="claude" %}
{% include badge.html name="Python" icon="python" %}
{% include badge.html name="YAML" icon="yaml" %}
{% include badge.html name="LaTeX" icon="latex" %}
{% include badge.html name="n8n" icon="n8n" %}
{% include badge.html name="Notion" icon="notion" %}
</p>
</div>
</div>
</section>

## How I work with Claude Code

- **Plan before code.** Bigger changes start in plan mode, or with a grilling session where Claude interviews me until we agree on what to build. This page started that way.
- **A CLAUDE.md in every repo.** It holds the conventions and context Claude needs, so I don't repeat them every session.
- **Skills for anything I do twice.** `/check` and `/apply` above, and a grilling skill for planning.
- **Kanban tickets and small commits.** I work alone, so the board is my project manager, and every change gets one focused commit.
