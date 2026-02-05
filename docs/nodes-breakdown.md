# Nodes Breakdown

This document provides a detailed explanation of the main nodes and logical blocks used in the n8n workflow.

The goal is to clarify the responsibility of each component and simplify future modifications.

---

## WordPress Fetch Nodes

**Purpose**
- Retrieve the latest article from each WordPress source

**Key Notes**
- One node per website
- Configured with a limit of one item
- Acts as the entry point of the workflow

---

## Date Validation Logic

**Purpose**
- Ensure content freshness

**How it works**
- Compares article publication date with the current date
- Applies a 14-day threshold
- Blocks outdated content from further processing

---

## AI Agent Nodes

**Purpose**
- Transform raw articles into newsletter-ready sections

**Responsibilities**
- Generate a short title
- Produce a summarized body text
- Create a call-to-action with a link
- Assign exactly one tag

**Important Constraints**
- Fixed output schema
- No extra text or explanations
- Editorial tone aligned with business communication

---

## Parsing & Cleanup Code Nodes

**Purpose**
- Extract structured fields from AI output
- Remove unwanted formatting
- Normalize text for aggregation

These nodes act as a bridge between AI output and deterministic data processing.

---

## Merge & Aggregate Nodes

**Purpose**
- Combine outputs from all sources

**Behavior**
- Maintains a fixed order of sections
- Produces a single aggregated object
- Ensures missing sections do not break the flow

---

## HTML Rendering Nodes

**Purpose**
- Generate the final newsletter markup

**Details**
- Uses a static HTML template
- Injects content without modifying layout
- Outputs a clean HTML file ready for delivery
