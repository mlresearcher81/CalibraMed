# CalibraMed: Calibration-Aware Neuro-Symbolic Clinical Decision Support

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mlresearcher81/CalibraMed/blob/main/notebooks/Final_Neuro_Symbolic_Pipeline_Perfect.ipynb)

CalibraMed is a calibration-aware neuro-symbolic framework for translating longitudinal microbiome predictions into safe, structured clinical decisions. The system integrates deep learning models w[...]

---

## 🧠 Overview

Modern microbiome models achieve strong predictive performance but remain difficult to interpret and deploy safely in clinical settings. CalibraMed addresses this challenge by introducing **Calibra[...]

The system combines:

- A **deep learning predictive backbone** (Established baseline)
- A **calibration layer** using Local Calibration Error (LCE)
- A **multi-agent reasoning engine** (LLM-based)
- A **safety-first decision policy** with human-in-the-loop deferral

---

## 🔗 Dataset location

Place the dataset zip and extracted files in the repository `data/` directory. The notebook `notebooks/Final_Neuro_Symbolic_Pipeline_Perfect.ipynb` expects the dataset at:

- data/asv_interpretability_dataset_modified.zip
- data/asv_interpretability_dataset_modified.csv (after extraction)

If you prefer a different location, update the dataset path in the notebook accordingly.

---

## ⚙️ Architecture

CalibraMed operates in two layers:

### 🔹 Neuro Layer (Predictive Backbone)
- BiLSTM + GRU-Attention (Screener Ensemble)
- Temporal Fusion Transformer (Sentinel Model)
- SHAP-based feature attribution
- Local Calibration Error (LCE) estimation

### 🔹 Symbolic Layer (Multi-Agent Reasoning)
- Screener Agent (High-sensitivity reasoning)
- Sentinel Agent (Precision-oriented reasoning)
- Meta-Arbiter Agent (Final decision synthesis)
- LCE-gated safety mechanism

---

## 🔒 Key Features

- ✅ Calibration-aware decision making via **Local Calibration Error (LCE)**
- ✅ Neuro-symbolic integration of DL models and LLM reasoning
- ✅ Multi-agent clinical reasoning (Screener–Sentinel–Arbiter)
- ✅ Deterministic LLM outputs (low temperature inference)
- ✅ EHR-compatible structured output generation
- ✅ Human-in-the-loop deferral for uncertain cases
- ✅ Safety-first design to mitigate hallucinations

---

## 📊 Decision Pipeline

1. Longitudinal microbiome data → Deep learning models
2. Neural models output:
   - Risk scores
   - SHAP explanations
   - Calibration signals (LCE)
3. Multi-agent reasoning layer processes signals
4. LCE gating determines:
   - ✔ High/Low → Structured clinical decision
   - ❗ High uncertainty → Physician review

---

## 🧪 Installation

```bash
git clone https://github.com/mlresearcher81/CalibraMed.git
cd CalibraMed
pip install -r requirements.txt
```
---

## 🔑 Llama 3.1 Access Requirements (Crucial Step)

Because Meta's **Llama-3.1-8B-Instruct** is a gated model, the weights cannot be downloaded anonymously. To successfully run the notebook without encountering authentication errors, you must complete the following security and registration steps before execution:

### 1. Request Meta Approval
* Create or log into a [Hugging Face](https://huggingface.co/) account.
* Navigate to the official [Meta-Llama-3.1-8B-Instruct model card](https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct).
* Fill out the required access request form and agree to Meta's community license. Approval is typically granted automatically within a few minutes to a few hours.

### 2. Generate an Access Token
* Once your account is granted access, navigate to your Hugging Face **Settings** > **Access Tokens**.
* Generate a new token with **Read** permissions. Treat this token as a secure password.

### 3. Configure Google Colab Secrets
To ensure security, the pipeline does not hardcode API keys into the script. Instead, it securely pulls the key using Colab's `userdata` API.
* Open the `Final_Neuro_Symbolic_Pipeline_Perfect.ipynb` notebook in Google Colab.
* Click the **🔑 Secrets** icon (the key symbol) in the left-hand sidebar.
* Click **Add new secret**. 
* Set the Name to `HF_TOKEN` and paste your Hugging Face Read token into the Value field.
* Toggle the **Notebook access** switch to the "on" position so the code can read the token during initialization.
