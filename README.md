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
Military-Skills-Taxonomy/
├── data/
│   ├── processed/
│   │   ├── DAFECD-31-Oct-24.csv
│   │   ├── DAFOCD-31-Oct-24.csv
│   │   ├── LAiSER Final Results.csv
│   │   └── afsc_clean.csv
│   └── raw/
│       ├── DAFECD-31-Oct-24.pdf
│       ├── DAFOCD-31-Oct-24.pdf
│       ├── DoD Military-Civilian Crosswalk.csv
│       └── ESCO-ONET Crosswalk.csv
├── notebooks/
│   ├── AFOCD-AFECD Merge Code.ipynb
│   ├── LAiSER Extraction Analysis.ipynb
│   ├── LAiSER_Taxonomy_Code.ipynb
│   ├── LLM Run CODE V1.ipynb
│   ├── LLM Run CODE V2.ipynb
│   └── Taxonomy Merge Mega Code.ipynb
├── results/
│   ├── Prompts/
│   │   ├── enhanced_taxonomy_prompt.txt
│   │   └── prompt_for_reference.txt
│   ├── laiser/
│   │   └── LAiSER Final Results.csv          # copy kept here for convenience
│   └── llm_taxonomies/
│       ├── military_skills_taxonomy_claude_3_5_sonnet_20250403-001643.txt
│       ├── military_skills_taxonomy_claude_3_5_sonnet_pilot_20250422.txt
│       ├── military_skills_taxonomy_gpt_4_turbo_enhanced_20250403-001752.txt
│       └── military_skills_taxonomy_gpt_4_turbo_pilot_20250422.txt
├── docs/
│   └── paper/
│       └── README.md        # final manuscript & figures live here
└── README.md

