# Product Requirements Document (PRD)

# Personal LLM Wiki (Karpathy-Style Knowledge Compiler)


# Resources

- Andrej Karpathy — Personal LLM Wiki Concept  
  https://x.com/karpathy/status/2039805659525644595

- MindStudio Blog — Building a Personal LLM Wiki  
  https://www.mindstudio.ai/blog/andrej-karpathy-llm-wiki-knowledge-base-claude-code#main-content

- Data Science Dojo — LLM Wiki Tutorial  
  https://datasciencedojo.com/blog/llm-wiki-tutorial/

- YouTube — Personal LLM Wiki Walkthrough  
  https://www.youtube.com/watch?v=4SB3T1reCHw

- YouTube — Building AI Knowledge Systems  
  https://www.youtube.com/watch?v=it8v6GNxBDI&t=79s

- YouTube — Karpathy-Style Knowledge Compilation Concepts  
  https://www.youtube.com/watch?v=l4EzuMKmeA0



## Team Members

| Role            | Name   | Responsibility                                      |
| --------------- | ------ | --------------------------------------------------- |
| Senior Intern   | Esha   | AI orchestration, prompts, workflow coordination    |
| Junior Intern 1 | Tejas  | Video ingestion, transcription, extraction pipeline |
| Junior Intern 2 | Siddhu | Wiki UI, Markdown browsing, chat experience         |

---

# 1. Project Overview

The goal of this project is to build a lightweight AI-powered knowledge compilation system that converts long-form content (primarily videos) into a continuously improving Markdown wiki.

The system should process knowledge during ingestion time instead of relying entirely on query-time retrieval.

The final output should be:

* human-readable
* Markdown-native
* searchable
* interlinked

The project is intentionally designed as:

* an AI experimentation project
* a workflow orchestration project
* a hands-on learning experience

This is not intended to be an enterprise SaaS application.

---

# 2. Project Objective

Build a system where:

```text id="vk0ucw"
Video → Transcript → AI Compilation → Markdown Wiki
```

The AI system should:

* extract important concepts
* generate concept pages
* update existing pages
* connect related ideas
* improve summaries over time

The wiki should behave like a growing knowledge base.

---

# 3. Core Product Philosophy

## Key Idea

Instead of:

* repeatedly searching raw documents with RAG

We:

* compile knowledge once
* store structured Markdown pages
* continuously refine the knowledge base

The Markdown wiki itself is the main product.

The application/UI is only a way to browse and interact with it.

---

# 4. Goals

## Primary Goals

* Automatically transcribe uploaded videos
* Generate structured Markdown concept pages
* Create links between related concepts
* Update knowledge incrementally
* Allow users to browse and search the wiki
* Enable AI chat over compiled knowledge

---

## Secondary Goals

* Experiment with prompt engineering
* Learn AI orchestration workflows
* Explore knowledge compilation concepts
* Learn modern AI developer tooling

---

# 5. Non-Goals

The following are intentionally out of scope:

* Enterprise authentication systems
* Production-grade scalability
* Complex backend infrastructure
* Heavy DevOps workflows
* Large database systems

This project should remain lightweight and experimentation-focused.

---

# 6. High-Level Workflow

## End-to-End Pipeline

```text id="iggrjd"
/raw/video.mp4
    ↓
Transcription
    ↓
Transcript Processing
    ↓
AI Compilation
    ↓
Markdown Wiki Pages
    ↓
Search / Chat / Browsing
```

---

# 7. Functional Requirements

# 7.1 Video Ingestion

## Owner: Tejas

### Requirements

The system should:

* monitor a `/raw` folder
* detect newly added video files
* process videos automatically

---

### Supported Inputs

Initially support:

* `.mp4`
* `.mov`

Optional later support:

* YouTube URLs
* audio-only files
* PDFs

---

### Output

Generated transcript files should be stored in:

```text id="8oh0wo"
/transcripts
```

---

# 7.2 Transcription Pipeline

## Owner: Tejas

### Requirements

The system should:

* generate transcripts from uploaded videos
* support long-form videos
* preserve timestamps if possible

---

### Recommended Tools

Suggested options:

* Whisper API
* local Whisper models

---

### Output Format

Example:

```md id="khy4b3"
# Video Transcript

Source: ai-talk.mp4

[00:01:20]
Embeddings are vector representations...
```

---

# 7.3 AI Compilation Engine

## Owner: Esha

### Overview

This is the core feature of the project.

The AI compilation engine should:

1. Read transcript content
2. Inspect existing wiki pages
3. Decide whether to:

   * create a new page
   * update an existing page
   * merge related concepts
4. Write Markdown output

---

### Example Workflow

Transcript says:

```text id="8rtnr0"
RAG systems use embeddings for semantic retrieval.
```

The AI may:

* update `rag.md`
* update `embeddings.md`
* add wiki links

---

### Requirements

The system should:

* avoid duplicate pages
* maintain consistent terminology
* create concise summaries
* connect related concepts

---

# 7.4 Markdown Wiki Generation

## Owner: Esha

### Requirements

Each concept should become a Markdown page.

---

### Example Structure

```md id="r5y4ea"
---
title: Embeddings
tags:
  - ai
  - rag
---

TLDR:
Embeddings convert information into semantic vectors.

# Overview

# Related Concepts

- [[Vector Databases]]
- [[Semantic Search]]
```

---

### Standards

Every page should include:

* title
* short TLDR
* main explanation
* related concept links

---

# 7.5 Wiki Linking

## Owners: Esha + Siddhu

### Requirements

The system should:

* support `[[wiki-links]]`
* connect related concepts automatically
* generate backlinks where possible

---

### Example

```text id="3yotk3"
[[Embeddings]]
[[RAG]]
[[Semantic Search]]
```

---

# 7.6 Wiki Browser UI

## Owner: Siddhu

### Requirements

Build a lightweight UI that supports:

* sidebar navigation
* Markdown rendering
* page browsing
* search

---

### Suggested Stack

* Next.js
* Shadcn UI
* Tailwind

---

# 7.7 Search

## Owners: Siddhu + Esha

### Requirements

Users should be able to:

* search concept names
* search page contents

Optional:

* semantic/vector search

---

# 7.8 AI Chat Interface

## Owner: Siddhu

### Requirements

Users should be able to:

* ask questions about the wiki
* receive AI-generated answers
* see referenced concept pages

---

### Example

Question:

```text id="nchz1u"
What do the videos say about RAG?
```

Response should reference:

* relevant wiki pages
* related concepts

---

# 8. Technical Requirements

# Recommended Stack

| Area          | Suggested Technology |
| ------------- | -------------------- |
| Frontend      | Next.js              |
| Styling       | Tailwind             |
| UI Components | Shadcn UI            |
| AI SDK        | Vercel AI SDK        |
| Transcription | Whisper              |
| Storage       | Markdown files       |
| AI Provider   | OpenAI API           |

---

# 9. Folder Structure

## Recommended Structure

```text id="9nlf4v"
/raw
/transcripts
/wiki
/prompts
/scripts
/app
/components
```

---

# 10. Team Responsibilities

# Esha

## AI Workflow + Coordination

Responsibilities:

* overall architecture
* AI orchestration
* prompt engineering
* page update logic
* concept merging
* integration support

---

# Tejas

## Ingestion + Transcription

Responsibilities:

* video ingestion
* transcription pipeline
* transcript cleanup
* transcript chunking

---

# Siddhu

## Wiki Experience + UI

Responsibilities:

* Markdown rendering
* sidebar navigation
* wiki links
* search UI
* chat interface

---

# 11. Suggested Timeline

# Week 1

## Foundations

Goals:

* setup project
* transcription working
* basic Markdown generation

---

# Week 2

## AI Compilation

Goals:

* concept extraction
* wiki page generation
* page updates

---

# Week 3

## Linking + Navigation

Goals:

* wiki links
* Markdown browsing
* related concepts

---

# Week 4

## Search + Chat

Goals:

* search functionality
* AI chat over wiki
* source references

---

# Week 5

## Cleanup + Improvements

Goals:

* better prompts
* duplicate reduction
* UI polish

---

# 12. Success Criteria

The project is considered successful if:

* videos can be dropped into `/raw`
* transcripts are automatically generated
* AI creates useful Markdown pages
* pages become interlinked
* users can browse/search/chat with the wiki
* the knowledge base improves incrementally over time

---

# 13. Final Demo Expectations

At the end of the internship, the team should demonstrate:

1. Add video into `/raw`
2. Generate transcript automatically
3. AI creates/updates Markdown pages
4. Wiki pages link together
5. User browses/searches the wiki
6. AI answers questions using the wiki
7. Knowledge improves over time through compilation
