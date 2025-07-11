# Fawry AI Rising Gen: Competition Showcase

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=pytorch&logoColor=white)
![YOLOv8](https://img.shields.io/badge/YOLOv8-00FFFF.svg?style=for-the-badge&logo=yolo&logoColor=black)
![ByteTrack](https://img.shields.io/badge/Tracking-ByteTrack-blue.svg?style=for-the-badge)
![ArcFace](https://img.shields.io/badge/Metric%20Learning-ArcFace-orange.svg?style=for-the-badge)

This repository serves as a central showcase for our submission to the **Fawry AI Rising Gen Competition**. Our team successfully tackled two distinct computer vision challenges, leading us to achieve a **Top 8 finish out of 30 competing teams**.

---

### 🏆 Achievement: Top 8 Finalist & Team

Here is a photo of our team certificate after qualifying for the finals. This accomplishment reflects our dedication to building effective, real-world AI solutions under competitive pressure.

**_--- Instructions for you ---_**
**To add your photo, first upload the image file to this GitHub repository.**
**Then, replace `URL_TO_YOUR_CERTIFICATE_PHOTO.jpg` below with the name of your uploaded image file.**

![Fawry Competition Certificate](https://github.com/MHamdyK/Fawry-AI-Rising-Gen-Showcase/blob/main/Fawry_Competition.jpeg?raw=true)

---

## Project Breakdown

The competition was divided into two core tasks. Below is a detailed breakdown of our approach for each, with links to their dedicated repositories.

### 1. Face Re-Identification System

This project aimed to build a robust face identification system for identifying employees from surveillance footage. Our solution leveraged deep metric learning to achieve high accuracy.

#### **Technical Approach & Key Features:**
*   **Backbone Model:** Fine-tuned an **InceptionResnetV1** model, pre-trained on the extensive **VGGFace2** dataset, to serve as a powerful feature extractor.
*   **Metric Learning with ArcFace:** Implemented a custom **`ArcMarginProduct`** layer (ArcFace). This additive angular margin loss function enhances class separability in the embedding space, which is crucial for distinguishing between a large number of identities.
*   **Training Strategy:** Employed the **AdamW optimizer** and a **`CosineAnnealingLR` scheduler** for stable and effective convergence, achieving **99.3% accuracy** on the training set.
*   **Inference Pipeline:**
    1.  Generated an "embedding gallery" by averaging the feature vectors for all images of each known individual.
    2.  For a given test image, its embedding was compared against the entire gallery using **cosine similarity**.
    3.  Identities were assigned based on the highest similarity score, provided it exceeded a confidence threshold of `0.8`.
*   **Data Augmentation:** Utilized a comprehensive set of transforms including `RandomResizedCrop`, `RandomHorizontalFlip`, and `ColorJitter` to build a more robust and generalizable model.

<br>

<p align="center">
  <a href="https://github.com/MHamdyK/ArcFace-ReID-pytorch">
    <img src="https://img.shields.io/badge/View%20Code-ArcFace--ReID--pytorch-2ea44f?style=for-the-badge&logo=github" alt="View Re-ID Code" />
  </a>
</p>

---

### 2. Real-Time Multi-Object Tracking (MOT)

This project involved delivering a high-performance pedestrian tracking pipeline for crowded scenes, focusing on both detection accuracy and data association robustness.

#### **Technical Approach & Key Features:**
*   **Detector:** Fine-tuned a **YOLOv8m** model on a large, unified dataset. This provided the high-quality detections essential for reliable tracking.
*   **Tracker:** Integrated the **ByteTrack** algorithm for data association. ByteTrack's key innovation is its two-stage matching process, which retains low-confidence detection boxes to recover objects during occlusion, significantly reducing fragmentation and improving tracking continuity (HOTA score).
*   **Unified Dataset Creation:**
    *   Combined data from the official **MOT17** dataset with the **Fawry competition-specific dataset**.
    *   Engineered a robust data preparation pipeline to convert annotations from MOT format to YOLO format, handling various edge cases and ensuring label consistency.
*   **Targeted Hyperparameter Tuning:**
    *   Optimized training with an **SGD optimizer** and **cosine learning rate decay**, which are proven to be highly effective for detection tasks.
    *   Set image size to `1184x1184` to improve the detection of small, distant pedestrians.
    *   Carefully selected augmentations (e.g., disabling `mixup` and `copy_paste`) to preserve the integrity of multi-object scenes.
*   **End-to-End Pipeline:** Developed a complete inference pipeline that takes raw video frames, runs detection and tracking, and generates a competition-standard submission file, including scripts for visualization and video creation.

<br>

<p align="center">
  <a href="https://github.com/MHamdyK/ByteYOLO-MOT">
    <img src="https://img.shields.io/badge/View%20Code-ByteYOLO--MOT-2ea44f?style=for-the-badge&logo=github" alt="View MOT Code" />
  </a>
</p>

---

### How to Run

For detailed setup and execution instructions, please refer to the `README.md` files within each of the individual project repositories linked above.

---

### License

This project is licensed under the MIT License. See the `LICENSE` file for details.````