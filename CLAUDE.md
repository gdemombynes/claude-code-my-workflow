# CLAUDE.md — AI and Human Capital in Developing Countries

**Project:** AI and Human Capital in Developing Countries
**Institution:** World Bank
**Output:** Research paper (written in Google Docs)
**Branch:** main

---

## Core Principles

- **Plan first** — enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** — run scripts and confirm outputs at the end of every task
- **Single source of truth** — Google Doc is authoritative for prose; `figures/scripts/` is authoritative for all figures
- **Quality gates** — nothing ships below 80/100; all figures must be publication-ready
- **[LEARN] tags** — when corrected, save `[LEARN:category] wrong → right` to MEMORY.md

---

## Paper Overview

**Title:** Hope or Hype: Can AI Boost Human Capital in the Global South?
**Author:** Gabriel Demombynes
**Focus:** Original research (RCTs, causal studies); working papers and preprints included; education + health in LMICs
**Writing surface:** Google Docs
**Figures:** Python (matplotlib/seaborn), exported as PNG (300 dpi) + PDF
**Bibliography:** `Bibliography_base.bib`

**Google Doc:** https://docs.google.com/document/d/1vxr1U4iYvJLHHY79yxkjhWzocXinKGmJKDDsD3Ayci0/edit?usp=sharing

---

## Folder Structure

```
aihumancapital/
├── CLAUDE.md                    # This file
├── .claude/                     # Rules, skills, agents, hooks
├── Bibliography_base.bib        # Centralized bibliography
├── literature/
│   ├── raw/                     # Downloaded PDFs of source papers
│   └── summaries/               # Structured notes per paper (markdown)
├── figures/
│   ├── scripts/                 # Python scripts (one per figure)
│   └── output/                  # PNG + PDF outputs (gitignored if large)
├── paper/                       # Local markdown drafts / exported Google Doc snapshots
├── data/                        # Raw and processed datasets
├── quality_reports/             # Plans, session logs, merge reports
│   ├── plans/
│   ├── session_logs/
│   └── specs/
├── explorations/                # Research sandbox (see rules)
└── templates/                   # Session log, quality report templates
```

---

## Commands

```bash
# Run a Python figure script
python figures/scripts/figure_name.py

# Run all figure scripts
for f in figures/scripts/*.py; do python "$f"; done

# Validate bibliography citations
# (use /validate-bib skill)

# Check PDF paper (split for processing)
pdfinfo paper.pdf | grep "Pages:"
```

---

## Quality Thresholds

| Score | Gate | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for sharing/deployment |
| 95 | Excellence | Aspirational; required for figures in final paper |

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/lit-review [topic]` | Structured literature search + synthesis |
| `/interview-me [topic]` | Interactive research interview to formalize ideas |
| `/research-ideation [topic]` | Generate hypotheses + empirical strategies |
| `/review-paper [file]` | Comprehensive manuscript review |
| `/proofread [file]` | Grammar/typo/clarity review |
| `/data-analysis [dataset]` | End-to-end analysis workflow |
| `/validate-bib` | Cross-reference citations vs bibliography |
| `/commit [msg]` | Stage, commit, PR, merge |
| `/learn [skill-name]` | Extract discovery into persistent skill |
| `/context-status` | Show session health + context usage |
| `/deep-audit` | Repository-wide consistency audit |

---

## Python Figure Standards

All figures must follow these conventions (enforced by `.claude/rules/python-figures.md`):

| Requirement | Standard |
|-------------|----------|
| Style | `seaborn-v0_8-whitegrid` or `seaborn-v0_8-paper` |
| Resolution | 300 dpi for PNG; PDF always included |
| Output paths | `figures/output/figure_name.png` + `.pdf` |
| Reproducibility | `np.random.seed()` / `random.seed()` if stochastic |
| No hardcoded paths | Use `Path(__file__).parent` for script-relative paths |

---

## Paper Structure Tracker

| Section | Status | Notes |
|---------|--------|-------|
| 1. Introduction | Draft | Needs quotes on AI power; OLPC framing good |
| 2. Conceptual Framework | Draft | Direct provision vs. augmentation; enabling factors (electricity, internet, devices, expertise, institutions) |
| 3. Evidence — Education | Draft | 3 GenAI studies: Sierra Leone (Choi), Ghana/Rori (Henkel), Nigeria (De Simone) |
| 3. Evidence — Health | Draft | Diagnostics, imaging, maternal health, health systems; many sub-sections |
| 3. Evidence — Mental Health | Placeholder | Flagged for "deep research review" |
| 3. Evidence — Livelihoods | Placeholder | Uganda, Philippines examples noted |
| 4. Perils | Outline only | Effort reduction, distraction, misinformation, bias, privacy |
| 5. Research Agenda | Outline only | 4 bullet points |
| 6. Policy Pathways | Outline only | 3 bullet points |
| 7. Conclusion | Not started | |
| Figures | Planned | Electricity access, internet access, device ownership |
