# Judge-Aware Ranking Framework — Official Code

**Paper:** [A Judge-Aware Ranking Framework for Evaluating Large Language Models without Ground Truth](https://arxiv.org/abs/2601.21817)

**Leaderboard:** [https://arxiv.org/abs/2601.21817](https://wujw13.github.io/rank_llm/)

**Authors:** Mingyuan Xu, Xinzi Tan, Jiawei Wu, Doudou Zhou

---

## Overview

This repository contains the official code and artifacts for reproducing and extending the experiments in *A Judge-Aware Ranking Framework for Evaluating Large Language Models without Ground Truth* (arXiv:2601.21817). The project implements a judge-aware extension of pairwise ranking models that jointly estimates model quality and judge reliability from pairwise comparisons and judge scores. The codebase is organized to support reproducible experiments, data preprocessing, model estimation, evaluation, and result generation.

---

## Repository layout

```
README.md
data/                # scored datasets (see below)
request_data/        # prompts and request scripts used to query judge LLMs
results/             # all generated outputs, statistics, and intermediate files
main/                # primary codebase; main.py implements fit + evaluation
```

### `data/`

Contains the scored datasets used to fit and evaluate the judge-aware ranking model. All datasets in this folder are **already scored by judge LLMs** and are ready to be consumed directly by the model.

Example contents:

* `judge_results_10k_chatbot_arena/` — Chatbot Arena dataset (judge LLM scores included)
* `judge_results_10k_mtbench/` — MT-Bench dataset (judge LLM scores included)
* `judge_results_10k_ultrafeedback/` — UltraFeedback dataset (judge LLM scores included)
* `in_house_data/` — In-house evaluation data collected by the authors (judge LLM scores included)

### `request_data/`

This folder documents and stores the request templates, prompt scripts, and tooling used to query judge LLMs for the scored judgments that populate `data/`.

**Note:** The actual outputs of those requests and aggregated statistics are saved under `results/` (see below). `request_data/` is meant as the reproducible recipe for how the scored judgments were collected.

### `results/`

A directory for all generated outputs produced by running `main/main.py` or other scripts. This folder acts as the canonical place to store both intermediate and final artifacts produced during experiments.

### `main/`

Contains the primary runnable code for fitting the judge-aware ranking model and producing results.

Key file:

* `main.py` — the main entrypoint. Responsibilities include:

  * loading data from `data/`
  * fitting the judge-aware model (MLE)
  * computing confidence intervals
  * saving all outputs to `results/`
---

## Requirements

List common dependencies in `requirements.txt`.

```
numpy
scipy
pandas
tqdm
matplotlib
pathlib
collections
typing
datasets
together
openai
oncurrent
```

---

## Citation

If you use this code or methodology in your work, please cite the paper:

```bibtex
@article{xu2026judgeaware,
  title={A Judge-Aware Ranking Framework for Evaluating Large Language Models without Ground Truth},
  author={Mingyuan Xu and Xinzi Tan and Jiawei Wu and Doudou Zhou},
  journal={arXiv preprint arXiv:2601.21817},
  year={2026},
  url={https://arxiv.org/abs/2601.21817}
}


