
# 🎬 Friends Actor Detection with YOLOv8

Computer Vision • Object Detection • Transfer Learning • Deep Learning

---

## 📌 Project Overview

This project explores multi-class object detection using **YOLOv8** to detect and identify the six main actors from the TV series *Friends*.

Instead of using a traditional face recognition pipeline, this project treats the problem as an **object detection task**, where each actor represents a separate class.

The model was fine-tuned using transfer learning on a custom-built dataset of manually annotated images.

---

## 🎯 Objective

To detect and classify the following six actors:

- Courteney Cox  
- David Schwimmer  
- Jennifer Aniston  
- Lisa Kudrow  
- Matt LeBlanc  
- Matthew Perry  

The system performs:

- 📦 Bounding box localization  
- 🏷 Multi-class classification  

---

## 🗂 Dataset Construction

### 🔍 Data Collection

The dataset was manually built from images collected via Google Images.

To ensure domain consistency and reduce distribution shift, all images were selected from the *Friends era* (1994–2004).

The dataset includes:

- 🎬 Scenes from the *Friends* TV series  
- 📸 Official photoshoots from the same period  
- 🎭 Red carpet appearances and interviews (1994–2004)  

Restricting the dataset to this time period was a deliberate methodological choice to:

- Maintain visual consistency (age, hairstyle, facial features)
- Reduce large appearance changes over time
- Improve model generalization within a controlled domain

### ✏ Annotation

- Tool used: **MakeSense.ai**
- Format: YOLO
- Bounding boxes drawn around the head region for consistency

### 📊 Dataset Statistics

- Total images: 277
- Number of classes: 6
- Train split: 70%
- Validation split: 20%
- Test split: 10%

---

## 🧠 Model Architecture

The model used is **YOLOv8n**, a lightweight object detection architecture pretrained on COCO.

Architecture components:

- Backbone (feature extraction)
- Neck (multi-scale feature aggregation)
- Detection head (bounding box regression + classification)

Transfer learning was applied by fine-tuning pretrained weights to adapt the model to the six custom classes.

---

## ⚙ Training Configuration

- Model: YOLOv8n
- Image size: 640x640
- Epochs: 50
- Batch size: 16
- Optimizer: Default Ultralytics optimizer
- Data augmentation: HSV variations, scaling, horizontal flipping

---

## 📈 Results

### 🔢 Quantitative Metrics (Test Set)

- mAP@50 ≈ 0.95
- mAP@50-95 ≈ 0.80
- Precision ≈ 0.88–0.90
- Recall ≈ 0.88–0.90

Despite the relatively small dataset size, the model achieved strong detection and classification performance.

---

## 📊 Confusion Matrix Analysis

Minor misclassifications occur mainly between visually similar actors, especially among male actors.

This is likely due to:

- Similar facial morphology  
- Comparable hairstyles  
- Variations in lighting conditions  

---

## 🖼 Qualitative Results

The model successfully detects and classifies actors across:

- Different lighting conditions
- Various facial expressions
- Moderate pose variations

Failure cases mainly occur under:

- Extreme facial expressions
- Partial occlusions
- Strong lighting contrast

---

## 🧪 How to Run

### Install dependencies

```bash
pip install ultralytics
```

### Train

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")
model.train(data="friends.yaml", epochs=50)
```

### Evaluate

```python
model.val(data="friends.yaml", split="test")
```

---

## 🚀 Possible Improvements

- Increase dataset size
- Add group scenes
- Try larger YOLO variants (YOLOv8s or YOLOv8m)
- Add stronger augmentation
- Compare with face-recognition-based pipelines

---

## 📌 Key Takeaways

- Transfer learning is extremely effective for small custom datasets
- Annotation quality significantly impacts performance
- Domain consistency (1994–2004 constraint) improves model stability
- YOLOv8 provides strong results even with limited data

---

## 👩‍💻 Author

Mazilda  
Master’s student in Intelligent Systems and Data Science  

---

## 📎 License

This project is for educational purposes only.
