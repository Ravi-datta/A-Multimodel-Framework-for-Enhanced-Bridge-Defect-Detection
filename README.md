# 🏗️ Multimodal Fusion Framework for Bridge Defect Detection with Cross‑Verification
*A reproducible research codebase that fuses Impact Echo (IE) and Ultrasonic Surface Wave (USW) data, augments it with image processing, and pinpoints bridge‑deck defects with an F1‑score of 0.83.*

---

## 🧠 Overview / Abstract  

Aging bridges often hide subsurface flaws—delamination, debonding, internal cracks—that visual inspection alone can miss.  
This project implements a **multimodal data‑fusion pipeline** that:

1. Converts raw IE & USW sensor signals into peak‑frequency and elasticity‑modulus maps.  
2. Filters defect‑prone points via data‑driven thresholds (k‑means).  
3. Localizes overlapping defect regions with **Alpha Shape Analysis (ASA)**.  
4. Cross‑verifies those regions on contour images using adaptive HSV masking + OpenCV bounding‑boxes.  

In pilot studies on six FHWA bridges, the framework increased localization accuracy and cut false positives by 32 percent

---

## 🔍 Problem Statement  

> **How can we reliably detect subsurface bridge‑deck defects using complementary NDE modalities, while keeping false alarms low enough for practical maintenance scheduling?**  

Traditional single‑modality NDE (either IE or USW) misses context; our fusion approach aims to deliver lane‑level, high‑confidence defect maps to DOT engineers.
---

## 🧪 Methodology / Approach  

| Stage | Key Techniques |
|-------|----------------|
| Data prep | XML → CSV converters, FFT for IE, cross‑correlation for USW | 
| Defect filtering | k‑means (k=3) thresholding |
| Spatial fusion | Alpha‑shapes (α = 0.5) & lane segmentation |
| Image cross‑verification | HSV masking, Canny‑edge adaptive morphology, OpenCV contours |
| Evaluation | Micro‑averaged precision/recall/F1 |

> Implemented in Python 3.9 with **NumPy, Pandas, scikit‑learn, shapely‑alphashape, OpenCV, Matplotlib** 
---

## 💡 Key Features / Contributions  

- **Dual‑modality fusion** of IE peak‑frequency and USW elasticity‑modulus for holistic defect capture 
- **Adaptive, geometry‑aware ASA** for precise overlapping‑defect localization, lane‑tagged for maintenance crews 
- **Vision‑based cross‑verification** that aligns fused points with contour “hot‑spots” to suppress false positives 
- **Scalable, script‑driven pipeline** ready for batch processing of large DOT datasets  
- **Benchmark performance**: Precision 0.75, Recall 0.92, F1‑score 0.83 on FHWA InfoBridge case study 

---

## 🚀 Installation / Quick Start  

```bash
# 1. Clone the repo
git clone https://github.com/<your‑handle>/bridge‑defect‑fusion.git
cd bridge‑defect‑fusion

# 2. Create environment
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 3. Run an end‑to‑end demo
python scripts/run_demo.py --config configs/i220_jackson.yaml
```
---

## 📘 License & Citation

This repository is licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).  
Commercial use is not permitted.

If you use this work in your research, please cite:

> "A Multimodal Fusion Framework for Bridge Defect Detection with Cross-Verification,"  
> IEEE International Conference on Big Data (Big Data), 2024.  
> DOI: [https://doi.org/10.1109/BigData62323.2024.10825867](https://doi.org/10.1109/BigData62323.2024.10825867)
