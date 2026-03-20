# LLM Causal Reasoning Audit
### Auditing Large Language Model Performance on Causal Inference Tasks in Economics and Social Science

> **Status: In Development** — Actively being built as part of a broader interest in critical AI literacy for Arts education.

---

## Overview

Large language models (LLMs) are increasingly used by students and researchers in the social sciences and humanities. But how well do they actually *reason*? This project systematically evaluates how well a locally-run LLM (via [Ollama](https://ollama.com)) handles causal reasoning tasks drawn from economics — one of the most common places where confusing correlation with causation leads to bad conclusions.

The notebook audits LLM responses across five categories of causal reasoning, compares performance across three prompting strategies, and frames all findings as a **critical AI literacy exercise** for undergraduate Arts students who may not have a technical background.

---

## Motivation

This project sits at the intersection of two things I care about:

1. **Causal inference in economics.** In ECON 398 (Introduction to Causal Methods) at UBC, I applied difference-in-differences methodology to estimate the causal effect of immigration policy reform on regional wages. That coursework made clear how difficult — and important — it is to distinguish causation from correlation. LLMs are trained on text that routinely conflates the two.

2. **Critical AI literacy.** Tools like ChatGPT are being adopted rapidly in academic settings, often without a clear understanding of their limitations. This project is designed to make those limitations visible and teachable, particularly for students in the social sciences and humanities who rely on causal reasoning in their discipline.

---

## What the Notebook Does

1. **Loads a local LLM** via the Ollama Python client (no API key required — runs entirely on your machine)
2. **Presents 20 curated questions** across five causal reasoning categories:
   - Correlation vs. Causation
   - Confounding Variables
   - Difference-in-Differences
   - Selection Bias
   - Reverse Causality
3. **Tests three prompting strategies** on each question:
   - Direct prompting
   - Chain-of-thought prompting
   - Few-shot prompting with economics examples
4. **Scores and logs all responses** to a CSV file for analysis
5. **Visualizes results** using Plotly:
   - Accuracy by reasoning category (bar chart)
   - Prompting strategy comparison (heatmap)
6. **Frames all findings** with plain-language Markdown explanations written for a non-technical Arts undergraduate audience

---

## Repository Structure

```
llm-causal-audit/
│
├── llm_causal_audit.ipynb     # Main Jupyter notebook (setup → prompting → scoring → visualization)
├── question_bank.py           # Curated question bank with correct answers and category labels
├── results/
│   └── llm_causal_audit_results.csv   # Logged LLM responses and scores
├── figures/
│   ├── accuracy_by_category.png       # Bar chart: accuracy by reasoning type
│   └── heatmap_strategies.png         # Heatmap: prompting strategy vs. category
├── requirements.txt           # Python dependencies
└── README.md
```

---

## Requirements

```
ollama>=0.4.0
pandas>=2.0.0
plotly>=5.0.0
kaleido>=0.2.1
jupyter>=1.0.0
```

Install all dependencies from inside a Jupyter cell:
```python
!pip install ollama pandas plotly kaleido jupyter
```

---

## Setup and Usage

**Step 1 — Install Ollama**

- **Linux/WSL:** Run in a Jupyter cell:
  ```python
  !curl -fsSL https://ollama.com/install.sh | sh
  ```
- **Mac/Windows:** Download the app from [ollama.com](https://ollama.com) (one-time install, ~2 min)

**Step 2 — Pull a model and start the server**

```python
!ollama pull llama3.2
!ollama serve &
```

**Step 3 — Run the notebook**

Open `llm_causal_audit.ipynb` and run `Kernel → Restart & Run All`. The notebook is fully self-contained and runs top-to-bottom without any manual steps.

---

## Key Design Choices

- **Local model only (Ollama):** No API key, no cost, fully reproducible. Anyone can run this on their own machine.
- **Manual scoring with a rubric:** Responses are scored 0 / 0.5 / 1 using a transparent rubric defined in the notebook. Manual evaluation is appropriate here because causal reasoning requires judgment, not pattern matching — and making that explicit is itself an educational point.
- **Written for a non-technical reader:** Every section includes a plain-language Markdown explanation before the code, so the notebook is readable as a standalone educational document, not just a script.

---

## Educational Connection

This project is motivated by the goals of the UBC TLEF GenAI Cluster initiative: to develop discipline-specific educational modules that demystify AI for Arts undergraduates. The findings here — particularly which types of causal errors LLMs make most consistently, and how prompting strategy affects performance — are designed to be directly usable as discussion material in an economics or social science classroom.

---

## Author

**Jaewoong Shin**  
BA, Combined Major in Economics and Statistics — University of British Columbia  
[LinkedIn](https://linkedin.com/in/jaewoong-shin-5348a922a) · [GitHub](https://github.com/jaesgithub)
