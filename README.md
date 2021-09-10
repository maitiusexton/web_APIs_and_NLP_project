# Project 3: Web APIs & NLP

## Problem Statement
***Given a post from either the r/travel or r/solotravel subreddits, how well can we predict from which subreddit it came?***

### Background
One of the strongest advances in machine learning technology has been than of natural language processing (NLP). NLP converts humans language into computer-readable data that can be analyzed and fit to various statistical models. The application of this technology range from translation services (i.e. Google Translate) to artificial intelligence. For our purposes, we're going to pull a large set of posts from either subreddit using the [*PushShift API*](https://github.com/pushshift/api) and perform analysis on a selection of recent usable posts. We want to be able to use the content of the post to predict its subreddit origin.

### Data that was analyzed
[`travel_posts.csv`](./travel_posts.csv): Roughly 167,000 of the most recent posts to the r/travel subreddit. \
[`solotravel_posts.csv`](./travel_posts.csv): Roughly 267,000 of the most recent posts to the r/solotravel subreddit.

### Data Dictionary
|Feature      | Value                                                                  |
|:------------|:-----------------------------------------------------------------------|
|       title | title of the submitted reddit post                                     |
|      author | username of the post's author                                          |
| created_utc | time that the user posted this post                                    |
|  solotravel | 1 if from the r/solotravel subreddit, 0 if from the r/travel subreddit |
|   subreddit | the subreddit in which this post was posted                            |
|    selftext | the body text of the post                                              |

## Analysis, Conclusions, and Recommendations
Despite my initial ideas that certain words or phrases would be more common in either subreddit, I did not find any evidence of such. Regardless of pretty much any type of model that I did, my training and testing score sat right around 75%. Even in adjusting my grid search parameters and taking subsamples of the data, there appears to be somewhat of a cap on how good a model can be for these particular two subreddits.\
My thinking to explain this is that there is a *lot* of overlap between either subreddit. The list of top words for either were nearly identical and, for the most part, it seems that the users of these subreddits are looking for holiday advice. Whether or not they wanted to travel with others didn't seem to affect this. I did find it interesting that some very different models (for example, Multinomial Naïve Bayes and Adaboost Classifier) produced nearly the same results. I unfortunately don't have a scientifically backed explanation for why this may be, but nevertheless, we were still able to correctly predict the subreddit roughly 3 out of every 4 times. Not the greatest, but not the worst.