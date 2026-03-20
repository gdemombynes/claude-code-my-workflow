---
paths:
  - "figures/scripts/**/*.py"
  - "literature/summaries/**/*.md"
  - "paper/**/*.md"
---

# Quality Gates & Scoring Rubrics

## Thresholds

- **80/100 = Commit** — good enough to save
- **90/100 = PR** — ready for sharing
- **95/100 = Excellence** — required for figures in the final published paper

---

## Python Figure Scripts (`figures/scripts/**/*.py`)

| Severity | Issue | Deduction |
|----------|-------|-----------|
| Critical | Script fails to run | -100 |
| Critical | Hardcoded absolute path | -20 |
| Critical | No output saved (`savefig` missing) | -20 |
| Major | Missing seed when stochastic | -10 |
| Major | No style applied (raw matplotlib defaults) | -10 |
| Major | Missing axis labels or title | -5 |
| Minor | No PDF version saved | -3 |
| Minor | `tight_layout()` not called | -2 |
| Minor | No docstring at top of script | -1 |

---

## Literature Summaries (`literature/summaries/**/*.md`)

| Severity | Issue | Deduction |
|----------|-------|-----------|
| Critical | Missing citation / incorrect author/year | -15 |
| Critical | Factual misrepresentation of paper's findings | -20 |
| Major | Missing key fields (RCT type, country, N, outcome) | -5 each |
| Major | Summary mixes up multiple papers | -10 |
| Minor | Inconsistent formatting vs template | -2 |

---

## Paper Drafts (`paper/**/*.md`)

| Severity | Issue | Deduction |
|----------|-------|-----------|
| Critical | Broken or missing citation | -15 |
| Critical | Logical contradiction between sections | -10 |
| Major | Unsupported empirical claim | -10 |
| Major | Grammar/typo errors (>3 per page) | -5 |
| Minor | Passive voice overuse | -2 |
| Minor | Section lacks topic sentence | -1 |

---

## Enforcement

- **Score < 80:** Block commit. List blocking issues.
- **Score < 90:** Allow commit, warn. List recommendations.
- User can override with justification.

## Quality Reports

Generated **only at merge time**. Use `templates/quality-report.md` for format.
Save to `quality_reports/merges/YYYY-MM-DD_[branch-name].md`.

---

## Tolerance Thresholds (Quantitative Claims)

| Quantity | Tolerance | Rationale |
|----------|-----------|-----------|
| Reported estimates from papers | Exact match | No tolerance — cite precisely |
| Derived calculations | ±1e-4 | Rounding in sources |
| Descriptive statistics from data | ±1e-6 | Floating point |
