Medical-Heart-Disease-End-2-End-Predictor

An end-to-end machine learning project that predicts whether a patient is likely to have heart disease from routine clinical measurements. It covers the full pipeline: data ingestion, cleaning, feature engineering, model training and evaluation, and deployment as a web app that returns an instant risk prediction.

Disclaimer: This tool is for educational and decision-support purposes only. It is not a substitute for professional medical diagnosis or advice.

Table of Contents
Problem Statement
Input Features
Output
Pipeline
Tech Stack
Project Structure
Installation
Usage
Results
Docker
Key Benefits
Future Work
Contributing
License
Problem Statement

Heart disease is one of the leading causes of death worldwide, and early detection greatly improves outcomes. This project uses patient data to classify each person as at risk or not at risk, giving clinicians and users a fast, data-driven screening aid.

Input Features
Feature	Description
age	Age of the patient
sex	Sex of the patient
cp	Chest pain type
trestbps	Resting blood pressure
chol	Serum cholesterol
fbs	Fasting blood sugar
restecg	Resting ECG results
thalach	Maximum heart rate achieved
exang	Exercise-induced angina
oldpeak	ST depression induced by exercise
slope	Slope of the peak exercise ST segment
ca	Number of major vessels
thal	Thalassemia result
Output

A binary prediction (heart disease: yes / no) along with a probability score showing how confident the model is.

Pipeline
Data collection and exploration: Load the dataset (e.g., UCI Heart Disease), then analyze distributions, correlations and class balance.
Preprocessing: Handle missing values and outliers, encode categorical variables and scale numeric features.
Feature engineering and selection: Keep the most predictive features and reduce noise.
Model training: Compare Logistic Regression, Random Forest, XGBoost, SVM and KNN, with hyperparameter tuning and cross-validation.
Evaluation: Accuracy, precision, recall, F1-score, ROC-AUC and confusion matrix. Recall is prioritized so that few true patients are missed.
Deployment: The best model is saved with joblib and served through a Streamlit web app.
Monitoring and CI/CD (optional): Containerize with Docker and deploy to the cloud.
Tech Stack
Language: Python
Data: Pandas, NumPy
ML: Scikit-learn, XGBoost
Visualization: Matplotlib, Seaborn
Deployment: Streamlit
DevOps: Docker
Project Structure
Medical-Heart-Disease-End-2-End-Predictor/
├── data/
│   └── raw/
│       └── heart.csv          # Dataset
├── models/                    # Saved model, metrics and plots
├── src/
│   ├── features.py            # Data loading and preprocessing
│   ├── train.py               # Training, tuning and evaluation
│   └── predict.py             # Inference helper
├── app.py                     # Streamlit web app
├── requirements.txt
├── Dockerfile
└── README.md
Installation
bash
# Clone the repository
git clone https://github.com/<your-username>/Medical-Heart-Disease-End-2-End-Predictor.git
cd Medical-Heart-Disease-End-2-End-Predictor

# Create a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
Usage

1. Add the dataset

Download the Heart Disease dataset (UCI or Kaggle) and place it at data/raw/heart.csv.

2. Train the model

bash
python src/train.py --data data/raw/heart.csv

This compares all models, saves the best one to models/model.joblib and writes metrics to models/metrics.json.

3. Run the web app

bash
streamlit run app.py

Open the app in your browser, enter the patient details and get an instant prediction with a probability score.

Results
Model	Accuracy	Precision	Recall	F1	ROC-AUC
Logistic Regression	-	-	-	-	-
Random Forest	-	-	-	-	-
XGBoost	-	-	-	-	-
SVM	-	-	-	-	-
KNN	-	-	-	-	-

Fill in the table with the metrics from models/metrics.json after training.

Docker
bash
docker build -t heart-disease-predictor .
docker run -p 8501:8501 heart-disease-predictor
Key Benefits
Fast, low-cost preliminary screening
Supports early diagnosis and clinical decision-making
Reproducible, deployable pipeline from raw data to a live app
Future Work
Add model explainability (SHAP / LIME)
Validate on larger and more diverse datasets
Add monitoring for data drift
Set up CI/CD and cloud deployment
Contributing

Contributions are welcome. Please open an issue first to discuss what you would like to change, then submit a pull request.

License

This project is licensed under the MIT License. See the LICENSE file for details.
