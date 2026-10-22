# Opencode

## Project Overview

This checkout stores Pi agent configuration, prompts, skills, and OpenSpec
metadata. It does not contain application source code, a dependency manifest,
or an executable test/build pipeline. See [README.md](README.md) for the inventory
and supported validation commands.

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
- Never speculate about files you have not opened. Consult available knowledge
  or semantic tools first, then read the specific file. If those tools are not
  available, use a targeted file inventory and text search.
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
- For executable code, write or update tests first and verify they fail before
  implementing the fix. For configuration and documentation, validate the actual
  formats and references; do not invent a test suite for this checkout.
- For multi-step tasks, state a brief plan with a verify step each.

### 5. Communication

- Give a high-level explanation of what changed — don't dump diffs without summary.

## Commands

Run these configuration checks from the repository root in PowerShell 7:

```powershell
Get-Content -LiteralPath '.pi/settings.json' -Raw | ConvertFrom-Json
Get-Content -LiteralPath '.pi/dashboard/knowledge_base.json' -Raw | ConvertFrom-Json
```

There is no dependency installation, application build, or test command for
the current checkout. `.pi/settings.json` has no worktree initialization hook.
Only add setup commands when the corresponding source and manifests exist.

## OpenSpec

The [OpenSpec configuration](openspec/config.yaml) selects the `spec-driven`
schema. No active change artifacts are currently checked in. When a change is
needed, place its artifacts under `openspec/changes/<name>/` and follow the
repository's [proposal prompt](.pi/prompts/opsx-propose.md) and
[proposal skill](.pi/skills/openspec-propose/SKILL.md). Check the locally installed
OpenSpec CLI's help before using its commands; this repository does not install it.

<!-- dox-doctrine -->

## DOX doctrine

The knowledge-base configuration for `pi-dashboard-kb-extension` lives in
[.pi/dashboard/knowledge_base.json](.pi/dashboard/knowledge_base.json), including
the `doctrine` settings (`inject`, `write`). The extension's availability depends
on the host environment; its configuration alone does not prove it is running.
