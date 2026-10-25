
# NYC Taxi Fare Prediction 🚕 

A machine learning regression project that predicts New York City taxi fares using trip details, geographical coordinates, and pickup time.

## 📌 Project Overview

This project explores the NYC Taxi Fare Prediction dataset and applies multiple machine learning algorithms to estimate taxi fares. It covers data preprocessing, exploratory data analysis, feature engineering, model training, and evaluation.

## 🎯 Objectives

- Analyze taxi trip data and identify features associated with taxi fares.
- Clean the data and handle invalid records and outliers.
- Engineer features from pickup time and geographical coordinates.
- Train and compare regression models.
- Evaluate model performance using Root Mean Squared Error (RMSE).

## 🛠️ Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- XGBoost
- Jupyter Notebook

## 📊 Machine Learning Workflow

1. Load and explore the dataset.
2. Prepare training and validation datasets.
3. Establish a baseline using mean fare prediction.
4. Train a Linear Regression model.
5. Engineer features:
   - Extract year, month, day, weekday, and hour from pickup datetime.
   - Calculate trip distance using the Haversine formula.
   - Calculate distances to selected landmarks.
6. Filter invalid records and outliers.
7. Train Ridge Regression, Random Forest, and XGBoost models.
8. Compare model performance using RMSE and explore hyperparameters.

## 🤖 Models Implemented

- Mean Baseline Regressor
- Linear Regression
- Ridge Regression
- Random Forest Regressor
- XGBoost Regressor

## 📁 Project Structure

```text
NYC-Taxi-Fare-Prediction/
├── data/
│   ├── train.csv
│   └── test.csv
├── nyc_taxi_fare_prediction.ipynb
├── README.md
└── requirements.txt
```

## 📂 Dataset

This project uses the [NYC Taxi Fare Prediction dataset on Kaggle](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction/data).

The dataset files are:

- `train.csv` — training data
- `test.csv` — test data

Download them from the Kaggle competition page and place them inside the local `data/` folder.

**Important:** The training dataset is approximately 5.5 GB. Do not upload it directly to GitHub. Download it separately from Kaggle when reproducing this project.

## ⚙️ Installation and Usage

### 1. Clone the repository

```bash
git clone https://github.com/samyak2305/NYC-Taxi-Fare-Prediction.git
cd NYC-Taxi-Fare-Prediction
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Download the dataset

Download `train.csv` and `test.csv` from Kaggle and place them inside the `data/` folder.

### 5. Update dataset paths

Make sure the notebook loads the files using the correct relative paths:

```python
train_path = "data/train.csv"
test_path = "data/test.csv"
```

Adapt these lines to your notebook's existing loading code if necessary.

### 6. Run the notebook

Open `nyc_taxi_fare_prediction.ipynb` in VS Code or Jupyter Notebook and execute the cells in order.

## 📈 Evaluation Metric

The models are evaluated using **Root Mean Squared Error (RMSE)**. A lower RMSE indicates more accurate predictions on the evaluation data.

Add the final model results after running the notebook and verifying the metrics.

## 🔍 Key Learning Outcomes

- Exploratory data analysis and data cleaning
- Feature engineering for date/time and geographical data
- Regression algorithms and ensemble learning
- Model evaluation and hyperparameter tuning
- Building an end-to-end machine learning workflow

## 👨‍💻 Author

**Samyak Gaikwad**

GitHub: [@samyak2305](https://github.com/samyak2305)

## 🙌 Acknowledgements

- freeCodeCamp for the machine learning learning resource
- Kaggle for the NYC Taxi Fare Prediction dataset
