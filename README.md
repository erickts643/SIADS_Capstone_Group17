# Combining Market Data and Reddit Sentiment for Equity Event Prediction 
MADS Capstone - Team Safari
- Last Update: December 2023

# Introduction
Our project examines the phenomenon of short squeezes in the stock market.  The main datasets of archived stock options chain data and Reddit WallStreetBets forum text were supplemented by public APIs Yahoo Finance, scraped data from Zacks.com, and imported data from Nasdaq. 

# Running the Code

## Requirements
Requirements.txt file includes all the libaries required to run our code.

## Jupyter Notebooks
Our code is stored in Jupyter notebooks that can be all be run independently.  They can be found in the Jupyter_Notebooks folder of this repository.  As long as you have the required libraries listed in the Requirements.txt file, you should be able to run the notebooks freely.

Note: Some of our notebooks connect with our database hosted on the AWS environment.  As per the given specifications for this Repo, we have removed the user login credentials to the AWS environment.  Please reach out to us if necessary. 

# Data access
Provenance of the two main datasets:
1. Historical archive of daily options data: Archived by one of our team members over a number of years. The data was available through a paid subscription to the Chicago Mercantile Exchange (CME).  For our purposes, the data was stored in an AWS S3 bucket, databased, and accessed via our Jupyter Notebooks. 
2. Reddit Text Data: Downloaded archive from the-eye.eu in Z standard compression format, extracted posts and comments in JSON. Then uploaded the extracted text (5.6 GB) into an AWS database.

Additional Data sourced via API calls that do not require special credentials or subscriptions.

# Data Flow
![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/c66b33f2-4f0c-4fe5-a181-82a69d7389c1)


# Reddit Sentiment
Sentiment analysis on r/WallStreetBets, as performed using the Reddit API via PRAW, provided valuable insights for trading ideas by gauging the collective sentiment of the community towards specific stocks. This analysis helped identify potentially popular or volatile assets by uncovering trending stock discussions, enabling traders to make informed decisions based on the sentiment dynamics within the subreddit.

A unique aspect of this analysis was the differentiation between positive and negative lexicon specific to r/WallStreetBets. The subreddit's language includes terms like "YOLO" (You Only Live Once) and "diamond hands" (holding onto a stock regardless of its performance), which are critical to accurately gauge sentiment within the community. Assigning different weights to sentiment scores based on the significance of certain terms within the community was vital. For instance, giving higher weight to terms that are particularly relevant or impactful in r/WallStreetBets discussions better reflected the community's sentiment trends.

![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/467b9900-4e03-4b88-8ebb-468a7e1a409f)


![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/c15543c1-1318-4323-969e-62a5dd36bc73)


# Short Sale Volume
We additionally integrated FINRA short sale volume data from market makers, focusing on its influence on stock prices and market dynamics. This data helped in understanding market behaviors, particularly in volatile conditions and "meme stocks" like GameStop (GME). The accompanying chart offers a comparative analysis of GME and the S&P 500 (SPY), centered on rolling short ratio volume. It features 1.5 and 2 standard deviation bands for SPY's short ratio volume, serving as benchmarks for typical market behavior. Notably, the chart, with areas shaded in green, highlights instances where GME's short ratio volume surpassed these thresholds. These peaks align with the meme stock phenomenon of 2020 and 2021, illustrating periods of unusually intense shorting activity in GME, far exceeding the market's standard range and underlining its pivotal role in the extraordinary market events of that period.

![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/64fb2177-e411-442a-97ed-9913a2612579)



# Model Performance and Results
Our logistic regression model demonstrated a notable ability to identify stock market events like short squeezes, achieving 71% accuracy in TimeSeriesSplit tests, signifying notable prediction capability. The model's precision, measuring the accuracy of positive predictions, is .77. Its recall rate, which shows how well the model identifies all relevant cases, stands at 0.70. The F1 score, a balance between precision and recall, is 0.73 for positive events and 0.69 for negative ones, indicating a solid performance in this specific context.

![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/e6f5f35d-b2db-422c-85ca-5dfdea500f10)

![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/bb853e60-aabd-49cd-8a8a-955a68b7aa2c)


# Discussion: Reddit Causality and Market Movements
We explored the causative impact of Reddit discourse on stock prices, examining if Reddit sentiments could precede and possibly trigger significant market movements. Notably, our analysis found that for specific "meme" stocks like BB and GME, Reddit discussions had a notable delayed causative effect on stock movements, highlighting a complex interplay between social media sentiment and market dynamics. Our findings also led us to delve into regulatory frameworks like REG-SHO, which governs short selling and provides exceptions for market makers. These participants, crucial for maintaining market liquidity, are permitted to short sell without restrictions under certain conditions. This regulatory backdrop potentially explains the observed volatility in trading events and notably influences our model's predictions, underscoring the complex dynamics of market behavior and regulatory influences in equity event prediction.

![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/b9e24acd-4333-49e1-a71c-eb23e990502f)
