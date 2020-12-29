# Online Auction End Price Prediction: Project Overview
- Created a tool that estimates the closing price in an online auction (MAE~ rs. 120) to help the sellers choose an appropriate opening bid or even decide to not auction the item at all.
- Scrapped over 1000 auctions data from the website DPHI
- Feature engineered from the name of the bidders the length of the bidder's name, and the email websites that they use.
- Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model.

# Code and Resources Used
- Python Version: 3.7
- Packages: Numpy, pandas, matplotlib, sklearn, seaborn, statsmodels
- Scraper Data: https://raw.githubusercontent.com/dphi-official/Datasets/master/auction_data/train_set_label.csv

# Dataset Description
  With each auction, we got the following:
- Auction Id - Unique identifier of an auction
- Bid - The proxy bid placed by a bidder
- Bid time - The time (in days) that the bid was placed, from the start of the auction
- Bidder - eBay username of the bidder
- Bidder rate - eBay feedback rating of the bidder
- Open bid - The opening bid set by the seller
- Price - The closing price that the item sold for (equivalent to the second highest bid + an increment)

# Data Cleaning
After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:
- Parsed email id websites from the names of the bidders
- Made columns for if they made account on different email websites or not
- Transformed usernames into the names by removing email ids
- Made column for the user's name length
- Removed the outliers 

# EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights:

![alt text](https://github.com/BhartiPandit98/Auction_Price_Prediction/blob/main/Correlation.JPG)

![alt text](https://github.com/BhartiPandit98/Auction_Price_Prediction/blob/main/Proxy_bid_distribution.JPG)

![alt text](https://github.com/BhartiPandit98/Auction_Price_Prediction/blob/main/Email_distribution.JPG)

# Model Building
First i splitted the dataset into test and train sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

I tried three different models:

- **Multiple Linear Regression** - Baseline for the model
- **Lasso Regression** - Because of the sparse data, I thought a normalized regression like lasso would be effective
- **Random Forest** - Again, with the sparsity associated with the data, I thought that this would be a good fit.

# Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets.

- **Random Forest** - MAE = 118.5
- **Lasso Regression** - MAE = 274.2
- **Multiple Linear Regression**  - MAE = 275.3


