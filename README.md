# Multimodal Colon Cancer Detection (2 Type Classification)

## Proposed Approach

The proposed framework performs multimodal colon cancer classification by integrating colonoscopy videos, histopathology images, and IHC biomarker information from the VIM-POLYP dataset. The video branch utilizes a pretrained **VideoMAE-S** encoder to extract temporal representations from sampled video frames, while the pathology branch employs a **Frozen DINOv2** encoder to obtain robust visual features from tissue patches. Clinical and biomarker information is processed using a **TabTransformer** to learn structured feature embeddings.

The extracted video and pathology representations are adaptively modulated using a **Biomarker-Guided Gated Fusion** mechanism, where biomarker embeddings dynamically regulate the importance of each visual modality. The gated multimodal features are subsequently integrated using a **Multimodal Fusion Layer (Transformer + MLP)** to generate a unified patient representation. Finally, a confidence estimation module and a classification head predict one of three diagnostic categories:

* Non-Neoplastic
* Neoplastic
* Carcinom

---

## Files

* **proposed_model.ipynb**
  Complete implementation of the proposed multimodal framework integrating VideoMAE-S, Frozen DINOv2, TabTransformer, Biomarker-Guided Gated Fusion, and Multimodal Fusion.

* **proposed_model_architecture.png**
  Visual illustration of the complete proposed architecture.

---

## First, Run

```bash
pip install -r requirements.txt
```

---

## Dataset

The experiments are conducted using the **VIM-POLYP Multimodal Colon Cancer Dataset**.

The dataset is publicly available at:

```bash
https://tinyurl.com/yemn5xv4
```

Update the dataset paths inside **proposed_model.ipynb** before execution.

---

## Train

### Proposed Multimodal Colon Cancer Classification Model

```bash
Open and run:

proposed_model.ipynb
```

---

## Model Components

### Video Branch

* Colonoscopy Video (AVI)
* Frame Sampling (1 fps)
* VideoMAE-S (Pre-trained & Frozen)
* Temporal Attention Pooling
* 512-D Video Feature

### Histopathology Branch

* Histopathology Images (TIFF)
* Tissue Patch Selection
* Frozen DINOv2 (Pre-trained & Frozen)
* Attention Pooling Across Patches
* 512-D Pathology Feature

### Biomarker Branch

* IHC Biomarkers
* Data Cleaning
* TabTransformer
* 128-D Biomarker Embedding

### Multimodal Fusion

* Biomarker-Guided Gated Fusion
* Multimodal Fusion Layer (Transformer + MLP)
* Unified Patient Embedding (1024-D)
* Confidence Estimation Module
* Classification Head (MLP + Softmax)

---

## Output Classes

* Non-Neoplastic
* Neoplastic
