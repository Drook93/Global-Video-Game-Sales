![Main Image Banner](https://raw.githubusercontent.com/Drook93/Global-Video-Game-Sales/main/Tableau%20Dashboard/Images%20%26%20Videos/Video%20Game%20Sales%20Banner-1.png)
<div align="center">
 
This project forecasts global video game sales and using Prophet model on Kaggle's dataset which included the following features: Game-Name, Platform, Release Year, Genre, Publisher, Global Sales and Regional Sales breakdown. I cleaned the data in pandas. Built, trained/tuned Prophet and ran developed a Tableau dashboard for the findings. Utilised the native forecasting tool to predict one year ahead into 2017, then compared it against Prophet's metrics.
↓↓↓Below shows a breakdown in further details of the steps I took.↓↓↓

</div>

<div align="center">
 
## Video Game Sales Dashboard🖥️
</div>

<img src="your-gif-link.gif" width="600" alt="Sharp Demo">
<div align="center">
  <img src="https://raw.githubusercontent.com/Drook93/Global-Video-Game-Sales/main/Tableau%20Dashboard%20gif.gif" 
       alt="Tableau Dashboard GIF" 
       style="width: 80%; max-width: 2000px; height: auto;">
</div>

----------------------------------------------------------------------------------------------------------
 **Data Preparation**🧹🪣:


----------------------------------------------------------------------------------------------------------
 **Prophet Time Series Forecasting**🔎:
 
- Bar chart of Globals Video Game Sales using seaborn and matplotlib (actual vs. forecasted).
  
 ![Prophet Forecast Viz](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Forecast.png)

- Imported relevant libraries such as pandas (for data manipulation), numpy (for arrays and matrices) and for visualisation seaborn and matplotlib.
  Also imprted prophet with cross validation along with required performance metrics.
  
 ![Importing Libraries](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%201.png)
 - Aggregated data up to 2016 at time period. Few samples of data in 2017 needed to be excluded.
 - Trained on Kaggle data → forecasted 1 year total sum ahead of time.
 - Carried out train test split 80/20 ready to test the model's performance
 - Executed model.predict() to forecast the full year of 2017.
   
 ![Training Model](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%2021.png)
  - I decided to tune the model after identifying the metrics using the following:
 changepoint_prior_scale=0.01,
    seasonality_prior_scale=0.1,
    yearly_seasonality=False,
    weekly_seasonality=False,
    daily_seasonality=False,
    growth='linear')
 - Evaluated the models metrics of RMSE, MAE from the training data and compaired against the test metrics with included MAPE and MASE.
   
 ![Evaluating Metrics](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%20updated%201.png)

-----------------------------------------------------------------------------------------------------------
 **Prophet Time Series Findings**🔎:
 
Overfitting Insight
Dataset was tiny and mostly linear and Prophet overfitted to noise.

Tuning Attempts:

Turned off daily, weekly, and yearly seasonality (all set to False).
Set growth to linear.
Seasonality_prior_scale to 0.1.
Set changepoint_prior_scale to 0.01.

Train: MAE/RMSE (generalised well):
RMSE: 82.29
MAE:  68.10
Prophet Accuracy Metrics (Test set):
RMSE: 202.20
MAE:  170.35
MAPE: 105.28%
MASE: 1.97
Test: MAPE too high.
Lesson: Prophet needs bigger, noisier data. This shows clear signs of overfitting. On this set it was not the right fit; a better suited model like linear regression or SARIMA would have given better results.

The image below shows the results of the cross validation which looks good on the surface, but final test errors were far off↓↓↓
![Cross Val Metrics](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%206.png)

----------------------------------------------------------------------------------------------------------
