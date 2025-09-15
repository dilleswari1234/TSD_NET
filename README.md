# 🎧 A Unified Audio Encoder Framework for Target Sound Detection(TSD)

## 📌 Overview

This is the task of determining whether a target sound occurs within an audio mixture.  
This repository provides an implementation of TSD using the **Strong and Strong+ Dataset**, which includes temporally strong labels and additional negative samples for realistic evaluation.

Our approach leverages a hybrid architecture where **frame-level** and **clip-level** embeddings are extracted and fused through **Bi-Directional GRU (Bi-GRU)** layers, followed by classification layers for sound event detection.

### 🔑 Key Features
- ✅ Support for **Strong and Strong+ dataset** with strong temporal annotations and negative samples  
- 🎵 Extraction of both **Frame-Level** and **Clip-Level** embeddings  
- 🧩 Flexible backbone: **CNN14** and **ConvNeXt** feature extractors  
- 📊 Evaluation with multiple metrics: **F1-score**, **Accuracy**, and **Error Rate**  


## 📂 Datasets

We use the **Strong and Strong+ dataset** from [DCASE Challenge](https://arxiv.org/pdf/2112.10153).  

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

To better evaluate the model in realistic conditions, we construct the **Urban TSD Strong+** dataset by introducing **negative samples**:

- **Negative samples** are mixture–reference pairs where the **target sound does not occur** in the mixture.  
- For generation, we randomly select a **reference audio** from UrbanSound8K whose events are **absent** in the chosen URBAN-SED mixture.  
- Since the target class is not present, the **timestamp labels are all set to 0**.  

This setup simulates real-world scenarios where a target sound may be missing, enabling robust training and evaluation of TSD models under both **positive and negative query conditions**.

These dataset variants provide a benchmark for assessing TSD models in diverse conditions.

You can download the datasets here:  
- [URBAN-SED](https://zenodo.org/records/1324404)  
- [UrbanSound8K](https://urbansounddataset.weebly.com/urbansound8k.html)  

---
