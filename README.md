# udacity-blog-post

## Introduction
This file illustrates on a high level process steps of CRISP-DM in terms of analysing price-forming attributes on Airbnb. This is a high level description, you may find more technical details in the seattle-udacity-blog.ipynb file. In addition, summary of this research was reflected in this [blog post](https://medium.com/@ruzannavt/analyzing-seattle-airbnb-data-5366abe71670)

## Business Problem
As Airbnb business and home owners we would like to understand what are the key factors that are affecting property prices, analyse what features can be used to predict pricing. This information might be helpful for all parties of AirBNB renting process and at the end increase profit. 
Given that this topic is quite complex and may contain wide range of questions, for Udacity research purposes it was decided to limit the topic to 3 questions: 

- Are there seasonal differences in pricing?
- Do reviews and cancellation policy impact prices?
- Can information from reviews and house descriptions be useful in predicting pricing groups?

Answers to all above questions resulted in the conclusion to following topic: what features can be used to predict pricing groups. 

## Data Understanding and Data Preparation
Data was taken from Kaggle repository and can be found [here](https://www.kaggle.com/airbnb/seattle/data). It contains 3 csv files: calendars, listings and reviews. Prior to starting data analysis, those files required some data cleaning, e.g. deleting records with N/A prices in calendar file (reasoning provided in ipynb file.

## Modeling
We used various methods and models to perform required analysis, e.g. 
- correlation analysis and chi-square to define potential correlation between price and season; 
- gradient boosting was used during classification and feature selection that have greatest impact on price formation; 
- substring search performed to search for specific mentions of certain words in reviews and homes' descriptions.
More details on implemented methods can be found in work file (seattle-udacity-blog.ipynb).

## Evaluation and conclusion 
After performing required steps in data cleaning, analysis and modelling we came up with several conclusions. 

### 1- Are there seasonal differences in pricing?
Even though distribution of prices during 4 seasons is almost identical, we did spotted interesting behaviour: 1) those listings of low price get even cheaper in summer (to compete for clients) and more expensive in autumn and winter (to earn money), 2) those listings of high prices get even more expensive in summer (to earn money) and cheaper in other seasons (to keep the clients).
![seasoning](https://github.com/ruzannaT/udacity-blog-post/blob/main/distribution.png)

### 2 - Do reviews and cancellation policy impact prices?

To answer this question, we retrieved reviews_per_month, review_scores_value and cancellation_policy features from listings file.
Before performing correlation analysis we visualised distribution of prices against review: it showed that there might be some correlation. 
![correlation](https://github.com/ruzannaT/udacity-blog-post/blob/main/correlation.png)
After running correlation analysis, turned out that review_scores_value does not correlate with pricing, but **reviews_per_month has a significant negative correlation (r=-0.21)**. 

Taking about potential impact of cancelation policies on prices, we came to the conclusion that yes, indeed, policy does have impact on prices.
After performing statistical tests, the chi-squared formally confirmed that the variables in the table are not independent.

### 3 - What features can be used for price predictions

To answer this question we performed semantic text analysis in combination with gradient boosting to define features that has significant impact on pricing. 
Below you may find list of top 15 most important features:
![top features](https://github.com/ruzannaT/udacity-blog-post/blob/main/top_features.png)
