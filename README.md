![Main Image Banner](https://raw.githubusercontent.com/Drook93/Global-Video-Game-Sales/main/Tableau%20Dashboard/Images%20%26%20Videos/Video%20Game%20Sales%20Banner-1.png)
- Building Tableau dashboard using Kaggle dataset for Global Video Game Sales. - Building and testing predictive model for time series forecasting using Profit, carrying ETL and EDA.
<div align="center">

1. **Data Preparation**🧹🪣:
   - Load consumer spending and CPIH data.
   - Calculate percentage changes for spending and inflation.
   - 

2. **Prophet Time Series Forecasting**🔎:

 ![Prophet Forecast Viz](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Forecast.png)
  - Visuals: Bar chart of Globals Video Game Sales using seaborn and matplotlib (actual vs. forecasted).

 ![Importing Libraries](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%201.png)
- Imported relevant libraries such as pandas (for data manipulation), numpy (for arrays and matrices) and for visualisation seaborn and matplotlib.
  Also imprted prophet with cross validation along with required performance metrics.
  
 ![Training Model](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%203.png)
   
 - Trained on Kaggle data → forecasted 1 year total sum ahead of time.
 - Carried out train test split 80/20 ready to test the model's performance
 - Executed model.predict to forecat the range of included for the full year of 2017.

 ![Evaluating Metrics](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%205.png)
 - I decided to tune the model after identifying the metrics using the following:
 changepoint_prior_scale=0.001,
    seasonality_prior_scale=0.001,
    yearly_seasonality=False,
    weekly_seasonality=False,
    daily_seasonality=False,
 - Tweaking hyperparameters (like Prophet's seasonality_mode, changepoint_prior_scale)
 - Evaluated the models metrics of RMSE, MAE from the training data and contrasted agains the test metrics of MAPE and MASE.
 - After careful evaultion, I tweaked metrics to improve model performance, the data set was small with clear linear trends.
 - The results show that the model was overfitting and the results were blowing up on the test set.

![](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard/Images%20%26%20Videos/Prophet%20Image%20Screenshot%206.png)
-
 - MAE: ~5% on test set, low error on peak seasons.
 - Visuals: Tableau dashboard + animated GIF (actual vs. forecast).


 **Prophet Time Series Findings**🔎:
 
Overfitting Insight
Dataset was tiny + mostly linear → Prophet overfitted noise.

Tuning Attempts

Turned off daily, weekly, and yearly seasonality (all set to False).
Set growth to linear.
Cranked seasonality_prior_scale down to 0.001.
Set changepoint_prior_scale to 0.001.
Result: Still overfit—train MAE/RMSE ≈ 0, test MAPE ~2300%, RMSE ~3,891.

Train: MAE/RMSE ≈ 0% (perfect fit, too perfect).
Test: MAPE exploded to ~2300%, RMSE hit 3.89k.
Tuned changepoint_prior_scale, seasonality_mode—still no dice.
Lesson: Prophet needs bigger, noisier data. On this set? Overkill. Would've done better with plain old linear regression or exponential smoothing.

## Video Game Sales Dashboard🖥️
![Tableau Dashboard/Images & Videos/Tableau Dashboard gif.gif](https://github.com/Drook93/Global-Video-Game-Sales/blob/main/Tableau%20Dashboard%20gif.gif))


</div>
