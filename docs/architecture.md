# Architecture

This document describes the technical architecture of the newsletter automation workflow.

The system is built around **n8n** as the orchestration layer and integrates external services such as WordPress APIs and Google Gemini (PaLM).

---

## Architectural Overview

The workflow follows a linear but modular pipeline:

- Data ingestion
- Validation and filtering
- AI-powered transformation
- Aggregation
- Final rendering

Each phase is isolated to simplify debugging and maintenance.

---

## Data Sources

- Multiple WordPress websites accessed via REST API
- Each source is queried independently
- Only the most recent article is retrieved per source

---

## Validation Layer

Before any AI processing occurs:
- Publication dates are compared against the current date
- Articles older than 14 days are discarded
- Discarded articles result in empty outputs, not errors

This guarantees content freshness and editorial relevance.

---

## AI Integration

AI is used to:
- Generate short titles
- Produce concise summaries
- Create call-to-action text
- Assign a single editorial tag

Key characteristics:
- Strict prompt constraints (length, tone, format)
- Deterministic output structure
- No markdown or formatting artifacts in responses

---

## Data Aggregation

Once individual sections are generated:
- Outputs are normalized into a shared structure
- All sections are merged into a single dataset
- The aggregated data becomes the single source of truth for rendering

---

## Rendering Layer

- A predefined HTML template is used
- Content is injected without altering layout or order
- The final output is a standalone HTML newsletter

---

## Error Handling

- Missing or invalid content does not stop execution
- Empty sections are handled gracefully
- The workflow favors partial output over hard failures
