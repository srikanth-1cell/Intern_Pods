# Personal LLM Wiki (Karpathy-Style Knowledge Compiler)

## Team Members

| Role            | Name   | Responsibility                                      |
| --------------- | ------ | --------------------------------------------------- |
| Senior Intern   | Esha   | AI orchestration, prompts, workflow coordination    |
| Junior Intern 1 | Tejas  | Video ingestion, transcription, extraction pipeline |
| Junior Intern 2 | Siddhu | Wiki UI, Markdown browsing, chat experience         |

---

# Project Overview

This project is about building a lightweight AI-powered knowledge compilation system that converts long-form content such as videos into a continuously improving Markdown wiki. The system should process information during ingestion time and transform raw transcripts into structured concept pages that can evolve over time.

The core idea is that the AI should not simply answer questions directly from raw transcripts. Instead, it should gradually build and improve a persistent knowledge base in Markdown format. As more videos are processed, the wiki should become cleaner, more connected, and more useful.

The final output of the project should primarily be a folder of Markdown files that are human-readable, searchable, and interlinked using wiki-style references.

---

# System Workflow

The system should support a simple end-to-end workflow where a user drops a video into a `/raw` folder and the application automatically processes it.

The workflow should look like this:

```text
/raw/video.mp4
    ↓
Transcript Generation
    ↓
Transcript Processing
    ↓
AI Compilation
    ↓
Markdown Wiki Pages
```

Once transcripts are generated, the AI system should analyze the transcript, identify important concepts, compare them against existing wiki pages, and either create new pages or update existing ones.

Over time, the wiki should behave like a growing knowledge garden where concepts become more refined and better connected.

---

# Video Ingestion and Transcription

Tejas will primarily focus on the ingestion and transcription workflow. The system should monitor a `/raw` folder and automatically detect newly added video files such as `.mp4` or `.mov`.

Once a video is detected, the system should generate a transcript using Whisper or another suitable transcription model. The generated transcript should be stored inside a `/transcripts` folder in Markdown or plain text format.

Where possible, transcripts should preserve timestamps so that later stages of the system can reference exact portions of the source material.

The ingestion pipeline does not need to be production-grade. The priority is to build a workflow that works reliably for experimentation and iteration.

---

# AI Compilation Engine

Esha will primarily focus on the AI compilation workflow, which is the core of this project.

The compilation engine should read transcript content and inspect the existing Markdown wiki before generating output. Instead of blindly creating new pages every time, the AI should decide whether a concept already exists and whether an existing page should be updated.

For example, if one transcript discusses “Photosynthesis” and a later transcript discusses “How Plants Convert Sunlight Into Energy,” the AI should attempt to recognize that these concepts are related and consolidate the information appropriately.

The AI should continuously improve pages by:

* refining summaries
* adding missing details
* creating links between related concepts
* reducing duplication
* maintaining consistent terminology

The overall objective is to simulate how a human might gradually build and refine a personal knowledge base over time.

---

# Markdown Wiki Structure

The wiki itself is the primary output of this project. Every important concept extracted from transcripts should become a Markdown page stored inside the `/wiki` directory.

Each page should remain concise, readable, and focused on a single concept. Pages should include:

* a title
* a short TLDR summary
* a main explanation section
* links to related concepts

Example:

```md
---
title: Photosynthesis
tags:
  - biology
  - plants
---

TLDR:
Photosynthesis is the process plants use to convert sunlight into chemical energy.

# Overview

Photosynthesis allows plants to use sunlight, water, and carbon dioxide to produce glucose and oxygen. This process primarily occurs inside chloroplasts and is essential for sustaining life on Earth.

# Related Concepts

- [[Chloroplasts]]
- [[Cellular Respiration]]
- [[Plant Cells]]
```

The wiki should remain readable even outside the application itself. The Markdown files should be usable independently in tools such as Obsidian or VS Code.

---

# Wiki Linking and Knowledge Connections

The system should support wiki-style linking using the `[[Concept Name]]` format. As the AI generates or updates pages, it should attempt to create useful relationships between concepts.

For example:

```text
[[Photosynthesis]]
[[Chloroplasts]]
[[Plant Cells]]
```

These links should help the knowledge base become increasingly interconnected over time. Siddhu and Esha should collaborate on making sure these wiki links work correctly both in generated Markdown and in the frontend viewer.

---

# Wiki Browser and Frontend Experience

Siddhu will primarily focus on the browsing experience and frontend interface.

The frontend should provide a lightweight interface for exploring the Markdown wiki. At minimum, the interface should support:

* sidebar navigation
* Markdown rendering
* clickable wiki links
* search functionality

The interface should feel similar to a lightweight Obsidian-style knowledge browser.

The frontend does not need complex authentication or backend infrastructure. The focus should remain on simplicity and usability.

Suggested technologies include:

* Next.js
* Tailwind CSS
* Shadcn UI

Optional enhancements may include:

* graph visualization
* backlinks
* dark mode
* concept relationship views

---

# Search and Chat Experience

The application should support a simple search and chat experience over the generated wiki.

Users should be able to search for concepts and browse relevant pages. Siddhu and Esha should also experiment with an AI chat interface where the model answers questions using the generated Markdown wiki as context.

For example, a user might ask:

```text
What do the videos say about photosynthesis?
```

The AI should respond using information synthesized from the wiki pages rather than directly querying raw transcripts.

The chat experience should reference relevant concepts and encourage exploration of the wiki itself.

---

# Folder Structure

The recommended project structure should remain simple and Markdown-centric.

```text
/raw
/transcripts
/wiki
/prompts
/scripts
/app
/components
```

The `/wiki` directory is the most important output of the project.

---

# Development Approach

This project should prioritize experimentation, iteration, and rapid learning. The goal is not to build enterprise software but to explore AI-native workflows and knowledge compilation systems.

The interns are encouraged to heavily use AI coding tools such as:

* Cursor
* Claude
* ChatGPT
* GitHub Copilot

The most important part of the project is learning how to:

* orchestrate AI workflows
* shape prompts
* iteratively improve outputs
* design useful knowledge structures

The project should remain lightweight, practical, and enjoyable to build.

---

# Suggested Timeline

During the first week, the team should focus on project setup, transcription generation, and initial Markdown generation.

During the second week, the focus should shift toward AI-driven concept extraction and wiki page generation.

The third week should focus on improving linking, navigation, and Markdown rendering.

The fourth week should focus on search, chat integration, and improving the overall knowledge compilation workflow.

Additional weeks can be used for experimentation, UI improvements, graph visualization, and refinement of prompts and page quality.

---

# Final Demonstration

At the end of the internship, the team should be able to demonstrate a workflow where:

* a video is dropped into `/raw`
* a transcript is generated automatically
* the AI creates or updates wiki pages
* concepts become linked together
* users can browse and search the wiki
* users can ask questions against the compiled knowledge base

The final system should demonstrate how AI can continuously build and refine a persistent Markdown-based knowledge system over time.

---

# Resources

* Andrej Karpathy — Personal LLM Wiki Concept
  [https://x.com/karpathy/status/2039805659525644595](https://x.com/karpathy/status/2039805659525644595)

* MindStudio Blog — Building a Personal LLM Wiki
  [https://www.mindstudio.ai/blog/andrej-karpathy-llm-wiki-knowledge-base-claude-code#main-content](https://www.mindstudio.ai/blog/andrej-karpathy-llm-wiki-knowledge-base-claude-code#main-content)

* Data Science Dojo — LLM Wiki Tutorial
  [https://datasciencedojo.com/blog/llm-wiki-tutorial/](https://datasciencedojo.com/blog/llm-wiki-tutorial/)

* YouTube — Personal LLM Wiki Walkthrough
  [https://www.youtube.com/watch?v=4SB3T1reCHw](https://www.youtube.com/watch?v=4SB3T1reCHw)

* YouTube — Building AI Knowledge Systems
  [https://www.youtube.com/watch?v=it8v6GNxBDI&t=79s](https://www.youtube.com/watch?v=it8v6GNxBDI&t=79s)

* YouTube — Karpathy-Style Knowledge Compilation Concepts
  [https://www.youtube.com/watch?v=l4EzuMKmeA0](https://www.youtube.com/watch?v=l4EzuMKmeA0)
