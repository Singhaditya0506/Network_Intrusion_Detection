# Network Intrusion Detection with Machine Learning

A practical machine learning project for detecting and classifying cyber-attacks from network traffic data.

## Project Overview
This repository builds a multiclass intrusion detection workflow using network traffic features. The notebook loads multiple attack CSV files, combines them into a single dataset, applies a leakage-safe preprocessing flow, and compares several models on the original imbalanced data and on SMOTE-resampled training data.

## Problem Statement
Modern network environments generate large volumes of traffic, and malicious activity can be difficult to detect using static rules alone. This project frames intrusion detection as a supervised classification task and evaluates which model performs best on a realistic imbalanced cyber dataset.

## Objectives

- Develop a machine learning-based system for network intrusion detection.
- Perform binary classification to distinguish between normal and attack traffic.
- Perform multiclass classification to identify 11 different traffic and attack categories.
- Analyze and preprocess network traffic data for effective model development.
- Address class imbalance using SMOTE applied only to the training data.
- Compare machine learning models for both binary and multiclass classification tasks.
- Evaluate model performance using Accuracy, Precision, Recall, and Macro F1-score.
- Analyze model performance across individual attack classes and overall classification performance.
- Identify suitable models based on their ability to detect different types of network traffic and attacks.

## Dataset
The dataset is split across multiple CSV files, one for each attack family. These files are combined into a single DataFrame before modeling.

The raw dataset files are currently not included in this GitHub repository and are excluded using the `.gitignore` file. The required dataset files may be added to the repository in the future.


## Attack Categories
The multiclass target is `attack_type`, which includes:
- back
- buffer_overflow
- ftp_write
- guess_password
- neptune
- nmap
- normal
- portsweep
- rootkit
- satan
- smurf


## Workflow
1. Load attack datasets
2. Combine files into a single dataset
3. Clean and align feature columns
4. Separate features and target
5. Split into train and test sets
6. Scale features using training-only statistics
7. Evaluate baseline models without SMOTE
8. Apply SMOTE only to training data
9. Train and compare models
10. Summarize results using Macro F1

## Models Compared
- Logistic Regression
- Decision Tree
- Random Forest
- Logistic Regression + SMOTE
- Decision Tree + SMOTE
- Random Forest + SMOTE

## Results

| Model | Macro F1 |
| --- | ---: |
| Logistic Regression (without SMOTE) | 0.8093006359530651 |
| Decision Tree (without SMOTE) | 0.7858146521904007 |
| Random Forest (without SMOTE) | 0.8548396920033903 |
| Logistic Regression + SMOTE | 0.7585572188279205 |
| Decision Tree + SMOTE | 0.8553752163044486 |
| Random Forest + SMOTE | 0.8005405883198035 |

### Optional Binary Task
The notebook also includes a binary classification variant for `normal` vs `attack` using logistic regression.

- Accuracy: 0.9978064631869072
- Macro F1: 0.9973604914938325

## Evaluation Metric
For this imbalanced multiclass problem, Macro F1 is the primary metric. It provides a more reliable comparison than raw accuracy when the class distribution is highly uneven.

## Repository Structure
```text
network-intrusion-detection/
├── data/
│   ├── README.md
│   └── <dataset csv files>
├── notebooks/
│   └── Network_Intrusion_Detection.ipynb
├── .gitignore
├── README.md
├── requirements.txt
└── .git/
```

## Requirements
Install the project dependencies with:

```bash
pip install -r requirements.txt
```

## How to Run
1. Clone the repository.
2. Place the required CSV files into the data/ folder.
3. Open the notebook in notebooks/.
4. Run the cells in sequence.

## Technologies Used
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Imbalanced-learn
- Jupyter Notebook

## Key Takeaways
- This is a real multiclass intrusion detection problem with class imbalance.
- Macro F1 is more meaningful than accuracy for this dataset.
- Oversampling should be applied only to the training set to avoid leakage.
- The notebook includes both the original multiclass task and a simpler binary attack-vs-normal task.

## License
This project is intended for learning and research use.
