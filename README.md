# Public-Transport-Forecasting-and-Insight-Analysis
This project uses time series analysis with a *SARIMAX* model to analyze and forecast daily passenger journeys for a public transport system.

The analysis is performed on a dataset containing daily ridership broken down by service type (Local, Light Rail, Peak, etc.). The goal is to understand ridership patterns and build a reliable model to forecast future demand.

Key Insights from the Analysis
* A Tale of Two Systems (Week vs. Weekend):* The transport network operates like two different systems. Ridership on School and Peak Service routes *drops to zero* on weekends, indicating they are pure "commuter" services.
* The Network's Core:* Local Route and Rapid Route are the system's backbone, carrying the vast majority of passengers.
* The 7-Day Cycle is King:* The data is dominated by a powerful 7-day weekly seasonality. The success of the SARIMAX model with seasonal_order=(...,7) confirms this is the most important predictive feature.
* Robust Validation:* The model's performance is validated using two separate methods: a 14-day holdout (for short-term accuracy) and a 60/30/10 train/val/test split (for generalizability).

Project Structure
This project is contained in a single Jupyter Notebook (Public-Transport-Forecasting-and-Insight-Analysis.ipynb) and is organized into the following steps:

1.  Import Libraries: Imports pandas, numpy, matplotlib, statsmodels, and sklearn.
2.  Load & Explore: Loads the CSV file, parses dates, and cleans column names.
3.  Generate Key Insights:
    * Calculates total ridership by service.
    * Analyzes and plots average ridership by day of the week.
    * Plots 30-day rolling averages to identify long-term trends.
    * Computes a correlation matrix between services.
4.  SARIMAX Forecasting:
    * A SARIMAX(1,1,1)(1,0,1,7) model is trained individually for each service type.
    * A 7-day forecast is generated for each service.
5.  Prepare Output Table: The 7-day forecasts are combined and saved.
6.  Model Evaluation: The model's accuracy is rigorously tested using two backtesting strategies (14-day holdout and train/val/test split) with MAE and RMSE metrics.


Outputs
This project generates three key files:

* 7_day_forecast_results.csv: The 7-day passenger forecast for each service.
* model_backtest_metrics.csv: Performance metrics (MAE, RMSE) from the 14-day backtest.
* model_backtest_train_val_test_metrics.csv: Performance metrics from the train/val/test split.
