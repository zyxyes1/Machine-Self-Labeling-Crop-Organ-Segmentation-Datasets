# Machine-Self-Labeling-Crop-Organ-Segmentation-Datasets

## Introduction

This repository hosts four annotated datasets for cross-domain crop organ semantic segmentation, released as part of the **Machine Self-Labeling (MSL)** framework for zero-human-annotation plant organ segmentation. The datasets cover two crop organs (wheat spike, maize tassel) across different imaging conditions, annotation qualities, and labeling sources, enabling research on cross-domain transfer, self-training, and generalization evaluation.

The MSL framework addresses a critical bottleneck in agricultural AI: pixel-level annotation of crop organs requires expert knowledge and incurs prohibitive labor costs. By leveraging labeled source-domain data (rice panicle) and unlabeled target-domain images, MSL enables machines to autonomously learn to annotate unseen plant organs — without any human annotation in the target domain.

## Dataset Overview

| Dataset | Crop Organ | Pixel-Level GT | Images | Description | Purpose | Reference |
|---|---|---|---|---|---|---|
| FIP-1.0 | Wheat spike | Yes | 100 | 100 images randomly selected from FIP-1.0 with manual wheat spike annotation | Wheat generalization test | Roth et al., 2025 |
| MTC | Maize tassel | Yes | 303 | 303 images randomly selected from MTC-maize with manual maize tassel annotation | Maize target domain; original images for self-labeling, GT for final comparison only | Lu et al., 2017 |
| MrMT | Maize tassel | No | 1,000 | 1,000 images randomly selected for self-training | Maize unlabeled target domain | Yu et al., 2023 |
| maize-Redmi | Maize tassel | Yes | 61 | Strict hold-out dataset captured with Redmi Note 12 Pro and manually annotated | Maize generalization test | This work (Redmi cellphone) |

## Dataset Details

### FIP-1.0 (Wheat Spike)
- **Organ**: Wheat spike (Triticum aestivum)
- **Annotation**: Pixel-level manual ground truth
- **Image count**: 100
- **Source**: Randomly sampled from the FIP-1.0 dataset
- **Purpose**: Strict hold-out test set for evaluating cross-dataset generalization capability
- **Note**: This dataset is used **only for testing** and never participates in training, early stopping, model selection, or hyperparameter tuning

### MTC (Maize Tassel)
- **Organ**: Maize tassel (Zea mays)
- **Annotation**: Pixel-level manual ground truth
- **Image count**: 303
- **Source**: Randomly sampled from the MTC-maize dataset
- **Purpose**: Maize target domain for self-labeling; original images used for training, GT used only for final baseline comparison
- **Note**: In the MSL pipeline, only original images are used as unlabeled target-domain images. Ground truth does **not** participate in training, screening, or model selection

### MrMT (Maize Tassel, Unlabeled)
- **Organ**: Maize tassel
- **Annotation**: No pixel-level ground truth
- **Image count**: 1,000
- **Source**: Randomly selected from the MrMT-512 dataset (seed=2025 for reproducibility)
- **Purpose**: Maize unlabeled target domain for self-training
- **Note**: Provides diverse maize tassel morphology under different imaging conditions, backgrounds, and variety distributions

### maize-Redmi (Maize Tassel, Strict Hold-out)
- **Organ**: Maize tassel
- **Annotation**: Pixel-level manual ground truth
- **Image count**: 61
- **Source**: Captured by the authors using a Redmi Note 12 Pro smartphone
- **Purpose**: Strict hold-out test set for evaluating cross-dataset generalization capability
- **Note**: This dataset is used **only for testing** and never participates in training, early stopping, model selection, or hyperparameter tuning

## File Structure
