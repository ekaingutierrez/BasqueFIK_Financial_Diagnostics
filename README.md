# BasqueFIK: Regional Financial Diagnostics & Corporate Risk Modeling

## Project Overview
This repository contains a comprehensive Machine Learning and financial analysis pipeline developed to assess the economic and financial health of the business fabric in the Basque Country (CAV) using official corporate data from over 26,000 companies. 

Instead of relying on static financial reporting, this project builds an automated risk-scoring system (Altman Z-Score), behavioral clustering models, and dynamic quadrant visualizers to proactively identify vulnerable corporate cohorts across the region.

## Data Confidentiality Notice
The datasets used in this project are not included in this repository. 
Due to the sensitive and confidential nature of the official corporate financial records, all raw data files (.csv, .xlsx) have been strictly excluded via .gitignore to comply with data privacy standards. 
Note: To execute the pipeline locally, users must provide their own structured dataset and place it within a local /Data directory.

## Tech Stack & Libraries
* Language: Python 3.10+
* Data Processing & Imputation: Pandas, NumPy, Scikit-Learn (Random Forest Regressors)
* Dimensionality Reduction & Clustering: Scikit-Learn (PCA, K-Means, RobustScaler), SciPy (Hierarchical Clustering / Ward Linkage)
* Visualization: Plotly, Seaborn, Matplotlib, Missingno

## Methodology & Technical Pipeline

### 1. Data Engineering, Quality Audit & Imputation (01_data_cleaning_and_imputation.ipynb)
* Missing Data Analysis: Evaluated absence patterns (MCAR, MAR, MNAR) using missingno. Imputed structural zeros where appropriate and applied median sector-based imputations to preserve economic coherence.
* Advanced Imputation: Implemented Random Forest Regressors to predict complex missing financial variables (e.g., EBITDA, financial debts) based on non-linear relationships with total assets and fixed assets.
* Outlier Treatment: Handled extreme values across financial ratios by clipping at the 5th and 95th percentiles to prevent distortion in unsupervised models.

### 2. Financial Diagnostics & Altman Z-Score (02_financial_and_economic_diagnosis.ipynb)
* Calculated critical financial and economic ratios: Liquidity, Acid Test, Solvency, Indebtedness, ROA, ROE, DSCR, and Working Capital vs. NOF.
* Implemented the Altman Z-Score model adapted for non-listed companies to categorize corporate solvency risk into three distinct zones: Safe Zone, Grey Zone, and Danger Zone.

### 3. Dimensionality Reduction & Behavioral Clustering (03_ratios_and_pca_clustering.ipynb)
* Feature Extraction & Scaling: Standardized financial features using RobustScaler to normalize disparate scales and mitigate outliers prior to dimensionality reduction.
* Principal Component Analysis (PCA): Applied dimensionality reduction, retaining 95% of cumulative variance to eliminate multicollinearity between financial metrics.
* K-Means & Hierarchical Clustering: Determined the optimal number of clusters using the Elbow Method and Silhouette Score. Executed K-Means and validated structural groupings through Hierarchical Clustering (Ward linkage) to profile distinct financial cohorts.

### 4. Strategic Quadrant Mapping & Regional Risk Analysis (04_four_quadrants_visualization.ipynb & 05_provincial_risk_analysis.ipynb)
* Mapped corporate positioning across a Four-Quadrant Matrix evaluating Economic Position (ROA) vs. Financial Position (Solvency) against sectoral benchmarks utilizing single-trace vectorized Plotly charts.
* Performed regional comparative analytics across Alava, Biscay, and Gipuzkoa to identify localized vulnerability pockets and dominant business sectors (e.g., CNAE 6820 Real Estate).

## How to Run the Project
1. Clone the repository:
   git clone https://github.com/ekaingutierrez/basquefik-financial-diagnostics.git
   cd basquefik-financial-diagnostics

2. Install dependencies:
   pip install -r requirements.txt

3. Run the analysis notebooks sequentially from 01_ to 06_ (Requires local dataset in /Data).
