# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 5: Sentiment Analysis of COVID-19 Tweets 
#### Eu Jin Lee: [GitHub](https://github.com/missingNA) 
#### Gwen Rathgeber: [GitHub](https://git.generalassemb.ly/gwenrathgeber)

## Problem Statement

With the recent series of unfortunate events that has happened, the COVID-19 pandemic being a major one; social media has been a constant stream of valuable information that could shed light on the state of the country. Twitter is a great text based social medium in which Natural Language Processing (NLP) techniques can be implemented on. Hence in this project, the goal is to conduct a sentiment analysis to determine the polarity of tweets related to COVID-19 and mapped them geographically across the United States.
The nation's response to the pandemic has been largely regional and state-based in nature. Some states have enacted strictly enforced stay-at-home policies, while others have provided less stringent guidelines paired with instructions on a federal level. From this analysis, we would be able to observe the response of the nation according to respective state and federal guidelines. Comparing the sentiment analysis of tweets across the United States with respect to both the local policies on social distancing and the occurrences of the pandemic in those areas.

In this project, we make initial steps toward designing and implementing a web-tool or an app for tracking and monitoring geo-tagged tweets during the pandemic, in close to real time.

While traditional methods for alerting on such events rely on official information derived from official sources (e.g. CDC), our focus is attempting to utilize social media activity to identify these events and alert when an event first occurs. The question we look at primarily here is, given a sea of text content from social media platforms, how is the general public's response to pandemic guidelines and policies and how quickly does the public respond from the time a policy has been implemented? And what sort of implementation would be valuable?

## Executive Summary
The workflow of the projects is as follows:

- Importing packages, obtaining COVID-19 geo-tagged tweet ids 
- Hydrating tweets 
- Exploratory data analysis of tweets collected 
- Sentiment analysis of tweets
- Evaluation
- Visualizations 
- Conclusions and Recommendations

For the purposes of this project, we pulled tweet ids from the Institute of Electrical and Electronics Engineers' (IEEE) Data Repository. The data mining process was an interesting but long process. First, obtaining a dataset of COVID-19 related tweet ids totalling to ~168,493 (at the time). Next, hydrating those tweet ids using the TWARC API to obtain the Twitter information of those tweets. The tweets were then filtered for only those from the United States (primary focus) with state information. Our final tweets count was ~65,000. 

A sentiment analysis was then conducted using TextBlob, determining the polarity of the tweets ranging from overwhelming positive on one end to overwhelming negative on the other. TextBlob is a popular Python library for processing textual data. It provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation etc. 

The sentiment analysis data is then mapped using the geo-tagged information from these tweets to build a visual timeline of the country's overall sentiment on COVID-19. This opens up the ability for us to view the public's response on the events that unfold throughout the current pandemic. It also allows us to dive into deeper issues regarding response times and help us make better decisions in health policymaking especially in the event of the pandemic. 

### Table of Contents 

- [Data Dictionary](#Data-Dictionary)
- [Package Import](#Package-Import)
- [Scraping COVID-19 Geo Tagged Tweet URLs](#Scraping-COVID-19-Geo-Tagged-Tweet-URLs)
- [Hydrating Tweets using TWARC API](#Hydrating-Tweets-using-TWARC-API)
- [Unsupervised Sentiment Analysis](#Unsupervised-Sentiment-Analysis)
    - [Analyzing Twitter Data](#Analyzing-Twitter-Data) 
    - [Visualizing Twitter Data](#Visualizing-Twitter-Data)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [References](#References)

### Software Requirements 
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) (Twitter Scraping)
- [TextBlob](https://textblob.readthedocs.io/en/dev/) (Twitter Sentiment Analysis Model)
- [TWARC API](https://textblob.readthedocs.io/en/dev/) (Tweet Hydration)

### Datasets
Dataset used for the project can be found:
[here](https://ieee-dataport.org/open-access/coronavirus-covid-19-geo-tagged-tweets-dataset)

- The dataset above contains global geo-tagged COVID-19 tweets totalling to approximately 168,493 at the time of extraction. 
- The tweets were then hydrated to obtain the tweets on its respective information using TWARC API
- Filtered for US based tweets bringing the final count to 64,595 tweets.

#### Data Dictionary 

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
| p_pos          | float64 | proportion of positive sentiment                   |
| p_neg          | float64 | proportion of negative sentiment                   |

---

## Visualization

![Tweet Sentiment Timelapse](https://git.generalassemb.ly/gwenrathgeber/project_5/blob/master/assets/coronavirus_sentiment_timelapse_w_legend.gif)

## Conclusion and Recommendations 
In this project, we analyzed the sentiments of COVID-19-related tweets in several ways. The overall trend shows that the public has been more optimistic over time. Digging into the dual-dimensional sentiment analysis we conducted, we found that the sentiment “Positive” went down initially and towards the end, and “Negative” went up through the height of the pandemic. We were also able to see the respective sentiment consensus by state. Our results reflect the general reaction of the 'first wave' of the pandemic and the political climate during this time. 

The fight against COVID-19 not only needs the guidance from the government but also a positive attitude from the public. Our analysis provides a potential approach to reveal the public’s sentiment status and help institutions respond timely to it.

Our analysis has shown some relationships between geographic data 
and the general sentiments of the state during the pandemic. Moving forward, introducing more granular data such confirmed cases' growth and adding additional dimensionality to our sentiment analysis would help provide a more comprehensive picture. Allowing us to generate more insights into hardest-hit areas, demographic of those affected; enabling institutions and government to take affirmative action based on this valuable information. 

## References

- COVID-19 Geo Tagged Tweets Dataset:
https://ieee-dataport.org/open-access/coronavirus-covid-19-geo-tagged-tweets-dataset
- Package for Hydrating Tweets:
https://github.com/DocNow/twarc
- Unsupervised Sentiment Analysis (K Means Clustering): https://towardsdatascience.com/unsupervised-sentiment-analysis-a38bf1906483
- Recommended Python libraries for Sentiment Analysis: https://www.iflexion.com/blog/sentiment-analysis-python
- Everything You Need to Know About Sentiment Analysis: https://monkeylearn.com/sentiment-analysis/
- Twitter Sentiment Analysis with Python and NLTK: http://www.laurentluce.com/posts/twitter-sentiment-analysis-using-python-and-nltk/
- Is it possible to do sentiment analysis of unlabelled text using word2vec model?: https://stackoverflow.com/questions/61185290/is-it-possible-to-do-sentiment-analysis-of-unlabelled-text-using-word2vec-model
- Making a request to download csv: https://stackoverflow.com/questions/35371043/use-python-requests-to-download-csv