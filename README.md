# PDSAFormer-Code
An Attention-Driven Hybrid PDSAFormer Framework for Explainable Parkinson's Disease Prediction

This project proposes PDSAFormer, an attention-driven hybrid deep learning framework for Parkinson's Disease (PD) prediction using speech-derived features. The framework combines feature selection, spectral feature attention, Transformer-based learning, residual feature fusion, XGBoost, and SHAP explainability.

Project Workflow
Speech Features
      ↓
Data Preprocessing
      ↓
Feature Selection
753 → 200 Features
      ↓
Feature Embedding
      ↓
Spectral Feature Attention
      ↓
Transformer Encoder
      ↓
Residual Feature Fusion
      ↓
PDSAFormer
      ↓
Hybrid Fusion with XGBoost
      ↓
Final Prediction
      ↓
PD / Healthy
      ↓
SHAP Explainability
Dataset

Dataset used:

pd_speech_features.csv

The dataset contains 756 samples and 755 columns.

Target column: class
Identifier column: id
Usable features after removing id: 753
Selected important features: 200
Class Distribution
Class 1 : 564
Class 0 : 192
Data Preprocessing

The following preprocessing steps were performed:

Loaded the speech-feature dataset.
Removed the id column.
Separated the target variable class.
Standardized the feature values using StandardScaler.
Selected the 200 most informative features.
Divided the data into training, validation, and testing sets.
Data Split
Total samples : 756
Training      : 604
Testing       : 152

The training set was further divided into:

Training   : 483
Validation : 121
Testing    : 152
Proposed PDSAFormer

PDSAFormer is the proposed deep learning architecture.

Main Components

1. Feature Embedding

The 200 selected features are transformed into a dense representation using a Dense layer followed by Batch Normalization and Dropout.

2. Spectral Feature Attention

The attention module learns the importance of different feature dimensions and emphasizes informative speech characteristics.

3. Transformer Encoder

Multi-Head Self-Attention is used to learn relationships between the feature representations.

The Transformer block includes:

Multi-Head Attention
Residual Connection
Layer Normalization
Feed-Forward Network
Residual Feature Fusion

4. Classification

The learned representation is passed through fully connected layers and a sigmoid output to predict:

0 → Healthy
1 → Parkinson's Disease
Hybrid PDSAFormer + XGBoost

The proposed framework combines the PDSAFormer prediction with an independent XGBoost prediction.

                 200 Features
                      │
             ┌────────┴────────┐
             ↓                 ↓
        PDSAFormer          XGBoost
             ↓                 ↓
        Probability P1    Probability P2
             └────────┬────────┘
                      ↓
              Weighted Fusion
                      ↓
               Final Prediction

The fusion is represented as:

Pfinal = w1 × P1 + w2 × P2

where:

w1 + w2 = 1
Explainable AI

SHAP (SHapley Additive exPlanations) is used to interpret the model predictions.

SHAP helps identify:

Important speech features
Positive and negative feature contributions
Overall feature importance
Individual prediction explanations

This provides greater transparency into the model's decision-making process.

Models Compared

The proposed framework was compared with:

Model	Category
SVM	Classical Machine Learning
XGBoost	Gradient Boosting
LightGBM	Gradient Boosting
CatBoost	Gradient Boosting
TabNet	Deep Learning
MLP-ResNet	Modern Deep Learning
Hybrid PDSAFormer	Proposed Hybrid Framework
Performance
Model	Accuracy	ROC-AUC
SVM	90.8%	0.964
XGBoost	86.8%	0.950
LightGBM	88.8%	0.960
CatBoost	88.2%	0.948
TabNet	85.5%	0.922
MLP-ResNet	78.3%	0.852
Hybrid PDSAFormer	94.7%	0.978

Evaluation metrics include:

Accuracy
Precision
Recall
F1-Score
ROC-AUC
Technologies
Python
Pandas
NumPy
Scikit-learn
TensorFlow / Keras
XGBoost
LightGBM
CatBoost
TabNet
SHAP
Matplotlib
Google Colab
Repository Structure
PDSAFormer/
│
├── pd_speech_features.csv
├── PDSAFormer.ipynb
├── README.md
└── figures/
Google Colab

The complete implementation and experiments are available in Google Colab:

Colab Link:
(https://github.com/Poovizhi-P-36/PDSAFormer-Code.git)

How to Run
Clone or download this repository.
Open PDSAFormer.ipynb in Google Colab.
Upload pd_speech_features.csv.
Run the notebook cells sequentially.
The notebook performs preprocessing, feature selection, model training, comparison, hybrid prediction, and SHAP analysis.
Research Objective

The objective of this project is to develop an accurate and explainable Parkinson's Disease prediction framework using speech features, combining attention-based deep learning with tree-based machine learning.

Authors

S. Madhav
P. Niramal
P. Poovizhi

Department of Computer Science and Design
Kongu Engineering College
Perundurai, Erode – 638060, India

Disclaimer

This project is intended for academic and research purposes only. It is not intended to replace professional medical diagnosis or clinical decision-making.
