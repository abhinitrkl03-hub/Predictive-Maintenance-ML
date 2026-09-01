# Machine Predictive Maintenance Classification

## 📌 Project Overview

Machine Predictive Maintenance Classification is a machine learning project designed to predict whether a machine is likely to experience a failure based on its operating conditions.

The project uses machine sensor and operating parameters such as air temperature, process temperature, rotational speed, torque, tool wear, and machine type. Several classification algorithms were evaluated, and **Random Forest Classifier** was selected as the final model based on its test performance.

A **Streamlit web application** is also developed to allow users to enter machine parameters and receive a failure prediction interactively.

---

## 🎯 Objectives

The main objectives of this project are:

* Analyze machine operating and sensor data.
* Perform data preprocessing and exploratory analysis.
* Encode categorical machine-type information.
* Build and compare multiple machine learning classification models.
* Select an appropriate model based on classification performance.
* Save the trained model using Joblib.
* Develop an interactive Streamlit application for real-time predictions.

---

## 📊 Dataset

The dataset contains **10,000 observations and 10 columns**. The available variables include:

| Feature                 | Description                   |
| ----------------------- | ----------------------------- |
| UDI                     | Unique data identifier        |
| Product ID              | Product identifier            |
| Type                    | Machine/product type          |
| Air temperature [K]     | Air temperature in Kelvin     |
| Process temperature [K] | Process temperature in Kelvin |
| Rotational speed [rpm]  | Machine rotational speed      |
| Torque [Nm]             | Machine torque                |
| Tool wear [min]         | Tool usage/wear time          |
| Target                  | Binary failure indicator      |
| Failure Type            | Type of machine failure       |

## The dataset contains three machine types: **L, M, and H**, and the analysis found **no missing values**.

## 🔍 Machine Learning Workflow

The project follows the following workflow:

```text
Dataset
   ↓
Data Exploration
   ↓
Data Preprocessing
   ↓
Feature Selection
   ↓
Ordinal Encoding
   ↓
Train-Test Split
   ↓
Model Training
   ↓
Model Comparison
   ↓
Random Forest Selection
   ↓
Model Serialization
   ↓
Streamlit Deployment
```

### 1. Data Preprocessing

The `Type` feature is categorical and contains three ordered categories:

```text
L → 0
M → 1
H → 2
```

An `OrdinalEncoder` was used with the category order `['L', 'M', 'H']`.

The dataset was divided into:

* **80% Training Data**
* **20% Testing Data**

using `train_test_split` with `random_state=42`.

---

## 🤖 Models Evaluated

The following classification algorithms were tested:

1. Logistic Regression
2. Decision Tree Classifier
3. Random Forest Classifier
4. Support Vector Machine (SVM)

### Model Performance

| Model               | Training Accuracy | Test Accuracy |
| ------------------- | ----------------: | ------------: |
| Logistic Regression |            98.22% |        97.75% |
| Decision Tree       |           100.00% |        97.45% |
| Random Forest       |           100.00% |    **98.25%** |
| SVM                 |            96.58% |        96.85% |

The Random Forest model achieved the highest test accuracy among the evaluated models at **98.25%**.

> **Note:** The dataset is highly imbalanced across failure classes. Therefore, accuracy alone should not be considered sufficient for evaluating the model. The classification report shows substantially weaker performance for some minority failure classes.

---

## 🌲 Final Model

The final model is a:

**Random Forest Classifier**

with:

```python
RandomForestClassifier(n_estimators=100)
```

## The trained model was saved using Joblib for use in the Streamlit application.

## 🖥️ Streamlit Application

The project includes an interactive Streamlit application where users can enter machine operating parameters.

The application accepts:

* Machine Type
* Air Temperature [K]
* Process Temperature [K]
* Rotational Speed [rpm]
* Torque [Nm]
* Tool Wear [min]

The application then uses the trained model to generate a prediction.

The prediction is triggered using the **Predict Failure** button.

---

## 📁 Project Structure

```text
Machine-Predictive-Maintenance/
│
├── app.py
├── predictive_maintenance.csv
├── model.joblib
├── Machine_Predictive_Maintenance_Classification.ipynb
├── requirements.txt
└── README.md
```

### File Description

| File                                                  | Description                                                          |
| ----------------------------------------------------- | -------------------------------------------------------------------- |
| `app.py`                                              | Streamlit application for machine failure prediction                 |
| `predictive_maintenance.csv`                          | Dataset used for model development                                   |
| `model.joblib`                                        | Trained Random Forest model                                          |
| `Machine_Predictive_Maintenance_Classification.ipynb` | Complete data analysis, preprocessing, model training and evaluation |
| `requirements.txt`                                    | Python dependencies                                                  |
| `README.md`                                           | Project documentation                                                |

---

## ⚙️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Joblib**
* **Streamlit**
* **Google Colab / Jupyter Notebook**

The Streamlit application uses Streamlit and Scikit-learn as listed in the project's requirements file.

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Machine-Predictive-Maintenance.git
cd Machine-Predictive-Maintenance
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

### 3. Activate the environment

**Windows:**

```bash
venv\Scripts\activate
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

The project currently specifies Streamlit `1.21.0` and Scikit-learn in `requirements.txt`.

---

## ▶️ Run the Application

Make sure `app.py` and the trained model file are in the same directory.

Then run:

```bash
streamlit run app.py
```

The application will open in your browser.

---

## 🧪 Example Input

You can provide values such as:

```text
Type: Medium
Air Temperature: 300.0 K
Process Temperature: 310.0 K
Rotational Speed: 1500 rpm
Torque: 45 Nm
Tool Wear: 100 min
```

After entering the values, click:

```text
Predict Failure
```

The application returns the model's prediction.

---

## 📈 Results

The Random Forest classifier achieved:

```text
Training Accuracy : 100.00%
Test Accuracy     : 98.25%
```

The model performed particularly well on the majority **No Failure** class, while performance on several minority failure classes was lower due to the strong class imbalance present in the dataset.

---

## 🔮 Future Improvements

The project can be further improved by:

* Handling the significant class imbalance using techniques such as SMOTE or class weighting.
* Optimizing Random Forest hyperparameters using GridSearchCV or RandomizedSearchCV.
* Comparing additional ensemble models such as XGBoost and Gradient Boosting.
* Adding probability/confidence scores to the Streamlit application.
* Improving input validation in the Streamlit interface.
* Adding confusion matrix and feature-importance visualizations to the application.
* Deploying the Streamlit application using a cloud platform.
* Using a complete preprocessing pipeline so that training-time transformations are consistently applied during inference.

---


If you found this project useful, consider giving the repository a ⭐.
