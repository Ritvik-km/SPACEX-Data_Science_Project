# SpaceX Data Science Project

## Falcon 9 Launch Success Prediction System

### Project Overview

This capstone project builds a comprehensive pipeline to predict the success of SpaceX Falcon 9 first-stage landings. By combining data ingestion, wrangling, exploratory analysis, interactive visualizations, and machine learning, the project demonstrates end-to-end data science best practices applied to real-world space launch data.

### Table of Contents

- [Background](#background)
- [Features](#features)
- [Data Collection](#data-collection)
- [Data Wrangling & Preparation](#data-wrangling--preparation)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Interactive Visual Analytics](#interactive-visual-analytics)
- [Machine Learning Pipeline](#machine-learning-pipeline)
- [Dashboard](#dashboard)
- [Results & Insights](#results--insights)
- [Requirements](#requirements)
- [License](#license)

### Background

SpaceX's ability to reuse the first stage dramatically reduces launch costs. Predicting the landing success of Falcon 9 first stages enables stakeholders to assess launch bids and operational risk. This project leverages SpaceX's public API and historical launch data to build a predictive model and interactive analytics tools.

### Features

- Automated data collection from the SpaceX REST API and Wikipedia web scraping
- Data cleaning and feature engineering (one-hot encoding, derived labels)
- Extensive EDA with scatter, bar, and line plots
- SQL-based analysis for summary statistics and queries
- Interactive maps of launch sites with Folium
- Plotly Dash dashboard for dynamic exploration
- Machine learning classification models (KNN, Decision Tree, SVM, Logistic Regression)
- Model evaluation with accuracy metrics and confusion matrix

### Data Collection

**Data Sources:**
- SpaceX API: https://api.spacexdata.com/v4/launches/past
- Wikipedia: "List of Falcon 9 and Falcon Heavy launches"

Raw JSON and HTML data were parsed into Pandas DataFrames and exported to CSV files.

### Data Wrangling & Preparation

- Filtered to Falcon 9 launches
- Extracted key features: booster version, payload mass, orbit, launch site, landing outcome
- Created binary Class label: 1 = successful landing, 0 = failure
- Handled missing values and applied one-hot encoding for categorical variables

### Exploratory Data Analysis (EDA)

**Visualizations:**
- Scatter plots to examine relationships between payload mass, flight number, and landing outcome
- Bar charts to compare success rates across orbits and launch sites
- Line charts to visualize yearly success trends

**SQL queries for:**
- Unique launch sites
- Payload summaries
- First ground-pad landing date
- Booster versions with specific outcomes

### Interactive Visual Analytics

**Folium Map:**
- Geographic distribution of launch sites, colored by success/failure
- Proximity Analysis: Distances of sites to railways, highways, coastlines, and nearby cities

**Plotly Dash Dashboard:**
- Launch counts and success ratios per site
- Payload vs. success scatter plots
- Booster version performance

### Machine Learning Pipeline

**Feature Scaling:** StandardScaler

**Train/Test Split:** 80/20

**Model Training with GridSearchCV for hyperparameter tuning:**
- K-Nearest Neighbors (KNN)
- Decision Tree
- Support Vector Machine (SVM)
- Logistic Regression

**Model Evaluation:**
- Accuracy comparison
- Confusion matrix analysis
- **Best Model:** Decision Tree with 0.90 accuracy (criterion: gini, max_depth=8, max_features=sqrt, min_samples_leaf=4, min_samples_split=5, splitter=random)

### Dashboard

A Plotly Dash application enabling users to:
- Select launch sites
- View site-specific success/failure ratios
- Explore payload vs. landing outcome across payload ranges and booster versions

### Results & Insights

- Success rates improved with more flights and over time, peaking in 2020
- KSC LC-39A had the highest success ratio
- Heavy payloads positively influenced LEO/ISS orbits but negatively impacted MEO/GTO/VLEO
- Decision Tree classifier outperformed other models for landing success prediction

### Requirements
```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
plotly>=5.0.0
dash>=2.0.0
folium>=0.12.0
scikit-learn>=1.0.0
requests>=2.25.0
beautifulsoup4>=4.9.0
jupyter>=1.0.0
```

### License

This project is licensed under the MIT License - see the LICENSE file for details.
