# CalibraMed: Calibration-Aware Neuro-Symbolic Clinical Decision Support

CalibraMed is a calibration-aware neuro-symbolic framework for translating longitudinal microbiome predictions into safe, structured clinical decisions. The system integrates deep learning models with Large Language Model (LLM)-based multi-agent reasoning under strict uncertainty constraints.

---

## 🧠 Overview

Modern microbiome models achieve strong predictive performance but remain difficult to interpret and deploy safely in clinical settings. CalibraMed addresses this challenge by introducing **Calibration-Gated Multi-Agent Arbitration (CMAA)**, a framework that constrains LLM reasoning using reliability signals derived from calibration metrics.

The system combines:

- A **deep learning predictive backbone** (Foundational Baseline)
- A **calibration layer** using Local Calibration Error (LCE)
- A **multi-agent reasoning engine** (LLM-based)
- A **safety-first decision policy** with human-in-the-loop deferral

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
git clone https://github.com/your-username/CalibraMed.git
cd CalibraMed
pip install -r requirements.txt
