# 🔬 MSPE-DeiT: Multimodal Framework for Skin Cancer Diagnosis

<div align="center">

![Status](https://img.shields.io/badge/Status-Under%20Review-yellow?style=for-the-badge)
![Venue](https://img.shields.io/badge/Venue-IEEE%20Access-blue?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Medical%20Imaging-green?style=for-the-badge)
![Institution](https://img.shields.io/badge/Institution-PEC%20Chandigarh-red?style=for-the-badge)

**A Vision Transformer based Multimodal Deep Learning Framework for Skin Cancer Diagnosis**

*Punjab Engineering College (Deemed to be University), Chandigarh, India*

</div>

---

## 📌 Overview

Skin cancer is one of the most prevalent cancers worldwide, with melanoma being its most fatal form. Early and accurate detection is critical for improving patient outcomes. This work proposes a **multimodal deep learning framework** that goes beyond conventional single-modality approaches by jointly leveraging:

- 🖼️ **Dermoscopic Images** — high-resolution lesion imagery
- 📷 **3D Total Body Photography (3D-TBP) Scans** — smartphone-quality whole-body lesion captures
- 📋 **Patient Clinical Metadata** — structured patient information and engineered lesion features

By combining these three modalities through an ensemble strategy, the framework achieves robust generalization across diverse patient populations.

---

## ✨ Highlights

- 🧠 **MSPE-DeiT** — a novel Modality-Specific Patch Embedding Data-efficient image Transformer that handles heterogeneous image modalities through dedicated embedding layers and a shared encoder backbone
- 📊 **Clinical Data Pipeline** — XGBoost and a Bayesian-optimized ANN with skip connections for structured metadata classification
- 🤝 **Soft-Voting Ensemble** — combines complementary predictions from all three branches for maximum robustness
- 📁 **Large-scale Evaluation** — trained and tested on ~480k images spanning ISIC 2016 through ISIC 2024
- ⚡ **Computationally Efficient** — designed with real-world clinical deployment in mind

---

## 📂 Dataset

This work uses publicly available datasets from the **International Skin Imaging Collaboration (ISIC)**:

| Dataset | Type | Link |
|---|---|---|
| ISIC 2016 | Dermoscopic | [ISIC Archive](https://www.isic-archive.com/) |
| ISIC 2017 | Dermoscopic | [ISIC Archive](https://www.isic-archive.com/) |
| ISIC 2018 / HAM10000 | Dermoscopic | [ISIC Archive](https://www.isic-archive.com/) |
| ISIC 2019 / BCN20000 | Dermoscopic | [ISIC Archive](https://www.isic-archive.com/) |
| ISIC 2020 | Dermoscopic | [ISIC Archive](https://www.isic-archive.com/) |
| ISIC 2024 | 3D-TBP + Clinical | [Kaggle](https://www.kaggle.com/competitions/isic-2024-challenge) |

> All datasets are publicly available. Download them from the links above before running the code.

---

## 🚀 Getting Started

> Full setup instructions will be added upon paper acceptance. A preview is provided below.

### Prerequisites

```bash
Python >= 3.8
PyTorch >= 2.0
CUDA >= 11.8 (recommended)
```

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/MSPE-DeiT.git
cd MSPE-DeiT

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Quick Start

```bash
# Preprocessing
python preprocess.py --data_dir /path/to/isic_datasets

# Training
python train.py --config configs/mspe_deit.yaml

# Evaluation
python evaluate.py --checkpoint checkpoints/best_model.pth
```

> ⚙️ Detailed configuration files, pretrained weights, and full pipeline scripts will be released post-publication.

---

## 📈 Results

Our ensemble framework achieves strong performance on a held-out test set of ~80k samples from ISIC 2024:

| Model | Accuracy | AUROC | Specificity | Sensitivity |
|---|---|---|---|---|
| MSPE-DeiT (Image only) | 97.49% | 96.54% | 88.89% | 96.10% |
| XGBoost (Clinical only) | 89.81% | 95.20% | 89.81% | 89.87% |
| ANN (Clinical only) | 89.06% | 89.68% | 87.09% | 75.95% |
| **Ensemble (Proposed)** | **93.11%** | **94.81%** | **93.12%** | **84.81%** |

> The ensemble achieves the best overall **balance** across all metrics, particularly addressing the extreme class imbalance (1000:1) present in the ISIC 2024 dataset.

---

## 👥 Authors

<table>
<tr>
<td align="center"><b>Uttam Mittal</b><br>PEC Chandigarh<br></td>
<td align="center"><b>Siddhesh Varpe</b><br>PEC Chandigarh</td>
<td align="center"><b>Aaditya Sharma</b><br>PEC Chandigarh</td>
<td align="center"><b>Tamanna Sood</b><br>Roundglass Living</td>
</tr>
<tr>
<td align="center"><b>Padmavati Khandnor</b><br>PEC Chandigarh</td>
<td align="center"><b>Sarthak Garg</b><br>PEC Chandigarh</td>
<td align="center"><b>Sudesh Rani</b><br>PEC Chandigarh</td>
<td align="center"><b>Mayank Gupta</b><br>PEC Chandigarh</td>
</tr>
<tr>
<td align="center"><b>Lilia El Amraoui</b><br>Princess Nourah University, Saudi Arabia</td>
<td align="center"><b>Kaïs Ouni</b><br>University of Carthage, Tunisia</td>
<td align="center" colspan="2"><b>Adnen El Amraoui</b><br>University of Artois, France</td>
</tr>
</table>

---

## 📄 Citation

If you find this work useful, please consider citing it. BibTeX will be available upon publication.

```bibtex
@article{mittal2025mspedeit,
  title     = {MSPE-DeiT: A Vision Transformer based Multimodal Framework for Skin Cancer Diagnosis},
  author    = {Mittal, Uttam and Varpe, Siddhesh and Sharma, Aaditya and Sood, Tamanna and
               Khandnor, Padmavati and Garg, Sarthak and Rani, Sudesh and Gupta, Mayank and
               El Amraoui, Lilia and Ouni, Kais and El Amraoui, Adnen},
  journal   = {IEEE Access},
  year      = {2025},
  note      = {Under Review}
}
```

---

## 🙏 Acknowledgements

This research was supported by **Princess Nourah bint Abdulrahman University Researchers Supporting Project** (PNURSP2026R831), Riyadh, Saudi Arabia.

We also thank the **ISIC** for making their benchmark datasets publicly accessible, which made this research possible.

---

## 📬 Contact

For queries regarding the paper or code, feel free to reach out:

- **Uttam Mittal** — hemanthmittal02@gmail.com
- **Siddhesh Varpe** — siddheshsanjayvarpe.mt24cse@pec.edu.in

---

<div align="center">

⭐ **Star this repo** to stay updated when the full code is released!

![Visitors](https://visitor-badge.laobi.icu/badge?page_id=your-username.MSPE-DeiT)

</div>
