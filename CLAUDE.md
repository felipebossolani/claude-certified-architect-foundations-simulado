# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A self-contained, single-page quiz app for studying the **Claude Certified Architect — Foundations (CCA-F)** exam. No build tools, no frameworks, no dependencies.

**Live:** https://felipebossolani.github.io/claude-certified-architect-foundations-simulado/

## Architecture

- **`index.html`** — The entire app: HTML structure, CSS (dark theme with CSS variables), and vanilla JavaScript. All-in-one, ~650 lines. Questions are loaded inline from the JSON file via a `const QUESTIONS = ...` assignment at line 333.
- **`all_questions.json`** — Question bank (337 questions) with schema: `{ id, source, scenario, task_statement, question, options: {A,B,C,D}, correct, explanation, domain }`.

## Exam Domains (5)

| Domain | Title | Weight | Questions |
|--------|-------|--------|-----------|
| D1 | Agentic Architecture & Orchestration | 27% | 95 |
| D2 | Tool Design & MCP Integration | 18% | 43 |
| D3 | Claude Code Configuration & Workflows | 20% | 90 |
| D4 | Prompt Engineering & Structured Output | 20% | 65 |
| D5 | Context Management & Reliability | 15% | 44 |

## App Features

- Domain filtering (select which domains to study)
- Two answer modes: `immediate` (reveal on click) and `end` (confirm button)
- Question order: `shuffle` or `sequential`
- Scaled scoring (100–1000, pass threshold: 720)
- Per-domain breakdown on results screen
- "Retry wrong" — reshuffles only missed questions for another round

## Key Conventions

- UI language is **Portuguese (pt-BR)**.
- The HTML file embeds the full question array inline — when updating questions, sync both `all_questions.json` and the embedded `QUESTIONS` constant in `index.html`.
- Question IDs follow the pattern `D{domain}-{number}` (e.g., `D1-001`).
- No build step — to run, just `open index.html`.
