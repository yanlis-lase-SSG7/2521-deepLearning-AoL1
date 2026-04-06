# Deep Learning AoL 1 : [will be updated soon]

**Student Name:** Yanlis Alim Sang Putra Lase  
**Student ID:** 2702751284  
**Program:** Master's in Informatics, BINUS Graduate Program

This repository contains the implementation and documentation for a Deep Learning assignment (Forum 03) focused on modeling workforce welfare indicators in Indonesia.

## 1. Project Overview

This project applies a **Multi-Layer Perceptron (MLP)** approach to predict the welfare ratio of workers in Indonesia using integrated socio-economic indicators. The prediction target is a welfare proxy ratio built from wage and expenditure variables, allowing the model to capture purchasing-power-oriented welfare patterns rather than wage magnitude alone.

The research objective is both predictive and comparative: to build a robust end-to-end machine learning pipeline and evaluate how architecture depth and optimization settings affect generalization quality.

## 2. Data Source

All data originates from **Badan Pusat Statistik (BPS)** and is accessed through Kaggle:

- **Kaggle dataset:** `rezkyyayang/pekerja-sejahtera`

The project uses exactly 8 dataset files, covering raw and processed versions of the four primary domains (GK, UMP, Upah, Pengeluaran):

| No. | Domain | Raw File | Processed File | Description |
|---|---|---|---|---|
| 1 | GK (Garis Kemiskinan) | `gk.csv` | `gk.df.csv` | Poverty line indicators used as contextual socio-economic input |
| 2 | UMP (Upah Minimum Provinsi) | `ump.csv` | `ump.df.csv` | Provincial minimum wage indicators |
| 3 | Upah (Wages) | `upah.csv` | `upah.df.csv` | Worker wage information used in target construction |
| 4 | Pengeluaran (Expenditure) | `peng.csv` | `peng.df.csv` | Expenditure indicators used for welfare ratio formation |

## 3. Function and Purpose

The project is designed to perform the following core functions:

1. Predict the target variable **`upah_peng_ratio`** as a welfare ratio indicator.
2. Evaluate two MLP architectures for performance and stability comparison: **2-layer MLP** versus **4-layer MLP**.
3. Compare optimization behavior under multiple learning rates:

- `1e-3`
- `1e-4`
- `1e-5`
- `1e-6`

The comparative design supports a methodologically structured analysis of model capacity versus optimization granularity.

## 4. Expected Output

The expected deliverables of this project are:

1. **Trained MLP models** for each architecture and configuration scenario.
2. **Automated EDA report** generated as `EDA_Report_Welfare.html`.
3. **Visual loss evolution graphs** (training and validation loss curves) for architecture and learning-rate analysis.

### Quick Access: EDA Report (HTML)

Click here to open the published EDA report directly:

- **EDA Report:** [https://yanlis-lase-SSG7.github.io/2521-deepLearning-forum03/EDA_Report_Welfare.html](https://yanlis-lase-SSG7.github.io/2521-deepLearning-forum03/EDA_Report_Welfare.html)

## 5. Step-by-Step Installation and Usage

Run the following commands in PowerShell from your preferred working directory.

### 5.1 Git Clone

```powershell
git clone https://github.com/yanlis-lase-SSG7/2521-deepLearning-forum03.git
cd 2521-deepLearning-forum03
```

### 5.2 Create Virtual Environment

```powershell
python -m venv venv
```

### 5.3 Activate Virtual Environment (Windows)

```powershell
.\venv\Scripts\activate
```

### 5.4 Set Kaggle Token

```powershell
$env:KAGGLE_API_TOKEN="YOUR_KAGGLE_API_TOKEN"
```

### 5.5 Install Dependencies

```powershell
pip install -r Forum03-requirements.txt
```

Alternative (manual install):

```powershell
pip install pandas numpy matplotlib seaborn scikit-learn tensorflow kagglehub ydata-profiling
```

### 5.6 Run the Project Notebook

Open and execute:

- `Forum03-pekerja_sejahtera_question.ipynb`

For reproducible results, run notebook cells sequentially from top to bottom.

## 6. Technical Requirements

The technical stack for this project includes:

- Python 3.9+
- TensorFlow 2.x
- Scikit-Learn
- Pandas
- NumPy
- Matplotlib
- Seaborn
- KaggleHub
- ydata-profiling
- Jupyter Notebook / VS Code Notebook support

> Note (Windows): TensorFlow in this notebook is configured to run on CPU for native Windows compatibility.

## 7. Architecture Details

The following table summarizes the two MLP architectures evaluated in this assignment:

| Component | Model 01 | Model 02 |
|---|---|---|
| Hidden-layer depth | 2 layers | 4 layers |
| Hidden neurons | 64-32 | 128-64-32-16 |
| Output layer | 1 neuron (regression output) | 1 neuron (regression output) |
| Purpose | Baseline architecture with lower complexity | Deeper architecture for richer non-linear representation |

## 8. Workflow (How it Works)

The full pipeline is implemented as a structured sequence:

1. **Data Integration**  
	Consolidate GK, UMP, Upah, and Pengeluaran datasets into a unified analytical table.

2. **Local Dataset Caching**  
	Check `dataset/` first; download from Kaggle only when CSV cache is not available.

3. **Hierarchical Imputation (Province-Region-Type)**  
	Handle missing values progressively using grouped medians in hierarchical order to preserve local socio-economic context.

4. **One-Hot Encoding**  
	Convert categorical attributes into model-compatible binary feature vectors.

5. **Power Transformation**  
	Apply a PowerTransformer to stabilize target distribution and improve optimization behavior.

6. **Training**  
	Train the MLP architectures under controlled hyperparameter settings.

7. **Validation**  
	Evaluate model behavior using validation curves and comparative metrics across architecture depth and learning rates.

## Repository Structure

```text
2521-deepLearning-forum03/
├── dataset/
│   ├── gk.csv
│   ├── gk.df.csv
│   ├── peng.csv
│   ├── peng.df.csv
│   ├── ump.csv
│   ├── ump.df.csv
│   ├── upah.csv
│   └── upah.df.csv
├── EDA_Report_Welfare.html
├── Forum03-pekerja_sejahtera_question.ipynb
├── Forum03-requirements.txt
└── README.md
```
