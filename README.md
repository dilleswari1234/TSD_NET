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
It includes:
- **Weak labels** (clip-level)  
- **Strong+ labels** (strong temporal annotations with extra synthetic data)  

Dataset split:
- **Train**: Synthetic + real recordings with strong labels  
- **Validation**: Subset of strongly labeled clips  
- **Test**: Real-life audio recordings  

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
