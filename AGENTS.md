# Opencode

## Project Overview

<!-- One-paragraph description of what this project is. -->

> Keep this root file lean. It loads into every agent turn — verbose doctrine
> buries the rules the model must follow (signal dilution). Route per-file and
> task-specific detail into the directory `AGENTS.md` tree and `docs/`; keep
> only always-on doctrine here.

## Code Instructions

Behavioral guidelines to reduce common coding mistakes. Bias toward caution over
speed. For trivial tasks, use judgment.

### 1. Think Before Coding

- State assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them — don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- Never speculate about code you have not opened. Consult the doc tree
  (`kb agents <path>` / `kb_search`) first, then read the specific file.
- Before any major change, confirm the plan.

### 2. Simplicity First

- Minimum code that solves the problem. Nothing speculative.
- No features beyond what was asked; no abstractions for single-use code.
- No error handling for impossible scenarios.
- DRY: extract a shared helper when a pattern repeats; don't pre-extract for one call site.

### 3. Surgical Changes

- Touch only what you must. Match existing style.
- Don't refactor things that aren't broken.
- Remove imports/variables your changes made unused; leave pre-existing dead code (mention it).
- Every changed line traces directly to the request.

### 4. Goal-Driven Execution (TDD)

- Turn tasks into verifiable goals with explicit success criteria.
- Write or update tests first, verify they fail, then write the minimal implementation to pass.
- For multi-step tasks, state a brief plan with a verify step each.

### 5. Communication

- Give a high-level explanation of what changed — don't dump diffs without summary.

## Commands

<!-- Filled from the detected project stack; edit if your commands differ. -->

```bash
python -m venv .venv && .venv/Scripts/python -m pip install -r requirements.txt    # install dependencies
.venv/Scripts/python -m pytest       # run tests
python -m build      # build
```

## OpenSpec

This project uses OpenSpec for spec-driven changes. Place change artifacts at
`openspec/changes/<name>/`. Prefer `openspec change new <name>` to scaffold.

When authoring a proposal, add a `<!-- dox-doctrine -->

## DOX doctrine

Per-turn DOX doctrine — the kb-first READ discipline and the directory `AGENTS.md`
WRITE discipline — is injected by the `pi-dashboard-kb-extension`. Tune it in
`.pi/dashboard/knowledge_base.json` under the `doctrine` key (`inject`, `write`).
