# 🎧 Target Sound Detection with Strong+ Dataset

This repository contains the implementation of **Target Sound Detection**.
The model is trained and evaluated on the **Strong+ dataset**, which provides temporally strong labels suitable for supervised sound event detection tasks.

---

## 📌 Overview

Target Sound Detection aims to identify whether a target sound occurs in an audio mixture.  
Our **(MODEL)** architecture leverages **frame-level** and **clip-level** representations, fused through recurrent layers (BI-GRU), followed by classification layers for event detection.

**Key features:**
- Support for **Strong+ dataset** (with strong temporal annotations).  
- Extracts both **frame-level** and **clip-level** embeddings.  
- Flexible architecture supporting CNN14 and ConvNeXt feature extractors.  
- Evaluation metrics: **F1-score**, **Accuracy**, and **Error Rate**.

---

## 📂 Dataset

We use the **Strong+ dataset** from [DCASE Challenge](https://dcase.community/challenge2023/task-sound-event-detection-in-domestic-environments).  

## 📂 Datasets

We conduct experiments on **URBAN-SED** and **UrbanSound8K**, along with task-specific variants designed for **Target Sound Detection (TSD):**

- **URBAN-SED**  
  A synthetic dataset of **10,000 ten-second soundscapes** containing 1–9 events from 10 urban sound classes.  
  - Split: 6,000 training, 2,000 validation, 2,000 test examples  
  - Provides **precise frame-level annotations** for supervised sound event detection.

- **UrbanSound8K**  
  A dataset of **8,732 short, isolated clips** from the same 10 urban classes.  
  - Used as **reference audio** for model conditioning in TSD tasks.

---

### 🔹 Urban TSD Variants

We construct two **task-specific datasets** by combining URBAN-SED (as mixtures) and UrbanSound8K (as reference audio):

- **Urban TSD Strong**  
  - Retains **strong labels with timestamps** from URBAN-SED.  
  - Enables evaluation under **positive query conditions**, where the reference class is present in the mixture.

- **Urban TSD Strong+**  
  - Extends the **Strong** setup by adding **negative samples**, where the reference class is absent.  
  - Allows evaluation under both **positive and negative queries**, making the task more realistic and challenging.

These dataset variants provide a benchmark for assessing TSD models in diverse conditions.

You can download the dataset [here](https://zenodo.org/record/4660670).

---

## ⚙️ Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/your-username/TSD-Net.git
cd TSD-Net

# Create environment (Python 3.9+ recommended)
conda create -n tsdnet python=3.9
conda activate tsdnet

# Install dependencies
pip install -r requirements.txt
