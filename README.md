# Food Product Recognition

## Introduction
This project explores computer vision-based object detection techniques to identify food products on store shelves. We employ keypoint detection for single-instance recognition and combine keypoint and edge detection for multiple-instance detection.

### Image Preprocessing
Before detection, images undergo a denoising process. For instance:  
![Denoising Example](https://github.com/user-attachments/assets/5c8b0ffe-5ec8-4e1e-a68a-ae21e4a7cd30)

## Detection Approaches

### Single-Instance Detection
We perform feature-based detection without deep learning using the following steps:
1. **Feature Extraction & Matching**: SIFT is used for robust keypoint detection, and FLANN ensures efficient high-dimensional matching.
2. **Refinement & Localization**: Lowe's Ratio Test filters ambiguous matches, and RANSAC-based homography ensures accurate localization.
3. **Optional Validation**: ZNCC improves robustness but can be skipped when a sufficient number of matches is detected. Inspired by the Canny hysteresis algorithm, two thresholds determine if ZNCC is needed.

Results:  
![Single-Instance Detection](https://github.com/user-attachments/assets/c1ff490c-183e-4fca-950b-a71cb0d128a5)

### Multiple-Instance Detection
The same method is applied, with an additional step using the Hough Transform to detect long vertical dividers between milk cartons for scene segmentation. For instance:

![Hough Transform Example](https://github.com/user-attachments/assets/8c5c34d1-cfa9-4e0c-a9ee-ae36bb53ba33)

Results:  
![Multiple-Instance Detection](https://github.com/user-attachments/assets/ea7f0c8d-1c9f-4b52-9af6-b2497e3aaeb9)
