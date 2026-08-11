# AGENTS.md — HEREBUS client repo

## Purpose

Client delivery workspace for HEREBUS (Saskia's food business): intake, product scope, website/WhatsApp planning, session notes.

## Hard rules

1. **No personal banking / identity data** in this repo. That stays in `Ai-Whisperers/saskia-personal-context`.
2. **No live customer PII** (names, phones, addresses of buyers).
3. **No hand-editing of HEREBUS xlsx here** — workbooks are regenerated from Python in the personal-context repo.
4. **WhatsApp bot code does not live here by default** until explicitly scoped in; designs/notes OK under `docs/`.
5. Prefer Spanish for client-facing docs; English OK for internal analysis.

## Related repos

- `Ai-Whisperers/saskia-personal-context` — Excels, AGENTS foodbiz rules, calendar planner
- Hermes agent repos — infrastructure; do not freely rewrite foodbiz workbooks without approval gates
