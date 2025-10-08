# Health Diagnosis System

An AI system that provides preliminary health diagnoses for general sickness and diabetes risk based on user symptoms and vital signs. The system takes interactive input and generates a formatted HTML health report.


## 📜 Introduction
Healthcare diagnosis is a critical component of modern medicine that significantly impacts patient outcomes and healthcare system efficiency. Traditional diagnostic approaches rely heavily on clinical expertise and manual interpretation of symptoms, which can be time-consuming and subject to human error. With advances in artificial intelligence, machine learning-based diagnostic systems have emerged as powerful tools to assist healthcare professionals in making accurate and timely diagnoses.

This project implements such a system, capable of processing patient data, identifying complex patterns, and providing consistent diagnostic support. Its importance lies in enhancing preliminary medical screening, enabling early risk detection, and standardizing the initial diagnostic process.

## 📊 Datasets
This project was trained using the following publicly available datasets from Kaggle:
- [Disease Diagnosis Dataset](https://www.kaggle.com/datasets/kaushil268/disease-prediction-using-machine-learning)
- [Healthcare Dataset](https://www.kaggle.com/datasets/prathameshpatil3110/healthcare-dataset)
- [Early Stage Diabetes Risk Prediction Dataset](https://www.kaggle.com/datasets/saurabh00007/diabetes-prediction-uci)

## ✨ Key Features
- **Dual-Model Prediction**: Uses separate Random Forest models to predict general diseases (Cold, Flu, etc.) and assess diabetes risk.
- **Interactive Checkup**: A simple command-line interface guides the user through a health questionnaire.
- **Rule-Based Severity**: Applies clinical rules based on vitals (temperature, oxygen saturation) to assess the severity of the condition.
- **Formatted Health Report**: Generates a clean HTML report summarizing the diagnosis, vitals, and advice.

## 🛠️ Tech Stack
- **Models**: Random Forest Classifier
- **Core Libraries**: Scikit-learn, Pandas, NumPy, Joblib

## 🤝 Contributors
- **Anurag Singh 2352216**
- **Puja Kumari 2352217**
