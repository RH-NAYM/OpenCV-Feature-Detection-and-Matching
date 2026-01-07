# 💡 Visual Feature Matching & Debugging Toolkit (OpenCV + LightGlue)

[![main branch](https://img.shields.io/badge/branch-main-red?style=flat&logo=git&logoColor=white)](https://github.com/RH-NAYM/OpenCV-Feature-Detection-and-Matching/tree/main)

<p align="center">
  <a href="https://opencv.org/" target="_blank">
    <img src="https://img.shields.io/badge/OpenCV-Computer%20Vision-green?logo=opencv&logoColor=white" alt="OpenCV">
  </a>
  <a href="https://pytorch.org/" target="_blank">
    <img src="https://img.shields.io/badge/PyTorch-Deep%20Learning-red?logo=pytorch&logoColor=white" alt="PyTorch">
  </a>
  <a href="https://github.com/cvg/LightGlue" target="_blank">
    <img src="https://img.shields.io/badge/LightGlue-Feature%20Matching-purple" alt="LightGlue">
  </a>
  <a href="https://jupyter.org/" target="_blank">
    <img src="https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white" alt="Jupyter">
  </a>
</p>

## Overview

This project is a **production-grade visual feature matching and debugging toolkit** built on top of **OpenCV + SuperPoint + LightGlue**.

Unlike simple demo notebooks, this repository focuses on **failure analysis**:

- Why matches fail
- Where geometric constraints break
- How to visually debug correspondence collapse

It is designed for computer vision engineers working on:

- Image registration
- Homography / pose estimation
- AR / SLAM / SfM pipelines
- Low-texture or illumination-variant scenes

## Project Structure

```text
.
├── Feature-Matching-Debugging.ipynb     # Main interactive notebook
├── README.md                            # This file
├── requirements.txt                     # Dependencies (CUDA-locked)
├── data/                                # Example image pairs
│   ├── img1.jpg
│   └── img2.jpg
└── tools/
    ├── visualization.py                 # Visual debugging utilities
    ├── geometry.py                      # Homography & epipolar checks
    └── metrics.py                       # Match quality scoring
```

---

# 📋 Table of Contents (Notebook Sections)

```bash
Introduction to Local Feature Matching
Classical vs Learned Features (ORB vs SuperPoint)
LightGlue Matching Pipeline
Raw Match Visualization
🔥 Visual Debugging Toolkit for Match Failure
Match Confidence & Score Distribution
Geometric Verification (RANSAC / Homography)
Failure Modes & Root Cause Analysis
Robust Matching Strategies
```

---

# 🧠 What You’ll Learn

Feature Matching Intuition

Keypoints are hypotheses, not ground truth
Matches must satisfy appearance + geometry
Even deep matchers fail under domain shift

Common Failure Modes

Repetitive textures
Motion blur
Extreme viewpoint changes
Illumination collapse
Scale mismatch

Geometry Matters
A set of matches without geometric consistency is often useless.
Homography constraint:
x′ ∼ Hx
RANSAC filters out appearance-only hallucinations.
Visual Debugging Toolkit (Core Feature)
This toolkit emphasizes visual failure analysis, not just numerical metrics.
Features

Match Density Heatmap
→ Reveals spatial collapse of correspondences
Confidence-Colored Matches
→ Green = high confidence, Red = likely hallucinations
Inlier vs Outlier Split
→ RANSAC inliers (solid lines) vs rejected matches (faded)
Local Patch Inspection
→ Crop patches around failed matches for visual comparison
Degeneracy Warnings
→ Detects collinear keypoints or single-plane dominance

These tools help you understand why a matcher fails instead of just seeing that it failed.


---

# 🛠️ Technologies Used

Python 3.10+
OpenCV 4.8+
PyTorch (with CUDA support)
SuperPoint
LightGlue
NumPy
Matplotlib
Jupyter Notebook

---

# 📦 Installation (CUDA Locked)

```bash
# 1. Install PyTorch with CUDA (adjust version if needed)
pip install torch==2.1.0+cu121 torchvision==0.16.0+cu121 \
  --index-url https://download.pytorch.org/whl/cu121

# 2. Install remaining dependencies
pip install -r requirements.txt
```
Important:
Make sure your CUDA version matches your PyTorch build. A mismatch often leads to silent failures.



⚠️ CUDA mismatch = silent failure. Match your driver.

---

# 🚀 How to Run

```bash
jupyter notebook Feature-Matching-Debugging.ipynb
```
Drop your own image pairs into the data/ folder
Run cells sequentially
Use the debugging tools to analyze failures visually

Key Takeaways

More matches ≠ better matches
Geometry is the final judge
Visualization beats metrics during debugging
Even learned matchers need sanity checks

Real-World Applications

AR marker stability
Multi-view reconstruction
Retail shelf alignment
Drone image stitching
Medical image registration

Contributing
This repository is intentionally engineering-focused.
Pull requests are welcome for:

New failure visualization techniques
Additional geometric constraints
Performance profiling tools
Support for more matchers / extractors

