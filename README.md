🩺 AI-Powered Health Diagnosis System
This project is a comprehensive AI-powered health diagnosis system designed to provide preliminary medical screening. It leverages a dual-model architecture to predict general health conditions based on symptoms and vital signs, while simultaneously assessing a patient's risk for diabetes.

📋 Table of Contents
Introduction

Key Features

How It Works

Methods and Techniques

Datasets

Getting Started

Usage

File Structure

Contributors

📜 Introduction
Healthcare diagnosis is a critical component of modern medicine. Traditional diagnostic approaches rely heavily on clinical expertise and manual interpretation of symptoms, which can be time-consuming and subject to human error. With advances in artificial intelligence, machine learning-based diagnostic systems have emerged as powerful tools to assist healthcare professionals in making accurate and timely diagnoses. These systems can process vast amounts of patient data, identify complex patterns, and provide consistent diagnostic support, particularly in resource-constrained environments where access to specialized medical expertise is limited.

✨ Key Features
Dual-Model Architecture: Utilizes two specialized Random Forest models for predicting general diseases and diabetes risk, ensuring higher accuracy for each task.

Interactive Health Checkup: A user-friendly command-line interface that guides the user through a comprehensive health questionnaire.

Rule-Based Severity Assessment: Implements a post-processing logic based on clinical rules (e.g., high fever, low oxygen saturation) to assess the severity of a condition.

Contextual Insights: Integrates a separate healthcare dataset to provide context on common medications associated with the predicted diagnosis.

Data-Driven Visualizations: The training script includes visualizations to provide insights into the distribution of diagnoses, age, and other key features.

Formatted Health Report: Generates a clean, easy-to-read HTML report summarizing the user's vitals, AI-powered diagnosis, and recommended actions.

🚀 How It Works
The system operates in two main stages: training and inference.

Training (model_training.py):

Loads and cleans three distinct datasets.

Performs feature engineering (e.g., splitting blood pressure).

Trains a RandomForestClassifier for general disease diagnosis and another for diabetes prediction.

Saves the trained models and data processors (LabelEncoder objects) as .joblib files for later use.

Inference (health_checkup.py):

Loads the pre-trained models and encoders.

Prompts the user to enter their vitals and answer a series of symptom-related questions.

Uses the models to predict the primary condition and diabetes risk.

Applies rule-based logic to refine the diagnosis and determine severity.

Generates and displays a comprehensive health report in HTML format.

Example User Interaction & Report
The system first asks for user input via the command line:

--- Part 1: General Vitals & Symptoms ---
Enter your Age: 28
Enter your Gender (Male/Female): female
Enter your main Symptom (e.g., Fever): runny nose
...
--- Part 2: Diabetes Risk Assessment (Answer Yes/No) ---
Excessive or abnormally large production or passage of urine? no
...
Based on the input, it generates a detailed report:

HTML

<div style='font-family: Arial, sans-serif; border: 2px solid #007BFF; padding: 20px; border-radius: 10px; background-color: #f8f9fa; max-width: 650px; margin: auto;'>
    <h2 style='color: #0056b3; border-bottom: 2px solid #0056b3; padding-bottom: 10px;'>🩺 Comprehensive AI Health Report</h2>
    <h3 style='color: #007BFF;'>Primary Diagnosis</h3>
    <p><b>Predicted Condition:</b> <span style='font-weight: bold; font-size: 1.1em;'>Healthy</span></p>
    <p><b>Assessed Severity:</b> <span style='font-weight: bold; color: #28a745;'>Mild</span></p>
    <h3 style='color: #007BFF;'>Diabetes Risk Assessment</h3>
    <p><b>Potential Diabetes Status:</b> <span style='font-weight: bold; color: #28a745;'>Negative</span></p>
    <hr style='border: 1px solid #dee2e6; margin: 20px 0;'>
    <h3 style='color: #007BFF;'>Your Vitals</h3>
    <p><b>Body Temperature:</b> 37.1 °C | <b>Oxygen Saturation:</b> 96.0%</p>
    <p><b>Blood Pressure:</b> 151.0/96.0 mmHg | <b>Heart Rate:</b> 63.0 bpm</p>
    <div style='background-color: #e9ecef; padding: 15px; border-radius: 8px; margin-top: 20px;'>
        <p style='color: #495057; font-weight: bold;'>Disclaimer & Advice:</p>
        <p style='color: #495057;'>This is an AI-generated report, not a substitute for professional medical advice. Our recommendation is: <b>Stay hydrated and get plenty of rest. Monitor your condition.</b></p>
    </div>
</div>
🛠️ Methods and Techniques
Data Preprocessing
Feature Engineering: Blood Pressure (e.g., "120/80") was split into two numerical features: Systolic and Diastolic pressure.

Data Cleaning: Categorical strings were standardized by stripping whitespace and converting them to a consistent case.

Label Encoding: Non-numerical features were converted into numerical representations using sklearn.preprocessing.LabelEncoder.

Machine Learning Model
Random Forest Classifier is used for both prediction tasks. It's an ensemble method that builds multiple decision trees during training and outputs the mode of the classes for classification. This approach is robust to overfitting and handles complex interactions between features well.
The prediction for a new input x is given by:

Y 
prediction
​
 =Mode{h 
1
​
 (x),…,h 
k
​
 (x)}

where h 
i
​
 (x) is the prediction of the i-th decision tree in the forest of k trees.

Rule-Based Post-Processing
A rule-based system classifies the urgency (severity) of the condition using thresholds for Body Temperature (T) and Oxygen Saturation (O).

$$S = \begin{cases} \text{Severe} & \text{if } T > 39.0^\circ\text{C} \text{ or } O < 92\% \\ \text{Moderate} & \text{if } T > 38.0^\circ\text{C} \text{ or } O < 95\% \\ \text{Mild} & \text{Otherwise} \end{cases} $$## 📊 Datasets This project uses three datasets to train and provide context: 1. `disease_diagnosis.csv`: Contains patient vitals, symptoms, and diagnoses. 2. `diabetes_data_upload.xls`: A detailed dataset for training the diabetes risk model. 3. `healthcare_dataset.csv`: Used to provide contextual information on common medications for diagnosed conditions. ## 🚀 Getting Started Follow these instructions to set up and run the project locally. ### Prerequisites - Python 3.8 or higher - pip (Python package installer) ### Installation 1. **Clone the repository:** ```sh git clone https://github.com/anurags1904/Healthcare-Diagnosis-System.git cd Healthcare-Diagnosis-System ``` 2. **Create and activate a virtual environment (recommended):** ```sh # For Windows python -m venv venv venv\Scripts\activate # For macOS/Linux python3 -m venv venv source venv/bin/activate ``` 3. **Install the required dependencies:** Create a `requirements.txt` file with the following content and run the installation command. **`requirements.txt`**: ``` pandas numpy scikit-learn matplotlib seaborn joblib openpyxl ``` **Installation command**: ```sh pip install -r requirements.txt ``` ## ⚙️ Usage The system requires a two-step process to run. 1. **First, run the training script** to train the models and create the necessary `.joblib` files. ```sh python model_training.py ``` This script will load the datasets, train the models, and save them to your local directory. 2. **Next, run the interactive health checkup script.** ```sh python health_checkup.py ``` This will launch the interactive form in your terminal. Follow the prompts to enter your information and receive your health report. ## 📁 File Structure ``` . ├── model_training.py # Script to train and save the models ├── health_checkup.py # Script to run the interactive health checkup ├── disease_diagnosis.csv # Dataset for general diagnosis ├── diabetes_data_upload.xls # Dataset for diabetes prediction ├── healthcare_dataset.csv # Dataset for contextual insights ├── requirements.txt # List of Python dependencies ├── disease_model.joblib # Saved model (generated after training) ├── diabetes_model.joblib # Saved model (generated after training) ├── *.joblib # Other saved encoders └── README.md # This file ``` ## 🤝 Contributors - **Anurag Singh** - **Puja Kumari**$$
