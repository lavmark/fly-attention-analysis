# Fly Attention — multisensory behavioral analysis in *Drosophila*

Analysis code for a behavioral study of **visual, auditory, and multisensory attention** in
*Drosophila*. Flies are presented with visual cues (still bar, flicker, delayed, control) and
auditory cues; their turning/orienting responses are quantified per trial, modeled with
**latent state-space (HMM) methods**, and grouped with **unsupervised hierarchical clustering** to
identify attention-related response states.

> Rotation project, Clandinin Lab (Stanford). Notebooks were developed in Google Colab; data lives
> on Google Drive and is not included here, so the cells are meant to be **read** as a code/analysis
> sample (saved cell outputs show representative figures inline).

## Notebooks

| Notebook | What it does |
|---|---|
| [`fly_attention_v1.ipynb`](fly_attention_v1.ipynb) [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lavmark/fly-attention-analysis/blob/main/fly_attention_v1.ipynb) | Refined pipeline: per-trial analysis classes for each paradigm — visual cue (500 ms still bar, flicker, delay, control), auditory cue, and multisensory — with cross-window turning analyses probing motor-feedback attention. |
| [`fly_attention_preliminary.ipynb`](fly_attention_preliminary.ipynb) [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lavmark/fly-attention-analysis/blob/main/fly_attention_preliminary.ipynb) | First-pass analysis: `FlyTrial` data class, batch loading across flies, state-space (HMM) modeling via the [`ssm`](https://github.com/lindermanlab/ssm) library, and hierarchical clustering of trial responses across visual / control / multisensory / delay conditions. |

## Methods & stack

- **Behavioral quantification** — per-trial orienting/turning extraction, windowed cross-correlation of response epochs
- **Latent-state modeling** — hidden Markov / state-space models (`ssm`, `autograd`) to infer behavioral states
- **Unsupervised clustering** — hierarchical clustering (`scipy`: single / complete / average / ward linkage, dendrograms, `fcluster`)
- **Signal processing** — `scipy.signal` filtering and smoothing
- Python · NumPy · pandas · SciPy · Matplotlib · ssm · Jupyter/Colab

## Reproducing

The notebooks expect the behavioral dataset on Google Drive (paths under `clandinin_rotation_data/`,
grouped by condition: `controls/`, `delay/`, `multisensory_.../`, `visualcueflicker/`, …). To run,
point the `working_dir` variable at your own copy of the data and install the dependencies above
(`pip install ssm autograd`).
