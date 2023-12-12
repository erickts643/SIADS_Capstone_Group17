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

Additional Data sourced via API as depicted in our Data Flow diagram below.

# Data Flow
![image](https://github.com/erickts643/SIADS_Capstone_Group17/assets/127133109/c66b33f2-4f0c-4fe5-a181-82a69d7389c1)
