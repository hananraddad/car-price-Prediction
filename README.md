# 🚗 Used Car Price Prediction

A Machine Learning project that predicts the price of a used car based on its specifications.

The project covers the complete workflow, starting from data analysis and preprocessing, to model training, API development, and a simple web interface.

## 📊 Dataset

The dataset contains **19,237 used cars** with **18 features**.

After data cleaning and removing duplicates and outliers, **16,037 records** were used for the final modeling process.

## 🔍 Exploratory Data Analysis

The EDA included:

* Checking data types and missing values
* Removing duplicate records
* Cleaning numerical columns
* Detecting and handling outliers using the **IQR method**
* Exploring relationships between features and car prices
* Using visualizations such as KDE plots, boxplots, pairplots, and correlation heatmaps

## ⚙️ Data Preprocessing

The preprocessing pipeline included:

* Removing duplicate records
* Cleaning `Levy`, `Engine Volume`, and `Mileage`
* Removing extreme outliers
* Creating a new feature: **Age**
* Removing unnecessary columns such as `ID`, `Doors`, and `Prod. year`
* Encoding categorical features
* Scaling numerical features

### Encoding

Two encoding approaches were tested:

* **One-Hot Encoding**
* **Label Encoding**
* **Target Encoding** was also tested during model comparison.

### Scaling

`StandardScaler` was applied to numerical features, with the scaler fitted only on the training data to avoid **data leakage**.

## 🤖 Model Experiments

Different approaches were compared using Linear Regression and Random Forest.

| Approach        | Model             |  RMSE |   R² |
| --------------- | ----------------- | ----: | ---: |
| Label Encoding  | Linear Regression | 9,841 | 0.22 |
| Label Encoding  | Random Forest     | 5,530 | 0.75 |
| Target Encoding | Linear Regression | 8,119 | 0.47 |
| Target Encoding | Random Forest     | 5,630 | 0.74 |

Based on the results, **Label Encoding + Random Forest** was selected for the final model.

## ✅ Final Results

The final model was trained using:

* **Model:** RandomForestRegressor
* **Training data:** 13,631 samples
* **Test data:** 2,406 samples
* **RMSE:** ≈ 5,388
* **R²:** ≈ 0.777

The model achieved approximately **77.7% R²** on the test set.

## 🌐 API

The trained model was integrated into an API using **FastAPI**.

The API:

* Receives car specifications as JSON
* Validates inputs using Pydantic
* Applies the same preprocessing steps used during training
* Returns the predicted car price

### Endpoint

```text
POST /predict/
```

## 💻 Web Interface

A simple web interface was created using:

* HTML
* Bootstrap
* JavaScript

The user can enter the car specifications and receive the predicted price from the API.

## 📁 Project Structure

```text
Used-Car-Price-Prediction/
│
├── api/
│   └── main.py
│
├── notebooks/
│   ├── EDA.ipynb
│   ├── training.ipynb
│   ├── training-target-encoding.ipynb
│   ├── training-final.ipynb
│   └── first-stage.ipynb
│
├── preprocessing.py
├── index.html
├── requirements.txt
├── README.md
└── .gitignore
```

## 🛠️ Technologies

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* FastAPI
* Pydantic
* HTML
* Bootstrap
* JavaScript

---

### 👩‍💻 Author

**Hanan Raddad**

AI Student | Interested in Machine Learning, Data Analysis & Computer Vision
