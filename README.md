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

## Quick Start 🚀 — Pick Your Pipeline

| Goal | LLM Taxonomy Prototype  (bottom-up) |  LAiSER Extraction Prototype  (top-down) |
|------|-------------------------------------|------------------------------------------|
| **Run in the cloud (no install)** | <br>1. Open [`notebooks/LLM Run CODE V2.ipynb`](notebooks/LLM%20Run%20CODE%20V2.ipynb) <br>2. Click ![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg) <br>3. Provide OpenAI / Anthropic API keys when prompted | <br>1. Open [`notebooks/LAiSER_Taxonomy_Code.ipynb`](notebooks/LAiSER_Taxonomy_Code.ipynb) <br>2. Click **Colab** badge <br>3. Run **CPU-only** or switch runtime → GPU (faster) |
| **Run locally** | ```bash\n# clone & set up\nconda env create -f environment.yml\nconda activate miltax\njupyter lab notebooks/LLM\_Run\_CODE\_V2.ipynb\n``` | ```bash\nconda env create -f environment.yml\nconda activate miltax\njupyter lab notebooks/LAiSER_Taxonomy_Code.ipynb\n``` |
| **Required input files** | *Structured* data in **`data/processed/`**:  <br>• `afsc_clean.csv`  <br>• `O*NET …` & `ESCO …` cross-walks (already merged by the notebook) | *Unstructured* AFSC text in **`data/raw/`** (PDF) or **`data/processed/`** (CSV):  <br>• `DAFOCD-31-Oct-24.csv`  <br>• `DAFECD-31-Oct-24.csv` |
| **Outputs produced** | Hierarchical taxonomies written to **`results/llm_taxonomies/…txt`** | Skill-to-AFSC alignments written to **`results/laiser/LAiSER Final Results.csv`** |
| **Typical runtime*** | ~8 min / 30-AFSC sample (API) | ~3 h on free Colab CPU  → ~20 min on single T4/L4 GPU |

\* Times will vary with network / hardware.

> **Large files (>100 MB)** The enhanced_military_skills_taxonomy file is quite large and saved as a release if you need it.
> 

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


---

## Related Projects & Credits 🏅

**LAiSER** <https://github.com/LAiSER-Software> | GWU’s open-source pipeline|
> **Acknowledgments**      
> • The LAiSER development team—special thanks for the help!  

