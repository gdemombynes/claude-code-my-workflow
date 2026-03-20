---
paths:
  - "figures/**/*.py"
  - "figures/scripts/**"
---

# Python Figure Conventions

All figures for the AI & Human Capital paper must be publication-ready. No exceptions.

---

## File Organization

- **Scripts:** `figures/scripts/figure_<descriptive_name>.py` (one script per figure)
- **Output:** `figures/output/figure_<descriptive_name>.png` + `.pdf`
- Scripts must be self-contained and runnable from the repo root

---

## Required Template

Every figure script must follow this structure:

```python
"""
Figure: <Short description>
Paper section: <Which section this figure supports>
"""

from pathlib import Path
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib as mpl

# ── Reproducibility ────────────────────────────────────────────────────────────
np.random.seed(42)  # Only if stochastic; omit otherwise

# ── Paths ──────────────────────────────────────────────────────────────────────
ROOT = Path(__file__).parent.parent  # repo root
DATA_DIR = ROOT / "data"
OUT_DIR = ROOT / "figures" / "output"
OUT_DIR.mkdir(parents=True, exist_ok=True)

# ── Style ──────────────────────────────────────────────────────────────────────
plt.style.use("seaborn-v0_8-whitegrid")
mpl.rcParams.update({
    "font.family": "serif",
    "font.size": 11,
    "axes.labelsize": 12,
    "axes.titlesize": 13,
    "legend.fontsize": 10,
    "figure.dpi": 150,  # screen preview; savefig uses 300
})

# ── Data ───────────────────────────────────────────────────────────────────────
# ... load data here ...

# ── Plot ───────────────────────────────────────────────────────────────────────
fig, ax = plt.subplots(figsize=(7, 4.5))
# ... plot code here ...

ax.set_xlabel("X Label")
ax.set_ylabel("Y Label")
ax.set_title("Figure Title")

fig.tight_layout()

# ── Save ───────────────────────────────────────────────────────────────────────
stem = "figure_<name>"
fig.savefig(OUT_DIR / f"{stem}.png", dpi=300, bbox_inches="tight")
fig.savefig(OUT_DIR / f"{stem}.pdf", bbox_inches="tight")
print(f"Saved {stem}.png and {stem}.pdf")
```

---

## Quality Checklist

Before marking a figure complete:

- [ ] Script runs without errors from repo root: `python figures/scripts/figure_name.py`
- [ ] Both `.png` (300 dpi) and `.pdf` exist in `figures/output/`
- [ ] No hardcoded absolute paths — uses `Path(__file__).parent`
- [ ] Style is applied (`plt.style.use(...)` + `rcParams`)
- [ ] All axes labeled; title set; legend if multiple series
- [ ] Fonts match paper (serif, 11-12pt body)
- [ ] Figure is visually clean at 3.5" (single col) or 7" (double col) width
- [ ] `fig.tight_layout()` called before save
- [ ] `set.seed` / `np.random.seed(42)` present if stochastic

---

## Quality Scoring (Python Figures)

| Severity | Issue | Deduction |
|----------|-------|-----------|
| Critical | Script fails to run | -100 |
| Critical | Hardcoded absolute path | -20 |
| Critical | No output file saved | -20 |
| Major | Missing seed when stochastic | -10 |
| Major | No style applied (default matplotlib) | -10 |
| Major | Missing axis labels or title | -5 |
| Minor | No PDF version saved | -3 |
| Minor | `tight_layout()` not called | -2 |

---

## Style Notes

- Prefer `seaborn-v0_8-whitegrid` for most plots; `seaborn-v0_8-paper` for multi-panel
- Use colorblind-friendly palettes: `seaborn.color_palette("colorblind")`
- Never use default matplotlib blue for everything — assign colors intentionally
- Country/region comparisons: use a diverging palette centered on a meaningful reference
- Map figures: use `matplotlib` + `geopandas`; save at higher dpi (400)
