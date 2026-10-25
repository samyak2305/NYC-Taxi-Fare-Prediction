# NYC Taxi Fare Prediction 🚕

A machine learning regression project that predicts New York City taxi fares from trip coordinates, pickup time, passenger count, trip distance, and proximity to selected landmarks.

**Best recorded validation RMSE: 3.9825 (XGBoost)**

## Project Overview

This project explores the Kaggle NYC Taxi Fare Prediction dataset and compares regression models for estimating taxi fares. The notebook covers data exploration, cleaning, feature engineering, model training, evaluation, and XGBoost hyperparameter exploration.

## Dataset

The notebook's saved outputs show an initial working sample of **552,450 training rows** and **9,914 competition test rows**. The model evaluation after feature engineering and filtering used **431,098 training rows** and **107,742 validation rows**.

Download the dataset from the [Kaggle NYC Taxi Fare Prediction competition](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction/data).

Keep the large CSV files locally; they are not included in this GitHub repository. If your files are in the `data/` folder, update the notebook paths to `data/train.csv` and `data/test.csv` as needed.

## Workflow

1. Load and inspect the training and competition test data.
2. Split the training sample into training and validation sets.
3. Establish a mean-prediction baseline and evaluate an initial linear regression model.
4. Extract pickup year, month, day, weekday, and hour from the pickup timestamp.
5. Calculate trip distance using the Haversine formula.
6. Calculate drop-off distances to five landmarks:
   - John F. Kennedy International Airport (JFK)
   - LaGuardia Airport (LGA)
   - Newark Liberty International Airport (EWR)
   - Metropolitan Museum of Art (MET)
   - World Trade Center (WTC)
7. Filter implausible fares, coordinates, and passenger counts.
8. Train and compare Ridge Regression, Random Forest, and XGBoost.
9. Explore XGBoost hyperparameters using training and validation RMSE.

## Models and Results

The following metrics are taken from the notebook's saved outputs. **RMSE (Root Mean Squared Error)** measures prediction error in fare units; lower is better.

### Models after feature engineering and filtering

| Model | Training RMSE | Validation RMSE |
|---|---:|---:|
| Ridge Regression (`alpha=0.9`) | 5.0493 | 5.2178 |
| Random Forest (`50` trees, `max_depth=10`) | 3.5979 | 4.1630 |
| XGBoost (default estimator settings, `random_state=42`) | 3.1158 | 4.0137 |
| **Final XGBoost** (`500` estimators, `max_depth=5`) | **3.1858** | **3.9825** |

The final XGBoost configuration uses:

- `n_estimators=500`
- `max_depth=5`
- `learning_rate=0.1`
- `subsample=0.8`
- `colsample_bytree=0.8`
- `objective="reg:squarederror"`
- `random_state=42`
- `n_jobs=-1`

### Initial Baseline (Before Feature Engineering)

| Model | Training RMSE | Validation RMSE |
|---|---:|---:|
| Mean fare baseline | 9.7898 | 9.9000 |
| Linear Regression | 9.7886 | 9.9000 |

These baseline results come from an earlier stage and a different data split, so they should be treated as an initial reference rather than a perfectly controlled comparison.

### Key Findings

- The final XGBoost model achieved the lowest recorded validation RMSE among the feature-engineered models: **3.9825**.
- It slightly outperformed the earlier XGBoost model (**4.0137**) and Random Forest (**4.1630**) on validation RMSE.
- Feature engineering included pickup-time components, Haversine trip distance, and distances to selected landmarks.
- The notebook explores XGBoost hyperparameters including estimator count, tree depth, and learning rate.

> These metrics are from saved notebook outputs, not a fresh rerun. Results may change with different data, filtering, splits, library versions, or model settings. The competition test dataset has no fare labels, so the validation RMSE is not a Kaggle test-set score.

## Technologies Used

- Python
- NumPy
- pandas
- Matplotlib
- scikit-learn
- XGBoost
- Jupyter Notebook

## Project Structure

```text
NYC-Taxi-Fare-Prediction/
├── data/                         # Local dataset files; not committed
│   ├── train.csv
│   └── test.csv
├── nyc_taxi_fare_prediction.ipynb
├── README.md
└── requirements.txt
```

## Setup and Usage

### 1. Clone the Repository

```bash
git clone https://github.com/samyak2305/NYC-Taxi-Fare-Prediction.git
cd NYC-Taxi-Fare-Prediction
```

### 2. Create and Activate a Virtual Environment

**Windows PowerShell:**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Download the Dataset

Download `train.csv` and `test.csv` from the [Kaggle competition page](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction/data).

Place them in your local data directory and ensure the notebook's file paths match their location. Do not commit the large CSV files to GitHub.

### 5. Run the Notebook

Open `nyc_taxi_fare_prediction.ipynb` in VS Code or Jupyter Notebook and run the cells in order.

## Limitations

- Results are based on saved notebook outputs and should be rechecked after a fresh, end-to-end execution.
- Filtering rules for invalid fares and geographic coordinates affect the evaluation dataset.
- Validation RMSE is not a score on the unlabeled competition test set.
- The dataset is governed by Kaggle's competition terms.

## Author

**Samyak Gaikwad**  
GitHub: [@samyak2305](https://github.com/samyak2305)

## Repository

[NYC-Taxi-Fare-Prediction](https://github.com/samyak2305/NYC-Taxi-Fare-Prediction)