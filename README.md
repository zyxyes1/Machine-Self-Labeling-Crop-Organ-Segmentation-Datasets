# Machine-Self-Labeling-Crop-Organ-Segmentation-Datasets


## Introduction

This repository hosts four annotated datasets for cross-domain crop organ semantic segmentation, released as part of the **Machine Self-Labeling (MSL)** framework for zero-human-annotation plant organ segmentation. The datasets cover two crop organs — **wheat spike** and **maize tassel** — under different imaging conditions, annotation sources, and labeling qualities. They are intended for research on cross-domain transfer, self-training, and generalization evaluation in agricultural computer vision.

The MSL framework addresses a critical bottleneck in agricultural AI: pixel-level annotation of crop organs requires expert knowledge and incurs prohibitive labor costs. By leveraging labeled source-domain data (rice panicle) and unlabeled target-domain images, MSL enables machines to autonomously learn to annotate unseen plant organs — without any human annotation in the target domain.

**Important note on annotation sources:**  
- For the **FIP-1.0** subset, the original images are from Roth et al. (2025), but the 100 pixel-level ground-truth masks were **manually annotated by the authors of this release**.  
- For the **MTC** subset, the original images are from Lu et al. (2017), but the 303 pixel-level ground-truth masks were **manually annotated by the authors of this release**.  
- For the **MrMT** subset, the 1,000 images are **512×512 image patches randomly cropped from the MrMT dataset** (Yu et al., 2023). This subset has **no pixel-level ground truth**.  
- The **maize-Redmi** subset was **captured by the authors using a Redmi Note 12 Pro smartphone** and **manually annotated** for maize tassel. It serves as a strict hold-out test set.

## Dataset Overview

| Dataset | Crop Organ | Pixel-Level GT | Images | Description | Purpose | Reference |
|---|---|---|---|---|---|---|
| FIP-1.0 | Wheat spike | Yes | 100 | 100 images randomly selected from FIP-1.0 (Roth et al., 2025) and manually annotated by the authors | Wheat generalization test | Roth et al., 2025 (images); this work (GT) |
| MTC | Maize tassel | Yes | 303 | 303 images randomly selected from MTC-maize (Lu et al., 2017) and manually annotated by the authors | Maize target domain; original images for self-labeling, GT for final comparison only | Lu et al., 2017 (images); this work (GT) |
| MrMT | Maize tassel | No | 1,000 | 1,000 512×512 image patches randomly cropped from the MrMT dataset | Maize unlabeled target domain for self-training | Yu et al., 2023 |
| maize-Redmi | Maize tassel | Yes | 61 | Strict hold-out dataset captured by the authors using a Redmi Note 12 Pro and manually annotated | Maize generalization test | This work (Redmi cellphone) |

## Dataset Details

### FIP-1.0 (Wheat Spike)
- **Organ**: Wheat spike (*Triticum aestivum*)
- **Annotation**: Pixel-level manual ground truth by the authors of this release
- **Image count**: 100
- **Source**: Randomly sampled from the FIP-1.0 dataset (Roth et al., 2025)
- **Purpose**: Strict hold-out test set for evaluating cross-dataset generalization capability
- **Note**: This dataset is used **only for testing** and never participates in training, early stopping, model selection, or hyperparameter tuning

### MTC (Maize Tassel)
- **Organ**: Maize tassel (*Zea mays*)
- **Annotation**: Pixel-level manual ground truth by the authors of this release
- **Image count**: 303
- **Source**: Randomly sampled from the MTC-maize dataset (Lu et al., 2017)
- **Purpose**: Maize target domain for self-labeling; original images used for training, GT used only for final baseline comparison
- **Note**: In the MSL pipeline, only original images are used as unlabeled target-domain images. Ground truth does **not** participate in training, screening, or model selection

### MrMT (Maize Tassel, Unlabeled)
- **Organ**: Maize tassel
- **Annotation**: No pixel-level ground truth
- **Image count**: 1,000
- **Source**: 1,000 512×512 image patches randomly cropped from the MrMT dataset (Yu et al., 2023)
- **Purpose**: Maize unlabeled target domain for self-training
- **Note**: Provides diverse maize tassel morphology under different imaging conditions, backgrounds, and variety distributions

### maize-Redmi (Maize Tassel, Strict Hold-out)
- **Organ**: Maize tassel
- **Annotation**: Pixel-level manual ground truth by the authors of this release
- **Image count**: 61
- **Source**: Captured by the authors using a Redmi Note 12 Pro smartphone
- **Purpose**: Strict hold-out test set for evaluating cross-dataset generalization capability
- **Note**: This dataset is used **only for testing** and never participates in training, early stopping, model selection, or hyperparameter tuning

## File Structure
MSL-Crop-Organ-Segmentation-Datasets/

├── README.md

├── LICENSE

├── CITATION.cff

└── data/

├── FIP-1.0.zip # Wheat spike, 100 images + GT

├── MTC.zip # Maize tassel, 303 images + GT

├── MrMT.zip # Maize tassel, 1,000 images (no GT)

└── maize-Redmi.zip # Maize tassel, 61 images + GT
## Download

All datasets are available as ZIP archives under the **[Releases](https://github.com/YOUR_USERNAME/MSL-Crop-Organ-Segmentation-Datasets/releases)** section.

| Dataset | File | Size | Download |
|---|---|---|---|
| FIP-1.0 | `FIP-1.0.zip` | ~52.9 MB | [Download](https://github.com/YOUR_USERNAME/MSL-Crop-Organ-Segmentation-Datasets/releases/download/v1.0.0/FIP-1.0.zip) |
| MTC | `MTC.zip` | ~120.7 MB | [Download](https://github.com/YOUR_USERNAME/MSL-Crop-Organ-Segmentation-Datasets/releases/download/v1.0.0/MTC.zip) |
| MrMT | `MrMT.zip` | ~100 MB | [Download](https://github.com/YOUR_USERNAME/MSL-Crop-Organ-Segmentation-Datasets/releases/download/v1.0.0/MrMT.zip) |
| maize-Redmi | `maize-Redmi.zip` | ~50 MB | [Download](https://github.com/YOUR_USERNAME/MSL-Crop-Organ-Segmentation-Datasets/releases/download/v1.0.0/maize-Redmi.zip) |

## Usage

### Data Format

Each ZIP archive contains:
- `images/` — original RGB images (`.jpg` or `.png`)
- `masks/` — pixel-level ground truth masks (`.png`), where `0` = background and `255` (or `1`) = foreground

For datasets **without** ground truth (MrMT), only the `images/` folder is provided.

### Recommended Workflow

1. Download the desired datasets from the Releases page
2. Extract the ZIP archives
3. Use the MSL framework (code available at [MSL-Code-Repository]) for:
   - Self-labeling on unlabeled target domains (MrMT)
   - Cross-domain evaluation on hold-out sets (FIP-1.0, maize-Redmi)
   - Baseline comparison with human GT (MTC)


### References

    Roth L, Boss M, Kirchgessner N, et al. The FIP 1.0 Data Set: highly resolved annotated image time series of 4,000 wheat plots grown in 6 years[J]. GigaScience, 2025, 14: giaf051.

    Lu, H., Cao, Z., Xiao, Y., Zhuang, B., & Shen, C. (2017). TasselNet: counting maize tassels in the wild via local counts regression network. Plant methods, 13(1), 79.

    Yu, Z., Ye, J., Li, C., Zhou, H., & Li, X. (2023). TasselLFANet: a novel lightweight multi-branch feature aggregation neural network for high-throughput image-based maize tassels detection and counting. Frontiers in Plant Science, 14, 1158940.

    
