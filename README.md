# Drone Human & Car Detection System
**Antlings AI/ML Internship — Technical Assessment**

A computer vision pipeline for detecting humans and cars in drone/aerial imagery using YOLOv8, with object tracking via ByteTrack.

---

## Tasks Completed
| Task | Description | Status |
|------|-------------|--------|
| Task 01 | Dataset Understanding & Preprocessing | ✅ |
| Task 02 | Model Training (YOLOv8s fine-tuned on VisDrone) | ✅ |
| Task 03 | Human & Car Detection with Counting | ✅ |
| Task 04 | Object Tracking with ByteTrack (Bonus) | ✅ |
| Task 05 | Evaluation & Visualization | ✅ |

---

## Dataset
- **Source**: [VisDrone2019-DET](https://www.kaggle.com/datasets/banuprasadb/visdrone-dataset)
- **Train**: 6,471 images | **Val**: 548 images
- **Classes**: 10 (pedestrian, people, bicycle, car, van, truck, tricycle, awning-tricycle, bus, motor)
- **Classes used for counting**: pedestrian + people → Person | car → Car

---

## Model
- **Architecture**: YOLOv8s (pretrained on COCO, fine-tuned on VisDrone)
- **Input size**: 640×640
- **Training**: 50 epochs | Batch 64 | T4×2 GPU | Mixed Precision (AMP)
- **Tracker**: ByteTrack

---

## Results
| Metric | Epoch 20 | Epoch 50 |
|--------|----------|----------|
| mAP@0.5 | — | — |
| mAP@0.5:0.95 | — | — |
| Precision | — | — |
| Recall | — | — |

> Fill in values from your Cell 8 output before submitting.

---

## Sample Outputs

### Detection with Counting
![Detection Grid](outputs/detection_grid.png)

### Dataset Analysis
![Dataset Analysis](outputs/dataset_analysis.png)

### Evaluation Summary
![Evaluation](outputs/evaluation_summary.png)

---

## Project Structure
```
├── notebook.ipynb           # Full pipeline notebook
├── README.md
└── outputs/
    ├── dataset_analysis.png
    ├── sample_annotations.png
    ├── detection_grid.png
    ├── evaluation_summary.png
    ├── epoch_comparison_bars.png
    ├── epoch_comparison_curves.png
    └── epoch_comparison_predictions.png
```

---

## How to Run
1. Open `notebook.ipynb` on [Kaggle](https://kaggle.com)
2. Add dataset: `banuprasadb/visdrone-dataset`
3. Enable **GPU T4×2** accelerator
4. Run all cells in order

---

## Key Challenges
- Extreme small object sizes (pedestrians as small as 10×20 px)
- Dense crowd scenes with heavily overlapping boxes
- Variable altitude causing large scale differences
- Class imbalance across 10 categories

## Limitations
- Tracking uses sequential val images (pseudo-video), not real temporal video
- 50 epochs is sufficient for a demo but underfits for production use
- Small object recall remains low due to scale variation

---

## Demo Video
[[Watch on Google Drive](https://drive.google.com/file/d/1MAg3uJ81xn1Nelpk4nJBvSGKLiXWLFB0/view?usp=drive_link)](#) ← replace with your link

---

**Tools**: Python · YOLOv8 · ByteTrack · OpenCV · Kaggle T4×2 GPU
