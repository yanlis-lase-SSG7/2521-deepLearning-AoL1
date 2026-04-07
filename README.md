# Deep Learning AoL 1: Malware Binary Image Classification (Computer Vision)

**Student Name:** Yanlis Alim Sang Putra Lase  
**Student ID:** 2702751284  
**Program:** Master's in Informatics, BINUS Graduate Program

This repository contains Project I (AoL) implementation for COMP8044041, focused on malware family classification using computer vision on byteplot images.

## 1. Project Overview

This project addresses a cybersecurity computer vision case: **multi-class malware image classification (31 families)**. PE malware binaries are represented as grayscale byteplot images, then classified with deep learning models.

The project is designed for comparative and analytical objectives:
1. Build and evaluate a baseline CNN model.
2. Implement and compare three state-of-the-art transfer learning architectures.
3. Analyze model performance with full evaluation metrics and class-level error patterns.

## 2. Data Source

Dataset source:
- **Kaggle dataset:** `gauravpendharkar/blended-malware-image-dataset`

Dataset composition:
- Total classes: **31 malware families**
- Total images: around **13.7K**
- Split: pre-split directories (`train/` and `val/`)
- Format: grayscale PNG images (byteplot representation)

Data examples are shown directly in notebook EDA sections:
- class distribution chart
- sample byteplot images from multiple classes
- intensity and metadata summaries

## 3. Function and Purpose

Core functions of this project:
1. Classify malware images into 31 classes.
2. Compare four deep learning architectures:
	- **Model 1:** Baseline CNN (from scratch)
	- **Model 2:** ResNet50V2 transfer learning
	- **Model 3:** EfficientNetB0 transfer learning
	- **Model 4:** MobileNetV2 transfer learning
3. Provide comparative analysis using Accuracy, Precision, Recall, F1-Score, and Confusion Matrix.

## 4. Expected Output

Expected deliverables:
1. Trained models and histories for four architectures.
2. Automated EDA report: `EDA_Report_Malware.html`.
3. Saved visualization artifacts in `output_report/`:
	- training curves
	- confusion matrices
	- metric comparison chart
	- EDA charts

## 5. Step-by-Step Installation and Usage

Run commands from PowerShell.

### 5.1 Git Clone

```powershell
git clone https://github.com/yanlis-lase-SSG7/2521-deepLearning-AoL1.git
cd 2521-deepLearning-AoL1
```

### 5.2 Create Virtual Environment

```powershell
python -m venv venv
```

### 5.3 Activate Virtual Environment (Windows)

```powershell
.\venv\Scripts\activate
```

### 5.4 Set Kaggle Token (Do Not Hardcode in Files)

```powershell
$env:KAGGLE_API_TOKEN="YOUR_KAGGLE_API_TOKEN"
```

### 5.5 Install Dependencies

```powershell
pip install -r AoL1-requirements.txt
```

### 5.6 Run the Notebook

Open and execute:
- `AoL1-Malware-Vision.ipynb`

For reproducibility, run cells sequentially from top to bottom.

## 6. Technical Requirements

- Python 3.9+
- TensorFlow 2.x
- Scikit-Learn
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Pillow
- KaggleHub
- Jupyter Notebook / VS Code Notebook support

> Note (Windows): native TensorFlow is configured to run on CPU.

## 7. Architecture Details

| Aspect | Model 1 | Model 2 | Model 3 | Model 4 |
|---|---|---|---|---|
| Name | Baseline CNN | ResNet50V2 TL | EfficientNetB0 TL | MobileNetV2 TL |
| Strategy | From scratch | Frozen backbone + custom head | Frozen backbone + custom head | Frozen backbone + custom head |
| Input handling | Grayscale direct | Grayscale to pseudo-RGB | Grayscale to pseudo-RGB | Grayscale to pseudo-RGB |
| Objective | Baseline reference | Strong SOTA transfer baseline | Efficient SOTA transfer baseline | Lightweight SOTA baseline |

## 8. Workflow (How it Works)

1. **Environment Setup & Authentication**  
	Validate Kaggle token from environment variable.

2. **Dataset Retrieval and Validation**  
	Download dataset (if missing), validate `train/` and `val/` folder integrity.

3. **EDA and Data Understanding**  
	Explore class distribution, sample images, pixel statistics, and metadata report.

4. **TensorFlow Input Pipeline**  
	Load images with resize (`128x128`), normalization, batching, and prefetch.

5. **Model Building**  
	Build baseline CNN and three transfer learning models.

6. **Training**  
	Train all models under the same hyperparameter setup for fair comparison.

7. **Evaluation and Comparison**  
	Evaluate using full metrics and confusion matrices; summarize best-performing model.

8. **Analysis by Learning Objectives**  
	Interpret architecture-performance relation (LO4), advancements/challenges (LO5), and design innovation (LO6).

## 9. AoL Form Coverage Checklist

This notebook is aligned with Project I AoL instructions:
1. Computer vision case/topic is clearly defined and motivated.
2. Dataset source, composition, and examples are documented.
3. Multiple deep learning models are implemented and experimented.
4. Model performance is evaluated and compared with clear analysis.
5. Source code and report artifacts are included in the repository.

## Repository Structure

```text
2521-deepLearning-AoL1/
├── dataset/
│   ├── train/
│   └── val/
├── output_report/
├── AoL1-Malware-Vision.ipynb
├── AoL1-requirements.txt
├── EDA_Report_Malware.html
└── README.md
```
