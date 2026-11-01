---
framework_version: 1.1.0
---

# Agent Guidelines: AI Job Search

This workspace is structured to manage job search activities, scraper tools, CVs, cover letters, and interview preparation across multiple AI developer CLIs and frameworks.

## Multi-Runtime & Multi-Model Architecture

This repository natively supports both **Google Antigravity CLI (`agy`)** and **Claude Code**, as well as other agent runtimes (Gemini CLI, Codex, Cursor, etc.) with first-class model support for **Gemini models** (e.g. Gemini 2.5 Pro, Gemini 2.5 Flash, Gemini 3.8 Flash) and Claude models.

### Runtime Configuration Files

- **Google Antigravity CLI & Gemini CLI:**
  - Loaded rule file: [GEMINI.md](GEMINI.md) and [AGENTS.md](AGENTS.md).
  - Customization root: `.agents/`
  - Skills discovery: `.agents/skills/*/SKILL.md` and declared external directories in [.agents/skills.json](.agents/skills.json).
  - Workflow skills: `.agents/skills/job-apply/`, `.agents/skills/job-setup/`, `.agents/skills/job-rank/`, `.agents/skills/job-interview/`, `.agents/skills/job-outcome/`.
- **Claude Code:**
  - Loaded rule file: [CLAUDE.md](CLAUDE.md).
  - Customization root: `.claude/`
  - Commands: `.claude/commands/*.md`.
- **Any CLI / Universal Agents:**
  - Load [AGENTS.md](AGENTS.md) and [GEMINI.md](GEMINI.md) as the primary instruction source.

---

## Thin-Pointer Design (Single Source of Truth)

To prevent duplication and configuration drift across different AI agent frameworks (Claude Code, Google Antigravity, Codex, Cursor, Gemini CLI, etc.), this workspace uses a unified thin-pointer design. All agent runtimes should load the canonical specifications and candidate profiles from the files and directories below:

1. **Personal Candidate Profile:**
   - The candidate profile, contact details, education, and target preferences are defined in [GEMINI.md](GEMINI.md) / [CLAUDE.md](CLAUDE.md) and the individual profile methodology files under [.claude/skills/job-application-assistant/](.claude/skills/job-application-assistant/) (specifically `01-*.md` etc.).
2. **Canonical Workflow Specifications:**
   - The step-by-step instructions and triggers for tasks (setup, scrape, rank, apply, upskill, interview) are defined in the [.claude/](.claude/) directory (specifically under `.claude/skills/` and `.claude/commands/`).
   - Workflow skills under `.agents/skills/` serve as thin pointers to these canonical specifications.
   - Do not duplicate these rules or specifications. Treat canonical files as the single source of truth.
3. **Portal Search Skills:**
   - Job-portal search CLIs live under [.agents/skills/](.agents/skills/) in the portable Agent Skills format (with a `SKILL.md` per portal). Codex and Antigravity discover these automatically; the `/scrape` workflow in [.claude/skills/job-scraper/](.claude/skills/job-scraper/) orchestrates them.

---

## Running with Antigravity CLI (`agy`)

Launch the Antigravity CLI in this repository root:

```bash
agy
```

Inside the interactive session, you can run any workflow using slash commands or natural language:
- `/setup` — Walk through onboarding or import documents to configure your profile.
- `/scrape` — Search configured job boards for openings matching your profile.
- `/rank` — Batch-score collected postings against your candidate rubric.
- `/apply <URL>` — Evaluate fit, tailor CV and cover letter, and run full verification.
- `/interview <company> <role>` — Generate STAR interview prep pack and talking points.
- `/outcome` — Record application status and outcome notes.

