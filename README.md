# D7047E — Advanced Deep Learning

Coursework and final project for **D7047E Advanced Deep Learning** at Luleå University of Technology (LTU).

The main deliverable of this repository is the final project: **Car Detection in Snow** using the Nordic Vehicle Dataset (NVD) with a YOLOv9-based detector.

---

## Repository Structure

```
.
├── 00/                              # Lab / exercise 0
├── 01/                              # Lab / exercise 1
├── 02/                              # Lab / exercise 2
├── 03/                              # Lab / exercise 3
├── 04/                              # Lab / exercise 4
├── project-car-detection-in-snow/   # Final project (main deliverable)
├── Car detection in snow-Group 16.pptx   # Project presentation
└── README.md
```

---

## Final Project — Car Detection in Snow

### Motivation

Vehicle detection in Nordic winter conditions is considerably harder than in the clear-weather scenes that most public detection benchmarks are built on. Snow cover removes colour and texture cues, low sun angles create long shadows and glare, falling snow adds noise, and vehicles are frequently partially buried or blend into a uniformly white background. On top of that, the imagery is captured from a UAV at altitude, so the targets are small and viewed from a top-down / oblique perspective.

The goal of this project is to train and evaluate a modern object detector on this domain and to quantify how well it holds up under those conditions.

### Dataset — Nordic Vehicle Dataset (NVD)

- Website: https://nvd.ltu-ai.dev/
- Paper: [Mokayed et al., *Nordic Vehicle Dataset (NVD): Performance of Vehicle Detectors Using Newly Captured NVD from UAV in Different Snowy Weather Conditions*, CVPRW 2023](https://openaccess.thecvf.com/content/CVPR2023W/AICity/html/Mokayed_Nordic_Vehicle_Dataset_NVD_Performance_of_Vehicle_Detectors_Using_Newly_CVPRW_2023_paper.html)

NVD consists of UAV-captured imagery of vehicles in snowy Nordic environments, recorded across varying snow conditions and flight altitudes, with bounding-box annotations for vehicles. It is proposed by the authors specifically as a benchmark for detection under adverse winter conditions, where models trained on standard datasets degrade sharply.

The dataset is **not redistributed in this repository** — it must be downloaded from the official website and placed locally (see *Setup*).

### Task

Single-class object detection: locate every vehicle in a given frame and output its bounding box.

### Approach

- **Base architecture:** YOLOv9, used as the reference detector required by the project brief.
- **Data preparation:** conversion of the NVD annotations to YOLO format, train / validation / test splitting, and image resizing to the network input resolution.
- **Training:** transfer learning from pretrained weights, with augmentation aimed at the failure modes of this domain (scale, mosaic, brightness/contrast jitter, flips).
- **Evaluation:** performance measured on a held-out test split with standard detection metrics.

### Metrics

The model is evaluated using the standard COCO-style detection metrics:

| Metric | Description |
|---|---|
| Precision | Fraction of predicted boxes that are correct |
| Recall | Fraction of ground-truth vehicles that are found |
| mAP@0.5 | Mean average precision at IoU threshold 0.5 |
| mAP@0.5:0.95 | Mean average precision averaged over IoU 0.5–0.95 |

Results, qualitative detections and the discussion of failure cases are reported in the project presentation (`Car detection in snow-Group 16.pptx`) and in the project folder.

### Scope and Limitations

- The project targets **vehicle detection only** — no tracking, re-identification, or counting across frames.
- Only the NVD imagery is used; no additional winter datasets are merged in.
- The focus is on evaluating a YOLOv9 baseline on this domain rather than proposing a new architecture.

---

## Setup

```bash
git clone https://github.com/Jukowsky/D7047E-ADL.git
cd D7047E-ADL/project-car-detection-in-snow

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Then download NVD from https://nvd.ltu-ai.dev/ and arrange it in YOLO layout:

```
datasets/nvd/
├── images/{train,val,test}/
└── labels/{train,val,test}/
```

A GPU with CUDA support is strongly recommended for training.

---

## Usage

Training:

```bash
python train.py --data data/nvd.yaml --weights yolov9-c.pt --img 640 --epochs 100 --batch 16
```

Evaluation on the test split:

```bash
python val.py --data data/nvd.yaml --weights runs/train/exp/weights/best.pt --task test
```

Inference on new images:

```bash
python detect.py --weights runs/train/exp/weights/best.pt --source path/to/images
```

> Adjust script names and flags to match the files in `project-car-detection-in-snow/`.

---

## Deliverables

- Source code, training and evaluation scripts — this repository
- Trained model weights
- Project presentation — `Car detection in snow-Group 16.pptx`

---

## References

1. H. Mokayed et al., "Nordic Vehicle Dataset (NVD): Performance of Vehicle Detectors Using Newly Captured NVD from UAV in Different Snowy Weather Conditions," *CVPR Workshops (AI City Challenge)*, 2023.
2. C.-Y. Wang, I-H. Yeh, H.-Y. M. Liao, "YOLOv9: Learning What You Want to Learn Using Programmable Gradient Information," 2024.

---

## Course

D7047E — Advanced Deep Learning
