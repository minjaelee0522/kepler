# Predictive Modeling Order Volume
## Minjae Lee, January 10 2022

### Introduction
One of Kepler's clients, Shazamazon, is an eCommerce retail store selling custom-made thingamabobs. Kepler's media team has been tasked with driving more Shazamazon orders to help them get a bigger foothold in the market. But before we start spending our client's money on advertising, we want to better understand what sorts of customer behaviors drive order volume so that our media team can target the most impactful parts of the customer journey.

At Kepler's request, Shazamazon provided the attached data set showing daily order volume across each of their target regions, along with the number of emails customers have opened, the average purchase value for each order, the number of social media likes, and the number of website visits. Despite being a retail provider, Shazamazon has confirmed that they never see seasonal variations in order volume, nor do they see any meaningful difference across regions.

As part of the Data Science team, you have been tasked with making sense of this data. Please create a model from this data set that can be used to predict order volume.

### Question
1. Final model equation

Answer: 
y = -3622.116230540076 + 0.0053585830697358795 * x0 + 0.34944136161492667 * x1 + 0.005764144902631139 * x2 - 0.027531986680644837 * x3 + 0.00018973927164358625 * x4 + 0.0019008713478966186 * x5


2. predicted number of orders given the following information: date = 2021-01-15, region_id = 7, email_opens = 10449, avg_order_value = 48.02, social_likes = 447, total_site_visits = 282887

Answer: 930.64331129


3. A high-level, step-by-step explanation of how you developed your model and why you took that step

Answer: There was no missing value, the most important part of the EDA process. The correlation between total_orders and the rest of the features was investigated, and total_site_visits and email_opens were overwhelmingly high. This is a very bad case because a small number of features determine the model by a large difference. Also, seasonal variation and no differences across regions were found, but upon investigation, there was no significant effect. Then I looked at the outelier, and the date, avg_order_value, and social_likes showed a similar distribution as if they were copied, so the rows with outliers were removed. And multicollinearity problem came up in the process of investigation using OLS. Also, it was expected that it would not be easy to make a good model due to the high P-value of other features except for email_opens and total_site_visits. The model was created using Ridge regularization, which is the best for multicollinearity, but the result was not significantly different from LinearRegression. I tried all regressors through Pipeline, but got similar or worse results. In the end, LinearRegression and Ridge gave the best results. The feature composition of the data was too biased, resulting in unsatisfactory results, and as always, I experienced the importance of EDA and Data Preprocessing once.


4. An explanation for why you chose this model

Answer: I selected multiple linear regression method because it can be used to capture important relationships between the forecast variable of interest and the predictor variables. Unfortunately, as a result, LinearRegression() produced the best results. Ridge is known to be the best solution for multicollinearity, so I expected it, but it didn't make much of a difference. It seems that there was a lack in EDA and data preprocessing process. After submission, I will review it carefully again without giving up.

