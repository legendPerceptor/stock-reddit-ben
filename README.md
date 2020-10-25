# stock-reddit-ben
For Network course at UChicago


## Introduction

The unfettered access to Internet and social networks has offered a growing number of people opportunities to gain support from all levels of online communities when they are making significant financial decisions. However, the quality of the information available, the unpredictable fluctuations of the market, and the expertise level for both authors and readers of a specific investment advice will all make contributions to whether the “support” is positive or negative. Believing in misleading advice can cause great harm to a person’s economic and psychological conditions. 

This project is motivated by the potential value offered by a discriminator mechanism for a subset of online financial advice. In this project, we hope to investigate users who consistently post or respond to investment-related topics on Reddit, analyze the correlation between their investment advice and market plays, estimate the expertise level of those users, and perhaps give a pattern suggesting which contents are more believable for future investment decisions.

## 1. Data Collection

In this project, we have two parts of data to collect.
1. the data for stock market
2. the data for reddit users who predicted the stock

For the first part, we use the dataset provided by a [Reddit post](https://www.reddit.com/r/algotrading/comments/bfrffa/updated_the_8000_stocks_daily_historical_data/) from user **u/its_dr_yen**, on  [Kaggle](https://www.kaggle.com/qks1lver/amex-nyse-nasdaq-stock-histories). The last scrape was done on 2020.06.12, and the files' size is ~3GB. We can also collect data from Eoddata, and the price for 5 years' historical data is $12.50.

Each stock symbol has an associated *.csv* file, and the columns in *.csv* are listed below:

- **date** - year-month-day, 2020-05-27
- **volume** - int, volume of the day
- **open** - float, opening price of the day
- **close** - float, closing price of the day
- **high** - float, highest price of the day
- **low** - float, lowest price of the day
- **adjclose** - float, adjusted closing price of the day

The symbol meaning can be matched in [Eoddata](http://eoddata.com/Default.aspx). We focus on **New York Stock Exchange**.

For the second part, we took a look at **r/Stock_Picks**, because "the sub to discuss your most recent picks and predictions, share advice, and ask investing related questions!" But there are plenty of AutoModerator claiming the rules under posts, which means lot's of posts on this sub is not relevant thus not of high quality. It's possible to crawl with praw API or something, but I found a database collected by a reddit user [here]("https://www.reddit.com/r/datasets/comments/3bxlg7/i_have_every_publicly_available_reddit_comment/"). He provides more than 1TB data, but also a one-month-comment set, which is 5~6GB. I think the two datasets stated above might be enough for us.

I think we can follow two papers [Stock market analysis using social networks]("https://dl.acm.org/doi/10.1145/3167918.3167967") and [Estimating Relative User Expertise for Content Quality Prediction on Reddit]("https://dl-acm-org.proxy.uchicago.edu/doi/10.1145/3078714.3078720"). The first give an idea on how to use ML methods to handle stock data and how to analyze user comments (in their paper, they analyzed tweets, though sadly didn't provide the data). The second paper focus on reddit user expertise level analysis.

# Problems
I personally think reddit data might be very difficult to handle with automated methods. For now, we are still lacking in statistical methods to handle those data.
