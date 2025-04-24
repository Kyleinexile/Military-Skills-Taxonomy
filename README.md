# Military-Skills-Taxonomy 📚⚙️
*A pilot study showing how modern NLP + LLM techniques can turn Air Force classification documents into a machine-readable skills taxonomy.*

---

## Why does this matter?

Across the Department of Defense there is still **no authoritative, machine-readable skills taxonomy** linking military occupational specialties to their civilian equivalents.  
Without it, veterans, workforce planners, and employers lack a shared, data-driven vocabulary for translating service-earned competencies into the language of the labour market.

This repository demonstrates two complementary AI pipelines that can close that gap:

| Pipeline | What it does | Scale in this pilot |
|----------|--------------|---------------------|
| **LLM prototype** (bottom-up) | Merges three structured civilian sources—O*NET, ESCO & the DoD Military-Civilian Crosswalk—then uses GPT-4 Turbo & Claude 3.5 Sonnet to generate a three-level skills hierarchy. | 30 AFSCs (15 Officer, 15 Enlisted) |
| **LAiSER prototype** (top-down) | Parses raw AFOCD/AFECD text, extracts skills with GWU’s **LAiSER** tool (SkillNer + cosine similarity) and aligns them to ESCO/OSN tags. | 123 AFSC descriptions |

---

## Quick Start 🚀

| Goal | What to do |
|------|------------|
| **Browse results** | Open any file in **`results/`** (`laiser/` for LAiSER CSV, `llm_taxonomies/` for LLM outputs). |
| **Re-run a notebook in Colab** | Click <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open in Colab" height="20"/> next to the notebook you want. |
| **Reproduce locally** | `conda env create -f environment.yml` → `conda activate miltax` → open notebooks in **`notebooks/`**. |

> **Large files (> 100 MB)** use Git LFS.  
> After cloning run `git lfs install && git lfs pull` if you see pointer files.

---

## Repository Structure
```text
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
│   │   └── LAiSER Final Results.csv
│   └── llm_taxonomies/
│       ├── military_skills_taxonomy_claude_3_5_sonnet_20250403-001643.txt
│       ├── military_skills_taxonomy_claude_3_5_sonnet_pilot_20250422.txt
│       ├── military_skills_taxonomy_gpt_4_turbo_enhanced_20250403-001752.txt
│       └── military_skills_taxonomy_gpt_4_turbo_pilot_20250422.txt
├── docs/
│   └── paper/                 # manuscript, figures, etc.
└── README.md                  # you are here
