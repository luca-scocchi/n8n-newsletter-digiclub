# Project Overview

This project implements an automated newsletter generation system built with **n8n**.

The workflow aggregates recent articles from multiple WordPress websites, processes them using AI, and produces a fully formatted HTML newsletter ready to be sent to subscribers.

The main objective is to automate editorial work while preserving:
- content freshness
- editorial consistency
- a professional and human-like writing style

---

## Goals

- Collect content from multiple independent WordPress sources
- Ensure only recent and relevant articles are included
- Transform raw articles into concise, engaging newsletter sections
- Enforce editorial rules (length, tone, structure)
- Generate a final HTML newsletter based on a predefined template

---

## Key Principles

- **No content invention**  
  If an article does not meet the requirements (e.g. too old), the workflow returns empty fields instead of fabricating content.

- **Separation of concerns**  
  Each logical step (fetching, validation, summarization, aggregation, rendering) is handled by dedicated nodes.

- **Extensibility**  
  New sources, editorial rules, or output formats can be added without redesigning the entire workflow.

---

## High-Level Workflow

1. Fetch the latest article from each WordPress source
2. Validate publication date (max 14 days old)
3. Generate structured summaries using AI
4. Normalize and aggregate all sections
5. Render the final HTML newsletter

---

## Intended Audience

- Automation engineers
- Marketing and editorial teams
- Developers working with n8n and AI-based workflows
- Organizations managing multi-brand or multi-site content
