
# Dataset Description – Friends Actor Detection

## Overview

This dataset was manually constructed for the purpose of training a YOLOv8-based multi-class object detection model.

The goal is to detect and classify the six main actors from the TV series *Friends*.

---

## Data Collection

Images were manually collected from Google Images.

To ensure **domain consistency** and reduce distribution shift, all images were restricted to the *Friends era* (1994–2004).

The dataset includes:

- 🎬 Scenes from the *Friends* TV series
- 📸 Official photoshoots from the same period
- 🎭 Red carpet appearances and interviews (1994–2004)

This temporal constraint was intentionally applied to:

- Maintain visual consistency (age, hairstyle, facial features)
- Avoid large appearance changes over time
- Improve generalization within a controlled visual domain

---

## Classes

The dataset contains 6 classes:

0. courteney_cox  
1. david_schwimmer  
2. jennifer_aniston  
3. lisa_kudrow  
4. matt_leblanc  
5. matthew_perry  

---

## Annotation

Annotations were manually created using **MakeSense.ai**.

- Format: YOLO
- Bounding boxes drawn around the head region
- One bounding box per visible actor

Annotation quality was prioritized to ensure stable training and reliable evaluation.

---

## Dataset Split

The dataset was divided into:

- 70% Training
- 20% Validation
- 10% Test

The split was performed randomly with a fixed seed to ensure reproducibility.

---

## File Structure (Expected)

dataset/
│
├── images/
│   ├── train/
│   ├── val/
│   └── test/
│
├── labels/
│   ├── train/
│   ├── val/
│   └── test/
│
└── friends.yaml

---

## Important Notice

⚠ The images are not included in this repository due to copyright restrictions.

The dataset can be reconstructed by:
1. Collecting images from the 1994–2004 period.
2. Annotating them in YOLO format.
3. Following the folder structure described above.

This repository contains:
- The dataset configuration file (`friends.yaml`)
- The training and evaluation pipeline
- Model outputs and analysis

---

## Key Considerations

- Dataset size: 277 images
- Small-scale custom dataset
- Transfer learning used to compensate for limited data
- Domain restriction improves stability

---

## Educational Use

This dataset was created strictly for academic and educational purposes.
