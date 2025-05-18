🌦️ Weather Prediction Project
🌟 Overview
Welcome to the Weather Prediction Project! This exciting time-series forecasting project predicts the maximum daily temperature (tmax) for the next day using historical weather data up to May 14, 2025. It also generates 10-day-ahead forecasts (May 15–24, 2025) 📅. We leverage three powerful machine learning models: Ridge Regression, XGBoost, and Long Short-Term Memory (LSTM) neural networks 🧠. With clever feature engineering, we enhance prediction accuracy and evaluate models using Mean Absolute Error (MAE) and Mean Squared Error (MSE) 📊.
🎯 Objectives

Predict tomorrow's tmax using historical weather data 🌡️.
Craft features like rolling means, percentage differences, and seasonal averages to capture weather patterns 📈.
Compare the performance of Ridge Regression, XGBoost, and LSTM models ⚖️.
Forecast tmax for May 15–24, 2025, with trained models 🚀.

📚 Dataset

Source: A CSV file (4020986 copy.csv) packed with historical weather data, including:
tmax: Maximum daily temperature (our target) 🌞.
tmin: Minimum daily temperature 🌜.
prcp: Precipitation ☔.
Other features (e.g., name, station).


Time Range: Up to May 14, 2025 🕒.
Preprocessing 🧹:
Dropped columns with >5% missing values.
Forward-filled remaining missing data.
Standardized column names to lowercase and dates to datetime.
Created target as next day’s tmax using shift(-1).



✨ Features

Raw Features: tmax, tmin, prcp.
Engineered Features 🛠️:
Rolling Means: 3-day and 14-day averages for tmax, tmin, prcp 📉.
Percentage Differences: Relative changes from rolling means 📏.
Expanding Means: Monthly and day-of-year averages for seasonal trends 🌸.


Predictors: All features except target, name, and station.

🤖 Models

Ridge Regression 🧮:

Linear model with L2 regularization (alpha=0.1).
Great for capturing linear weather patterns.
Evaluated with a custom backtest function to preserve time-series order ⏳.


XGBoost 🌳:

Gradient-boosting model with Grid Search for tuning (n_estimators, max_depth, learning_rate, subsample).
Excels at non-linear relationships and feature interactions.
Uses the same backtest function 📋.


LSTM (Long Short-Term Memory) 🧬:

Recurrent neural network for sequential data with 10-day sequences.
Architecture: Two LSTM layers (50 units each), dropout (0.2), dense output layer.
Custom backtest_lstm function for sequence handling 🕸️.
Note: Computationally heavy; may be slow without GPU 🐢.



📊 Evaluation

Metrics: MAE and MSE to measure prediction accuracy 🎯.
Backtesting: Time-series-aware cross-validation (backtest) splits data starting at 3650 days with 90-day steps 🔄.
10-Day Predictions: Forecasts for May 15–24, 2025, saved to 10_day_predictions.csv 📅.

🛠️ Installation
Prerequisites

Python 3.8+ 🐍
Google Colab (recommended) or a local environment with GPU for LSTM ⚡

Dependencies
Install the required packages:
pip install pandas numpy tensorflow scikit-learn xgboost matplotlib seaborn

Setup

Clone the repository:git clone https://github.com/surocodes/Weather_Prediction.git
cd weather-prediction


Upload 4020986 copy.csv.zip to Google Colab or place it in the project directory 📂.
Run Weather_Prediction.ipynb in Colab or locally 🚀.

🚀 Usage

Run the Notebook:

Open weather_prediction.ipynb in Google Colab 📓.
Upload 4020986 copy.csv.zip when prompted.
Execute cells to:
Load and preprocess data 🧹.
Engineer features 🛠️.
Train and evaluate Ridge, XGBoost, and LSTM models 🤖.
Generate 10-day predictions 📅.




Outputs:

Model Performance: MAE and MSE printed during backtesting 📈.
Predictions: 10_day_predictions.csv with Ridge and XGBoost forecasts for May 15–24, 2025 📜.
Plots: Visuals of prediction errors and 10-day forecasts 📊.


Customization:

Tweak rolling_horizons (e.g., [3, 14]) for different rolling windows 🔧.
Adjust XGBoost param_grid for hyperparameter experiments 🎛️.
Modify LSTM seq_length (default: 10) or architecture for better results 🧪.



📁 Project Structure
weather-prediction/
├── weather_prediction.ipynb  # Main notebook with code 📓
├── 4020986 copy.csv.zip     # Dataset (upload to Colab) 📊
├── 10_day_predictions.csv   # Output: 10-day predictions 📜
├── README.md                # This file 📄

🤩Results

Ridge Regression: Stable, linear predictions but may miss complex patterns 🧮.
XGBoost: Often outperforms Ridge by modeling non-linearities 🌳.
LSTM: Captures sequential patterns but requires significant compute 🧬.
10-Day Predictions: Stored in 10_day_predictions.csv with a plot comparing Ridge and XGBoost 📅.

⚠️ Limitations

Data Assumptions: Future tmin and prcp for 10-day predictions use May 14, 2025, values, which may limit accuracy 📉.
LSTM Performance: Slow in Colab without GPU; consider acceleration ⚡.
Feature Dependencies: Rolling and expanding means depend on historical data, which may be sparse for some days 📅.

🔮 Future Improvements

Integrate external tmin and prcp forecasts for better 10-day predictions 🌦️.
Optimize LSTM with batch processing or pre-trained models 🧠.
Combine Ridge, XGBoost, and LSTM in an ensemble model 🤝.
Add prediction confidence intervals using bootstrap or uncertainty methods 📊.

🤝 Contributing
We love contributions! To get started:

Fork the repository 🍴.
Create a feature branch (git checkout -b feature/new-feature) 🌿.
Commit changes (git commit -m 'Add new feature') 💾.
Push to the branch (git push origin feature/new-feature) 🚀.
Open a pull request 📬.

📜 License
This project is licensed under the MIT License. See the LICENSE file for details.
🙌 Acknowledgments

Powered by Python, Pandas, Scikit-learn, XGBoost, TensorFlow, and Matplotlib 🐍.
Gratitude to the open-source community for amazing tools and libraries 🌟.
Dataset from historical weather records (source withheld for privacy) 📊.

📬 Contact
Questions or feedback? Open an issue on GitHub or email suraj2005jan@gmail.com 📧.


