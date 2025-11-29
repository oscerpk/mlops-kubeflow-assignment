# California Housing — MLOps Pipeline (MLflow + DVC + Jenkins)
### Usman Shahid  
### BS AI — Cloud MLOps (Assignment #4)

---

## 📌 Project Overview

This project implements a **complete MLOps pipeline** using:

- **DVC** for data versioning  
- **MLflow** for experiment tracking  
- **A custom Python pipeline (`run_pipeline.py`)** instead of Kubeflow (as permitted due to Kubeflow instability)  
- **Jenkins** for Continuous Integration (CI)  
- **GitHub** for version control  
- **Scikit-learn** for model training  

The ML task is **California Housing Price Regression** using a simple machine learning model  
(RandomForestRegressor).  
The pipeline automates the entire ML workflow:

1. Data extraction (via DVC)
2. Data preprocessing
3. Model training
4. Model evaluation
5. Experiment logging (MLflow)
6. Automated CI pipeline (Jenkins)

---

## 📦 Repository Structure

mlops-kubeflow-assignment/
│── data/
│ ├── raw/
│ │ └── california.csv.dvc
│ └── processed/
│── artifacts/
│ ├── california.csv
│ ├── model/
│ └── metrics/
│── src/
│ └── pipeline_components.py
│── run_pipeline.py
│── requirements.txt
│── Jenkinsfile
│── README.md
│── .dvc/
│── .dvcignore
