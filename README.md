# Food Product Recognition

## Introduction
This project explores computer vision-based object detection techniques for identifying food products on store shelves without deep learning. We utilize **keypoint detection** for single-instance recognition and **keypoint + edge detection** for multiple-instance detection.

## Image Preprocessing
Before detection, images undergo a denoising process to enhance feature extraction. Example:  
![Denoising Example](https://github.com/user-attachments/assets/5c8b0ffe-5ec8-4e1e-a68a-ae21e4a7cd30)

---

## Detection Approaches

### Single-Instance Detection
Feature-based detection is performed without deep learning using the following steps:

1. **Feature Extraction & Matching**  
   - **SIFT** is used for robust keypoint detection.  
   - **FLANN** ensures efficient high-dimensional feature matching.

2. **Refinement & Localization**  
   - **Lowe's Ratio Test** filters ambiguous matches.  
   - **RANSAC-based homography** ensures precise localization.

3. **Optional Validation**  
   - **ZNCC (Zero-mean Normalized Cross-Correlation)** enhances robustness but is optional.  
   - Inspired by the **Canny hysteresis algorithm**, we use two thresholds to determine if ZNCC validation is needed.

#### Results  
![Single-Instance Detection](https://github.com/user-attachments/assets/c1ff490c-183e-4fca-950b-a71cb0d128a5)

---

### Multiple-Instance Detection
For multiple-instance detection, we apply the same keypoint-based method with an additional **scene segmentation** step:

1. **Edge-Based Segmentation**  
   - The **Hough Transform** detects long vertical dividers (e.g., between milk cartons).  
   - These dividers segment the scene to isolate individual products.

#### Example  
![Hough Transform Example](https://github.com/user-attachments/assets/8c5c34d1-cfa9-4e0c-a9ee-ae36bb53ba33)

#### Results  
![Multiple-Instance Detection](https://github.com/user-attachments/assets/ea7f0c8d-1c9f-4b52-9af6-b2497e3aaeb9)
