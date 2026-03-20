# Plan: Adapt Workflow Configuration for AI & Human Capital Paper

**Status:** DRAFT
**Date:** 2026-03-20
**Project:** AI and Human Capital in Developing Countries (research paper)

---

## Context

This repo was forked from a template designed for academic lecture slides (Beamer + Quarto). The user's actual project is a research **paper** — not slides — on what AI means for human capital in developing countries. The paper will be written in Google Docs, with Python figures. The infrastructure needs to be stripped of slide-specific concepts and re-oriented around a paper-writing + lit-review workflow.

Key user preferences (to be saved to memory):
- Structured, precise, and rigorous collaboration
- Publication-ready visuals
- Smart workflow that remembers decisions
- Plan-first always; contractor mode after approval
- More frequent check-ins during early sessions to learn the workflow

---

## What Changes

### 1. Update CLAUDE.md (primary config)

Fill placeholders and restructure for a paper project:
- **Project:** AI and Human Capital in Developing Countries
- **Institution:** (to be filled by user — I'll leave a clear prompt)
- Remove slide-specific sections (Beamer environments, Quarto CSS, lecture table)
- Replace with: paper structure tracker, Python figure conventions, Google Doc link field
- Replace Commands section: remove LaTeX/Quarto commands; add Python figure generation and lit-review commands
- Update Skills Quick Reference: remove slide skills, highlight paper-relevant ones
- Update folder structure diagram to match new layout

### 2. Create project folder structure

New directories to create (with `.gitkeep`):
```
literature/raw/          # Downloaded PDFs
literature/summaries/    # Structured notes per paper
figures/scripts/         # Python scripts for figures
figures/output/          # PNG/PDF outputs
paper/                   # Local copies / exported drafts from Google Doc
data/                    # Raw and processed datasets
```

Remove from CLAUDE.md references (but keep dirs that exist):
- `Slides/`, `Quarto/`, `Preambles/`, `docs/` — already exist, don't delete, just de-emphasize

### 3. Add Python figures rule

Create `.claude/rules/python-figures.md`:
- Always use `matplotlib` with consistent style (publication-ready)
- Figure scripts must be self-contained and reproducible
- Required: `set_style()` at top, `savefig()` with both PNG (300 dpi) and PDF
- No hardcoded paths
- Every figure script in `figures/scripts/`, output to `figures/output/`

### 4. Update quality-gates.md paths

Change path scoping from `Slides/**/*.tex`, `Quarto/**/*.qmd` to:
- `figures/scripts/**/*.py`
- `literature/summaries/**/*.md`
- `paper/**/*.md`

Add Python quality rubric:
- Critical: syntax errors (-100), hardcoded paths (-20)
- Major: missing reproducibility seed if stochastic (-10), no savefig (-5)
- Minor: missing style config (-3)

### 5. Update orchestrator-research.md

Adapt the research orchestrator loop for Python instead of R:
- Replace `Rscript` checks with `python` checks
- Replace `set.seed()` with `np.random.seed()` / `random.seed()`
- Replace `.R` file patterns with `.py`

### 6. Disable slide-specific rules (add `paths:` scope or comment out)

These rules are already path-scoped to `Slides/**` or `Quarto/**` — they won't fire. But update their headers to clarify they're not relevant for this project. No deletion (template preservation principle).

### 7. Save user preferences to memory

Write memory files capturing:
- User's project context and goals
- Collaboration style preferences (rigorous, publication-ready, more check-ins early)
- Python as primary analysis language (not R)
- Google Doc as primary writing surface

### 8. Update bibliography filename in CLAUDE.md

Rename reference from `Bibliography_base.bib` → `references.bib` (more standard for papers)
Actually: keep `Bibliography_base.bib` as-is (it already exists), just reference it correctly.

---

## Files to Modify

| File | Action |
|------|--------|
| `CLAUDE.md` | Major rewrite — fill placeholders, restructure for paper |
| `.claude/rules/quality-gates.md` | Update paths + add Python rubric |
| `.claude/rules/orchestrator-research.md` | Replace R → Python |
| `.claude/rules/python-figures.md` | **NEW** — Python figure conventions |

## Directories to Create

- `literature/raw/`
- `literature/summaries/`
- `figures/scripts/`
- `figures/output/`
- `paper/`
- `data/`
- `quality_reports/plans/`
- `quality_reports/session_logs/`
- `quality_reports/specs/`

## Memory Files to Write

- `user_profile.md` — role, goals, project
- `feedback_workflow.md` — structured/rigorous preferences, check-in frequency
- `project_aihumancapital.md` — paper topic, outputs, tools

---

## Verification

After implementation:
1. Read CLAUDE.md — confirm no unresolved `[PLACEHOLDER]` blocks
2. Confirm all new directories exist (`ls`)
3. Confirm python-figures rule is readable and well-formed
4. Confirm quality-gates paths are updated
5. Confirm memory files are written and indexed in MEMORY.md

---

## Open Questions

1. **Institution** — what institution should I put in CLAUDE.md? (or leave blank for now)
2. **Google Doc link** — do you want to track the paper's Google Doc URL in CLAUDE.md?
3. **Data** — do you have or expect to collect your own data, or is this purely a lit review + synthesis paper?
