# ![ga_logo](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)Project 5: Sentiment Analysis of COVID-19-related Tweets

#### Eu Jin Lee [GitHub](https://github.com/missingNA) [LinkedIn](https://www.linkedin.com/in/eeujinlee/)  

#### Gwen Rathgeber [GitHub](https://git.generalassemb.ly/gwenrathgeber) [LinkedIn](https://www.linkedin.com/in/gwenrathgeber/)

## Problem Statement

Throughout the course of the COVID-19 pandemic, social media has been filled with a constant stream of valuable information that could shed light on the state of the world. Twitter is a great text-based social medium for applications of Natural Language Processing (NLP) techniques. In this project, our goal is to visually represent the mood of the United States over the course of the COVID-19 pandemic. 

The nation's response to the pandemic has been highly regional in nature. Some states had larger earlier or delayed spikes in case rates, for example. States varied on their timeline of enacting and enforcing stay-at-home policies. We hope to visualize the response of the nation along those significant state boundaries. 
 
We also make initial steps toward creating a web-based tool or app for tracking and monitoring the mood of the country in real time.

## Executive Summary
The workflow of the projects is as follows:

- Importing packages, obtaining COVID-19 geo-tagged tweet ids 
- Hydrating tweets 
- Sentiment analysis of tweets
- Evaluation
- Visualization Deliverable
- Conclusions and Recommendations

For the purposes of this project, we pulled tweet ids from the Institute of Electrical and Electronics Engineers' (IEEE) Data Repository. The data mining process was an interesting but long process. First, obtaining a dataset of COVID-19 related tweet ids totalling to ~168,493 (at the time). Next, we hydrated those tweet ids using the `twarc` Twitter API wrapper to obtain the full `.json` data of those tweets. The tweets were then filtered for only those from the United States (primary focus) with state information. Our final tweets count was ~65,000. 

A sentiment analysis was then conducted using TextBlob, determining the polarity of the tweetson a positive-to-negative spectrum. TextBlob is a popular Python library for processing textual data. It provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation etc. 

The sentiment analysis data is then mapped in Tableau using the geo-tagged information from these tweets to build a visual timeline of the country's overall sentiment on COVID-19. This opens up the ability for us to view the public's response to events over the course of the pandemic. 

### Table of Contents 

- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Software Requirements](#Software-Requirements)
- [Dataset](#Dataset)
- [Data Dictionary](#Data-Dictionary)
- [Project Notebook](https://git.generalassemb.ly/gwenrathgeber/project_5/blob/master/code/project_5.ipynb)
- [Visualization](#Visualization)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [References](#References)

### Software Requirements 
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) (Twitter Scraping)
- [TextBlob](https://textblob.readthedocs.io/en/dev/) (Twitter Sentiment Analysis Model)
- [twarc Twitter API wrapper](https://textblob.readthedocs.io/en/dev/) (Tweet Hydration)

## Dataset
The datataset used for the project can be found [here.](https://ieee-dataport.org/open-access/coronavirus-covid-19-geo-tagged-tweets-dataset)

- This dataset contains global geo-tagged COVID-19 tweets ids which numbered approximately 170,000 when accessed. 
- The tweet ids were hydrated using the `twarc` wrapper for the Twitter API to obtain the full tweet data.
- After filtering for useable geo-location data and limiting the dataset to the United States, our final count was 64,595 tweets.

### Data Dictionary 

| Features       | Type    | Description                                        |
|----------------|---------|----------------------------------------------------|
| full_text      | object  | full text of the tweet                             |
| id             | float64 | tweet id                                           |
| date           | object  | date tweet was posted                              |
| city           | object  | city from which tweet was posted                   |
| country_code   | object  | country code from which related tweet was posted   |
| country        | object  | country corresponding to country code              |
| coordinates    | object  | latitude and longitudinal values of tweet location |
| state          | object  | state from which tweet was posted                  |
| classification | object  | overall tweet sentiment (positive or negative)     |
| p_pos          | float64 | percent chance of positive sentiment               |
| p_neg          | float64 | percent chance of negative sentiment               |

---

## Visualization

We used Tableau to create the visualization, a timelapse of the four previous days rolling average sentiment by state. [You can view or download it yourself on Tableau Public.](https://public.tableau.com/views/COVIDTwitterSentimentVisualization/Sheet1?:language=en&:display_count=y&publish=yes&:origin=viz_share_link)

![Tweet Sentiment Timelapse](https://git.generalassemb.ly/gwenrathgeber/project_5/blob/master/assets/coronavirus_sentiment_timelapse_w_legend.gif)

## Conclusion and Recommendations 
In this project, we analyzed the sentiments of COVID-19-related tweets in several ways. The overall trend shows that the public was initially optimistic, got much less cheerful in mid-April, then trended somewhat more positive throughout future months. We were also able to see the overall sentiment by state. You can especially track the major decrease in positive sentiment in NY and surrounding states after the pandemic reached its peak case load. Interestingly, there is not much of a visible decrease in sentiment over the course of the larger and more wide-spread second wave in our data.

The fight against COVID-19 not only needs the guidance from the government but also a positive attitude from the public. Our analysis provides a potential approach to examine the public’s mood and allow institutions to respond to it in a timely manner.

Our analysis has shown some relationships between geographic data and the general sentiments of the state during the pandemic. Moving forward, introducing more granular data such as the growth of confirmed cases or adding additional dimensionality to our sentiment analysis would help provide a more comprehensive picture. 

Our workflow was limited by the level of API access key granted by Twitter, preventing us from gathering much historical data on our own. We needed to find a pre-existing dataset, and would be well-served in the future to integrate additional COVID-related tweet datasets with what we were able to obtain.

In addition, time constraints prevented us from testing a variety of pre-trained sentiment analysis models. The TextBlob Naive Bayes model was trained on IMDB movie review, making it somewhat less than ideal for our data, but most other well-known pre-trained models have a similar issue. Future work could use a more advanced sentiment analysis model, either by accessing a paid API or by hand-labeling tweets to create a custom-fitted model for this application.

Finally, we would have liked to include a wider variety of visualizations of this data, included but not limited to annotations of major events, time series, and visualizations of more features such as retweets and likes.

## References

- COVID-19 Geo Tagged Tweets Dataset: https://ieee-dataport.org/open-access/coronavirus-covid-19-geo-tagged-tweets-dataset
- Package for Hydrating Tweets: https://github.com/DocNow/twarc
- TweetAnalyzer class adapted from: https://medium.com/shiyan-boxer/2020-us-presidential-election-twitter-sentiment-analysis-and-visualization-89e58a652af5
- Everything You Need to Know About Sentiment Analysis: https://monkeylearn.com/sentiment-analysis/
- Making a request to download csv: https://stackoverflow.com/questions/35371043/use-python-requests-to-download-csv