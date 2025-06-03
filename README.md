# Brain Tumor Segmentation using 3D CNN

This project implements a lightweight 3D Convolutional Neural Network (CNN) for brain tumor segmentation using multi-modal MRI scans. The model is designed to achieve high accuracy while minimizing computational cost, making it suitable for real-time clinical applications.

---

## Project Objective

- Build an optimized 3D CNN architecture for brain tumor segmentation.
- Reduce FLOPs and parameter count without sacrificing segmentation accuracy.
- Utilize a high-performance data pipeline using TensorFlow's `tf.data` API for efficient data loading and augmentation.

---

## Dataset

- **Source**: BraTS 2021 Dataset
- **MRI Modalities**: T1, T1ce (contrast-enhanced), T2, and FLAIR
- **Format**: NIfTI `.nii.gz`
- **Split**: 417 training, 90 validation, 90 testing samples

---

## Preprocessing Steps

- Skull stripping
- Voxel size standardization
- Intensity normalization
- Resampling to `128x128x40`
- Integration of all four modalities
- Data augmentation (normalization, batching, prefetching)

---

## Model Summary

- Input shape: `(128, 128, 40, 4)`
- 3D Convolutional layers with ReLU and BatchNorm
- Dropout layer (rate: 0.3)
- Final softmax layer to classify each voxel into 5 categories (including tumor subregions and background)
- Implemented using TensorFlow and tf.keras

---

## Model Performance

| Metric               | Value     |
|----------------------|-----------|
| Accuracy             | 96.26%    |
| Segmentation Loss    | 0.1383    |
| Parameters           | 55,000    |
| FLOPS                | 110 KFLOPS |

---

## Comparative Analysis

| Paper / Model                    | Parameters | FLOPS         | Accuracy |
|----------------------------------|------------|---------------|----------|
| Batool et al. (MultiPath CNN)    | 861K       | 8.66 MFLOPS   | 92.5%    |
| MIM Al-Khuzaie (VGG16)           | 138M       | 15.5 GFLOPS   | 96%      |
| J Nodirov (3D U-Net)             | 31M        | 50–200 GFLOPS | 99.41%   |
| AS Ladkat (3D U-Net with Skip)   | 50–100M    | 500–1000 GFLOPS | 99%    |
| AM Nancy (VGG-19)                | 143.7M     | 19.6 GFLOPS   | 96%      |
| **Proposed Model (This Work)**   | **55K**    | **110 KFLOPS**| **96.26%** |

---

## Key Features

- Lightweight 3D CNN with fewer parameters and low computational load
- Uses four MRI modalities for better segmentation precision
- Fast training and high throughput with TensorFlow’s `tf.data` API
- Capable of distinguishing tumor from non-tumor regions reliably

---

## Limitations and Future Work

- Requires more diverse datasets to improve generalizability
- Clinical trials are necessary for medical-grade validation
- Future improvements:
  - Uncertainty quantification
  - Hardware-level optimization
  - Reduction of overfitting via regularization techniques

---

## Author

**Akshay S Kumar**  
M.Tech Data Science  
CHRIST (Deemed to be University), Bangalore  
Academic Year: 2024–2025

---

## References

A complete list of academic references is available in the [project report](./Akshay_S_Kumar_2467422_2MTDS_Project_Report.pdf).
