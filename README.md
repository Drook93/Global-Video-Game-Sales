![Main Image Banner](https://raw.githubusercontent.com/Drook93/Global-Video-Game-Sales/main/Tableau%20Dashboard/Images%20%26%20Videos/Video%20Game%20Sales%20Banner-1.png)
<div align="center">
 
This project forecasts global video game sales and using Prophet model on Kaggle's dataset of about 16,600 rows which included the following columns:game name, platform, release year, genre, publisher, global sales, and regional sales breakdown. I cleaned the data in pandas trained Prophet and built and ran a Tableau dashboard and utilised the built in forecasting tool to predict one year ahead into 2017, then compared it against Prophet.

↓↓↓Below shows a breakdown in further details of the steps I took.↓↓↓

</div>
----------------------------------------------------------------------------------------------------------
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


 - Trained on Kaggle data → forecasted 1 year total sum ahead of time.
 - Carried out train test split 80/20 ready to test the model's performance
 - Executed model.predict() to forecast the full year of 2017.
   
 ![Training Model](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%202.png)

  - I decided to tune the model after identifying the metrics using the following:
 changepoint_prior_scale=0.001,
    seasonality_prior_scale=0.001,
    yearly_seasonality=False,
    weekly_seasonality=False,
    daily_seasonality=False,
 - Evaluated the models metrics of RMSE, MAE from the training data and contrasted agains the test metrics of MAPE and MASE.
   
 ![Evaluating Metrics](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%205.png)

-----------------------------------------------------------------------------------------------------------
 **Prophet Time Series Findings**🔎:
 
Overfitting Insight
Dataset was tiny and mostly linear and Prophet overfitted to noise.

Tuning Attempts:

Turned off daily, weekly, and yearly seasonality (all set to False).
Set growth to linear.
Cranked seasonality_prior_scale down to 0.001.
Set changepoint_prior_scale to 0.001.
Resulting in still overfit—train MAE/RMSE at 0, test MAPE ~2300%, RMSE ~3,891.

Train: MAE/RMSE ≈ 0% (too perfect fit).
Test: MAPE exploded to ~2300%, RMSE hit 3.89k.
Tuned changepoint_prior_scale, seasonality_mode.
Lesson: Prophet needs bigger, noisier data. On this set it was not the right fit. Would've done better with a old linear regression or exponential smoothing model.

The image below shows the results of the cross validation which looks good on the surface, but final test blew up↓↓↓
![](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%206.png)

----------------------------------------------------------------------------------------------------------
