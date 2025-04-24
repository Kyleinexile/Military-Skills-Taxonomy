# Military-Skills-Taxonomy 📚⚙️

_A pilot study showing how modern NLP and large-language-model techniques can turn Air Force classification documents into a machine-readable skills taxonomy._

<p align="center">
  <img src="docs/paper/figures/dual_pipeline_diagram.png" width="620" alt="Dual-pipeline overview"/>
</p>

---

## Why does this matter?

Across the U.S. Department of Defense no authoritative, machine-readable mapping exists between military occupations and civilian skill frameworks such as O*NET or ESCO.  
This repository contains the **code, data, and results** for an independent-study project that:

1. **Fuses civilian skills databases** (O*NET 29.1 + ESCO 1.1 + DoD Crosswalk) and lets LLMs build a bottom-up hierarchy.
2. **Extracts skills straight from AFOCD/AFECD PDFs** with GWU’s LAiSER tool (top-down).
3. Demonstrates how the two approaches complement each other and outlines a future hybrid workflow.

---

## Quick Start 🚀

| Want to… | Do this |
|----------|---------|
| **Browse the results** | Open any file in `results/` (LLM taxonomies or the full `LAiSER Final Results.csv`). |
| **Re-run a pipeline in Colab** | Click ![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg) next to the notebook you want—no local set-up needed. |
| **Reproduce locally** | `conda env create -f environment.yml` → `conda activate miltax` → launch notebooks in `notebooks/`. |

> **Large files (>100 MB)** are stored with Git LFS.  
> `git lfs install` then `git lfs pull` after cloning if you see pointer files.

---

## Repository Structure

```text
data/                      ↳ raw PDFs & civilian tables
    ├─ raw/
    └─ processed/          ↳ cleaned CSVs (ready for notebooks)

notebooks/                 ↳ Jupyter & Colab notebooks for every step
results/
    ├─ laiser/             ↳ LAiSER CSV output
    └─ llm_taxonomies/     ↳ GPT-4-Turbo & Claude taxonomy drafts
docs/
    └─ paper/              ↳ final manuscript, figures, and citations
