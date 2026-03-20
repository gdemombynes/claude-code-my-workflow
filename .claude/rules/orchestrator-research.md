---
paths:
  - "figures/scripts/**/*.py"
  - "explorations/**"
  - "data/**"
---

# Research Project Orchestrator

**For Python scripts, figures, and data analysis** — use this simplified loop instead of the full multi-agent orchestrator.

## The Simple Loop

```
Plan approved → orchestrator activates
  │
  Step 1: IMPLEMENT — Execute plan steps
  │
  Step 2: VERIFY — Run code, check outputs
  │         Python scripts: `python script.py` runs without error
  │         Figures: PNG + PDF created in figures/output/
  │         Stochastic code: np.random.seed() / random.seed() present
  │         If verification fails → fix → re-verify
  │
  Step 3: SCORE — Apply quality-gates rubric
  │
  └── Score >= 80?
        YES → Done (commit when user signals)
        NO  → Fix blocking issues, re-verify, re-score
```

**No 5-round loops. No multi-agent reviews. Just: write, test, done.**

## Verification Checklist

- [ ] Script runs without errors: `python figures/scripts/figure_name.py`
- [ ] All imports at top of file
- [ ] No hardcoded absolute paths — uses `Path(__file__).parent`
- [ ] `np.random.seed(42)` or `random.seed(42)` at top if stochastic
- [ ] Output files exist at expected paths in `figures/output/`
- [ ] Both `.png` (300 dpi) and `.pdf` saved
- [ ] Quality score >= 80

## Literature Workflow

When processing PDFs from `literature/raw/`:
1. Check page count: `pdfinfo paper.pdf | grep Pages`
2. Use the Read tool for PDFs ≤ 20 pages directly
3. For longer papers: split with Ghostscript (see `pdf-processing.md` rule)
4. Save structured summary to `literature/summaries/author_year_shorttitle.md`
5. Add citation to `Bibliography_base.bib`

## Summary Template

```markdown
# Author(s) (Year) — Short Title

**Full citation:** Author, A., & Author, B. (Year). Title. *Journal/Source*.
**Type:** [RCT / Observational / Survey / Review / Theory]
**Country/Region:** [e.g., Kenya, Sub-Saharan Africa]
**Sample size:** [N = ...]
**Time period:** [e.g., 2018–2022]

## Main Research Question
...

## Data & Methods
...

## Key Findings
- ...

## Relevance to Paper
...

## Limitations / Caveats
...
```
