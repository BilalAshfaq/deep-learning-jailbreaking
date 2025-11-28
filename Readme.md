## Evolutionary Jailbreaking Benchmark

This repository implements an evolutionary jailbreak attack pipeline for evaluating the safety robustness of large language models (LLMs). The included notebook runs iterative prompt mutation, evaluates multiple target models, and logs attack success statistics and visualizations.

# 1. Repository Structure

Main File: evolutionary_jailbreaking.ipynb : The primary notebook. 

It
Loads jailbreak datasets (Hugging Face).
Loads target models (Mistral and a LLaMA-based model).
Loads safety classifier (LlamaGuard).
Runs multi-round evolutionary jailbreak attacks.
Saves detailed logs, metrics, and plots.
demo_evolutionary_jailbreaking.ipynb
A lightweight demo. Uses a small subset of prompts and fewer rounds.

Demo keys are already set, and sample results (summaries, prompts, visualizations) are included in the repo.

Auto-generated directories
content/ – temporary experiment files and model offloading.
results/ – JSON logs: per-attack results, ASR per round, global summary.
plots/ – generated charts (success counts, ASR curves, model comparisons).

# 2. Dependencies & Installation
Core Dependencies

Python ≥ 3.9,
PyTorch,
CUDA toolkit (optional but recommended),
transformers,
datasets,
pandas,
numpy,
matplotlib,
jupyter,
Install (pip)
python -m venv .venv
source .venv/bin/activate

pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118   # or CPU-only
pip install transformers datasets pandas numpy matplotlib jupyter


(Conda installation works similarly.)

# 3. Demo Notebook (Sample Input/Output)

Use evolutionary_jailbreaking.ipynb for a quick example run. Outputs for demo run are already provided in the repo.

The demo:

Runs with predefined keys
Shows sample input prompts
Shows generated adversarial prompts and model responses
Produces sample metrics and visualizations
No configuration needed—just run all cells.

# 4. Dataset Download Instructions

This project uses publicly available jailbreak datasets from Hugging Face:
JailbreakV-28K/JailBreakV-28k
Field: jailbreak_query

JailbreakBench/JBB-Behaviors
Field: Goal

The notebook automatically downloads datasets using:
from datasets import load_dataset
ds = load_dataset("JailbreakV-28K/JailBreakV-28k", "JailBreakV_28K")


For offline use, download the dataset manually from Hugging Face and place it in a data/ folder, then load from disk (JSON/CSV).

# 5. Running the Full Experiment

Install dependencies

Launch Jupyter

Open evolutionary_jailbreaking.ipynb

Optionally adjust:
ROUNDS
ATTACKS_PER_ROUND
SAMPLE_CAP
DATASET_ID

Run all cells

Outputs will be saved under results/ and plots/.
