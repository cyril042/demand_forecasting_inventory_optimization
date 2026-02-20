Demand Forecasting and Inventory Optimization Using Machine Learning

Project Overview
This project develops an end-to-end data science pipeline that forecasts retail product demand and converts those forecasts into optimal inventory decisions. The objective is not only to predict future demand but to minimize operational cost by determining economically optimal order quantities under uncertainty. 

The workflow integrates time series forecasting, machine learning, and operations research using the newsvendor model. Results demonstrate measurable improvements in both predictive accuracy and inventory cost efficiency.

Business Problem
Retail inventory management involves balancing two competing risks:
- Overstocking → excess holding cost
- Understocking → lost sales and stockout cost
Accurate demand forecasting alone does not solve this problem. Businesses must translate forecasts into optimal ordering decisions that minimize total expected cost.

This project addresses both components: Forecast daily product demand and determine cost-optimal inventory levels.

Dataset

In this project, we used Retail Store Item Demand Forecasting dataset (Kaggle). Each record represents daily sales of a product at a specific store. Features include Date, Store ID, Item ID, and Daily sales (target variable).

For modeling clarity and interpretability, a single time series (Store 1, Item 1) was selected for detailed analysis.

Methodology
1. Time Series Forecasting
Three forecasting approaches were evaluated:
- Naive persistence baseline
- Moving average model (captures short-term seasonality)
- Random Forest regression with lag features and rolling statistics

Performance was evaluated using:
Mean Absolute Error (MAE)
Root Mean Squared Error (RMSE)
Symmetric Mean Absolute Percentage Error (SMAPE)

2️. Feature Engineering for Machine Learning
Lag-based predictors were constructed to convert the time series into a supervised learning problem:
- Lag 1 day
- Lag 7 days
- Lag 30 days
- Rolling mean (7 days)
- Rolling standard deviation (7 days)
These features capture temporal dependence and local demand variability.

3️. Inventory Optimization — Newsvendor Model
Forecasted demand was used to compute optimal inventory levels.
The newsvendor model determines the order quantity that minimizes expected cost by balancing:
- Holding cost per unit
- Stockout cost per unit

Optimal inventory is determined by the critical ratio: 
Stockout Cost / (Stockout Cost + Holding Cost)
  
	​
Simulation with actual demand was used to compare the optimized policy with a naive mean-demand strategy.

Forecasting Results
Model	          MAE	      RMSE	        SMAPE
Naive baseline	5.944	     7.36	        31.31%
Moving average	4.34	     5.50	        22.45%
Random Forest	  4.295	     5.371	      22.59%

Machine learning reduced forecasting error by approximately 28% compared to naive prediction.

Inventory Optimization Results
Assumptions:
- Holding cost = 1 per unit
- Stockout cost = 5 per unit

Strategy	             InventoryLevel	       Total Cost
Mean-demand policy	   20.52	               1220.43
Newsvendor optimal	   24.45	               840.42

Cost reduction: 31.14%

Key Insights:
Machine learning significantly improves demand prediction accuracy. Moving average models capture seasonality effectively. Forecasts alone do not create value — decision optimization does. Cost-aware inventory policies substantially reduce operational expense.This project demo nstrates how predictive analytics can be embedded into real decision frameworks.
                                    
Business Impact
By integrating forecasting with decision optimization, the system converts predictive insights into operational policies that directly reduce cost. The optimized inventory strategy lowered total cost by over 31%, demonstrating measurable financial value from data-driven decision making.

Conclusion
This project illustrates that the true value of data science lies not only in prediction accuracy but in actionable decision support. By combining machine learning with economic optimization, demand forecasts were translated into inventory policies that significantly improve operational efficiency.

Author
Cyril Udeani
