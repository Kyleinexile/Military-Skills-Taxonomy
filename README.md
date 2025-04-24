# Military-Skills-Taxonomy 📚⚙️

_A pilot study showing how modern NLP and large-language-model techniques can turn Air Force classification documents into a machine-readable skills taxonomy._

<p align="center">
  <img src="docs/paper/figures/dual_pipeline_diagram.png" width="620" alt="Dual-pipeline overview"/>
</p>

---

## Why does this matter?

Across the Department of Defense there is still no authoritative, machine‑readable skills taxonomy linking military occupational specialties to their civilian equivalents. Consequently, veterans, workforce planners, and private‑sector employers lack a shared, data‑driven vocabulary for translating service‑earned competencies into the language of the labor market.
This project served as a pilot to demonstrate that modern AI tools can bridge that gap. I constructed and evaluated two complementary pipelines:
1. •	**LLM Prototype**: A bottom‑up pipeline that first merged three structured civilian sources—O*NET, ESCO, and the DoD Military‑Civilian Crosswalk—into a single “mega‑skills” table. Two large‑language‑models (Claude 3.5 Sonnet 20240620 and GPT‑4‑Turbo) then processed ≈ 30 AFSCs (15 Officer, 15 Enlisted) from that table to generate parallel multi‑level skill taxonomies.
2. •	**LAiSER Prototype**: A "top-down" approach extracting skills directly from military documents by converting the Air Force Officer/Enlisted Classification Directories (AFOCD & AFECD) into CSV, processed 123 AFSC descriptions with GWU’s LAiSER (Leveraging AI for Skills Extraction & Research) extraction tool, and automatically aligned every extracted skill phrase to established taxonomies via cosine similarity scoring.



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
│   └── paper/
│              
└── README.md

