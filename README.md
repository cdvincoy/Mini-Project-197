# AI Workforce Readiness and Automation Clustering Using K-Means

This repository contains our CMSC 197 Machine Learning Mini Project titled:

**Clustering Countries Based on AI Workforce Readiness and Automation Indicators Using K-Means**

The project applies **K-Means clustering** to group countries based on artificial intelligence workforce readiness and automation-related indicators from 2015 to 2025.

## Project Overview

Artificial intelligence and automation are increasingly affecting employment, productivity, workforce structures, and national development strategies. However, countries differ in how they invest in AI, adopt automation, support workforce reskilling, and prepare policies for AI-driven labor market changes.

This project uses unsupervised machine learning to identify groups of countries with similar AI workforce readiness and automation profiles.

## Objectives

The main objective of this project is to group countries based on AI workforce readiness and automation indicators using **K-Means clustering**.

Specifically, the project aims to:

- Analyze AI workforce and automation-related indicators across countries.
- Preprocess and aggregate country-level data from 2015 to 2025.
- Apply K-Means clustering to identify country groups with similar profiles.
- Evaluate cluster quality using clustering validation metrics.
- Interpret the resulting clusters based on investment, automation, employment, productivity, reskilling, policy readiness, job displacement, job creation, and AI readiness.

## Dataset

The dataset used is the **AI Workforce and Automation Dataset (2015–2025)** from Kaggle.

Dataset source:  
https://www.kaggle.com/datasets/emirhanakku/ai-workforce-and-automation-dataset-20152025

The dataset contains:

- 20 countries
- Years covered: 2015–2025
- 220 rows
- 12 columns
- No missing values

Since the goal of the project is country-level clustering, yearly records were aggregated by country using the mean of numeric features. This resulted in 20 country-level observations.

## Selected Features

The following features were used for clustering:

### Investment and Capacity
- `AI_Investment_BillionUSD`
- `Reskilling_Investment_MillionUSD`

### Workforce and Labor Outcomes
- `Employment_Rate_Percent`
- `Job_Displacement_Million`
- `Job_Creation_Million`

### Readiness and Policy
- `Productivity_Index`
- `Automation_Rate_Percent`
- `AI_Policy_Index`
- `AI_Readiness_Score`

The variables `Year`, `Country`, and `Average_Salary_USD` were excluded from the final clustering feature set. Average salary was excluded because it reflects general economic development more than AI-specific workforce readiness.

## Methodology

The project followed this workflow:

1. Load the raw dataset.
2. Inspect dataset structure and missing values.
3. Aggregate yearly records by country.
4. Select relevant AI workforce and automation features.
5. Standardize features using `StandardScaler`.
6. Evaluate possible values of `k` using:
   - Elbow Method
   - Silhouette Score
7. Apply K-Means clustering with `k = 5`.
8. Evaluate cluster quality using:
   - Silhouette Score
   - Davies-Bouldin Index
   - Dunn’s Index
9. Visualize and interpret clusters using:
   - Correlation heatmap
   - Feature distribution plots
   - Standardized cluster profile heatmap
   - PCA visualization
   - World map visualization

## Model Used

The final clustering model used:

```python
KMeans(n_clusters=5, random_state=42, n_init=10)
```

Although smaller values of k, especially k = 2, produced higher silhouette scores, the final model used k = 5 because it provided more detailed and interpretable country groupings.


## Results

The K-Means model grouped the 20 countries into five clusters:

| Cluster | Countries | Interpretation |
| :----------- | :------------- | :------------ |
| Cluster 0         | China, Germany, Spain, Turkey           | Employment-strong, lower-readiness group          |
| Cluster 1         | Brazil, Japan, Netherlands, United States           | High-investment, high-readiness group          |
| Cluster 2         | France, Mexico, South Africa, South Korea           | Automation-heavy transition group          |
| Cluster 3         | Australia, Italy, Singapore, United Kingdom          | Mid-level automation with limited labor-market gains          |
| Cluster 4         | Canada, India, Russia, Sweden          | Policy- and reskilling-focused group          |


## Cluster Validation Results

The five-cluster model produced the following validation scores:

| Metric | Score |
| :---------- | :---------- |
Silhouette Score | 0.151 |
Davies-Bouldin Index | 1.277 |
Dunn’s Index | 0.453 |

The overall silhouette score indicates weak to modest cluster separation. Therefore, the results should be interpreted as exploratory rather than as perfectly separated clusters.

## Key Findings

The results suggest that AI workforce readiness is multidimensional. Countries differ not only in their level of AI adoption, but also in their investment, automation rate, productivity, reskilling support, AI policy readiness, job displacement, and job creation.

The world map visualization also suggests that countries in the same cluster are not always geographically close. This indicates that AI workforce readiness may be shaped more by investment, policy, and workforce development strategies than by regional location alone.

## Repository Structure

```text
Mini-Project-197/
├── README.md
├── global_ai_workforce_automation_2015_2025.csv
├── Mini Project K Means 5 Clusters.ipynb
├── .gitignore
└── docs/
    ├── Walviro - K-Means AI Workforce Machine Learning Paper.pdf
    ├── Walviro - K-Means AI Workforce Machine Learning Presentation.pdf
    └── Walviro_Mini_Project_Report_TEX_files.zip

```
Folder names may vary depending on the final repository organization.

## Requirements

The project was developed using Python and Jupyter Notebook.

Main Python libraries used:

```
pandas
numpy
matplotlib
seaborn
scikit-learn
plotly
```

To install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn plotly
```

## How to run the Notebook

1. Clone this repository:

```bash
git clone https://github.com/cdvincoy/Mini-Project-197.git
```

2. Open the project folder:

```bash
cd Mini-Project-197
```

3. Launch Jupyter Notebook:

```bash
jupyter notebook
```

4. Open the notebook file:

```txt
Mini Project K Means 5 Clusters.ipynb
```

5. Run the cells from top to bottom. (Restart Kernel if necessary)

Make sure the dataset file is in the same directory expected by the notebook, or update the dataset path in the notebook.

## Limitations

- The study uses only 20 countries after aggregation.
- The yearly records were averaged, so the model does not analyze year-by-year trends.
- The five-cluster solution has modest separation based on the silhouette score.
- The project uses only K-Means clustering; other clustering methods may produce different results.

## Future Work

Possible improvements include:

- Using a larger dataset with more countries.
- Analyzing yearly trends instead of only country-level averages.
- Comparing K-Means with other clustering algorithms such as Hierarchical Clustering or DBSCAN.
- Testing different feature combinations.
- Validating results with additional real-world labor, AI policy, and economic indicators.

## Authors

- Walton Karl Avillanosa
- John Romson Erazo
- Claire Dane Vincoy

University of the Philippines Visayas
CMSC 197 Machine Learning Mini Project

## References

- Kaggle Dataset: https://www.kaggle.com/datasets/emirhanakku/ai-workforce-and-automation-dataset-20152025
- Project Repository: https://github.com/cdvincoy/Mini-Project-197