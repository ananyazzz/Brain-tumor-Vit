<div align="center">

# 🧠 Brain Tumor MRI Classification
### *Vision Transformer (ViT) — Built from Scratch*

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)

<br/>

> **Classifying brain tumor MRI scans into 4 categories using a Vision Transformer (ViT) architecture — implemented entirely from scratch in PyTorch.**

<br/>

---

</div>

## 📌 Overview

This project applies **Vision Transformers (ViT)** to the task of **brain tumor classification** from MRI scans. Rather than relying on CNNs, the model splits each MRI image into fixed-size patches and processes them through a multi-head self-attention transformer — the same architecture that revolutionized NLP, now applied to medical imaging.

<br/>

## 🏷️ Tumor Classes

| Class | Description |
|-------|-------------|
| 🔴 **Glioma** | A tumor that starts in the glial cells of the brain |
| 🟠 **Meningioma** | Arises from the meninges surrounding the brain |
| 🟢 **No Tumor** | Healthy MRI scans with no tumor detected |
| 🔵 **Pituitary** | Tumor located in the pituitary gland |

<br/>

## 🏗️ Model Architecture

```
Input MRI (224×224×3)
        │
        ▼
 Patch Embedding (16×16 patches → 196 tokens)
        │
        ▼
 [CLS] Token + Positional Encoding
        │
        ▼
 ┌─────────────────────────┐
 │  Transformer Encoder ×6 │
 │  ┌───────────────────┐  │
 │  │ Multi-Head Attention│ │  ← 8 heads, Embed dim: 256
 │  │ (8 heads)         │  │
 │  ├───────────────────┤  │
 │  │  Feed Forward (MLP)│ │  ← MLP ratio: 4×
 │  └───────────────────┘  │
 └─────────────────────────┘
        │
        ▼
 Classification Head (MLP)
        │
        ▼
  4-Class Output (Softmax)
```

<br/>

## ⚙️ Configuration

| Hyperparameter | Value |
|---|---|
| Image Size | `224 × 224` |
| Patch Size | `16 × 16` |
| Batch Size | `32` |
| Epochs | `20` |
| Learning Rate | `3e-4` |
| Optimizer | AdamW |
| Weight Decay | `1e-4` |
| Embed Dimension | `256` |
| Transformer Depth | `6 layers` |
| Attention Heads | `8` |
| Dropout | `0.1` |

<br/>

## 🔬 Pipeline

```
📂 Dataset Loading
      ↓
📊 EDA & Class Distribution Analysis
      ↓
🔄 Image Preprocessing & Augmentation
      ↓
🏗️  ViT Model Definition (from scratch)
      ↓
🏋️  Training Loop (loss + accuracy tracking)
      ↓
📈 Evaluation (Confusion Matrix, F1, Accuracy)
      ↓
🖼️  Sample Predictions Visualization
```

<br/>

## 📦 Requirements

```bash
pip install torch torchvision timm matplotlib seaborn scikit-learn tqdm Pillow
```

| Package | Purpose |
|---|---|
| `torch` / `torchvision` | Model & data loading |
| `timm` | Pretrained ViT option |
| `scikit-learn` | Metrics (F1, confusion matrix) |
| `matplotlib` / `seaborn` | Visualization |
| `tqdm` | Training progress bars |

<br/>

## 🚀 Getting Started

**1. Clone the repository**
```bash
git clone https://github.com/ananyazzz/Brain-tumor-Vit.git
cd Brain-tumor-Vit
```

**2. Download the dataset**

Get the dataset from Kaggle → [Brain Tumor MRI Dataset](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)

Extract and set your `DATA_ROOT` path in the notebook configuration cell.

**3. Launch the notebook**
```bash
jupyter notebook brain_tumor_vit.ipynb
```

**4. Run all cells** — The notebook will train the ViT model and output metrics, plots, and sample predictions.

<br/>

## 📊 Results

The model is evaluated using:
- ✅ **Accuracy Score**
- ✅ **F1 Score** (macro-averaged)
- ✅ **Confusion Matrix**
- ✅ **Per-class Classification Report**

<br/>

## 📁 Project Structure

```
Brain-tumor-Vit/
│
├── brain_tumor_vit.ipynb   # Main notebook (full pipeline)
├── .gitignore              # Ignores checkpoints, DS_Store, etc.
└── README.md               # You are here!
```

<br/>

## 📚 Dataset

- **Source:** [Kaggle — Brain Tumor MRI Dataset](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)
- **Classes:** Glioma, Meningioma, No Tumor, Pituitary
- **Split:** Pre-divided into `Training/` and `Testing/` folders

<br/>

## 🧪 Why Vision Transformer?

Unlike CNNs that rely on local receptive fields, **ViTs capture global context** from the very first layer using self-attention. This makes them especially powerful for medical imaging, where subtle, spatially distant features can be diagnostically significant.

<br/>

## 🤝 Contributing

Pull requests are welcome! If you'd like to improve the model, add pretrained weights, or extend to other datasets, feel free to fork and submit a PR.

<br/>

<div align="center">

Made with ❤️ by [ananyazzz](https://github.com/ananyazzz)

⭐ *Star this repo if you found it helpful!*

</div>
