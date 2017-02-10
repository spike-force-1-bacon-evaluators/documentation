# Documentation

## [Ways of Working](docs/ways-of-working.md)

* [Definition of Done](docs/ways-of-working.md#markdown-header-definition-of-done)
* [Issue tracking](docs/ways-of-working.md#markdown-header-issue-tracking)
* [Topic branches](docs/ways-of-working.md#markdown-header-topic-branches)
* [Commit messages](docs/ways-of-working.md#markdown-header-commit-messages)
* [Code review](docs/ways-of-working.md#markdown-header-code-review)
* [Changelog](docs/ways-of-working.md#markdown-header-commit-changelog)
* [Gitflow](docs/ways-of-working.md#markdown-header-gitflow)
* [Release](docs/ways-of-working.md#markdown-header-release)
* [Principles for Evaluating Pull Requests](docs/pull-request-evaluation.md)
* [Project members](docs/project-members.md)
* [Project Description](#markdown-header-project-description)
* [3rd Party Libraries](docs/3rd-party-libs.md)

## Project Description
The Bodacious Advisor for Cuisine Over N-joyment ranks the restaurants within London based on Twitter reviews.

## The Bacon Approach
Our first step is to use a dataset provided by Yelp to get reviews and their associated Star Evaluation with a parser to get this key-value pair. This new dataset is used to train algorithms that are used for sentiment analysis so that we can read tweets for restaurants and predict its Star Evaluation (*-tweet). Reviews from Yelp will only be used for training the Ranking Algorithm. 

Using a list with 2380 restaurants based in London with Tweeter account, we use Twitter-API to get tweets that mention those accounts so that we can apply our sentiment analysis algorithm on them, discovering their *-tweet. Our time window is three months from now, so we will not consider old tweets.

//toDo Machine Learning (Sara)

//toDo ranking algorithm (Sara)

//toDo weight model (Sara)

## Architecture Overview
The B.A.C.O.N pipeline for ranking restaurants is built on top of 6 components: 

1. A client interface to access the ranked data;
2. An API to enables the access to data inside the storage;
3. A Data Translation Layer for cleaning and normalising data from Yelp Dataset and Twitter List Members;
4. A Data Process Layer, responsible for getting tweets about restaurants and formatting the data into our standard before store it;
5. The Data Analytics Layer stands on top of DataIku, where our team of Data Scientists perform sentiment analysis/ranking algorithms and weight models to get the Restaurant Rank;
6. We also have a Storage system to keep our precious data protected.

![architecture](images/arch.JPG)

The communication path through our components can be seen in the following image. 

![communication](images/communication.png)

Below we demonstrate the B.A.C.O.N. activity flow.
 
![activity](images/activity.png)

Starting with the Yelp Reviews Extractor, we get the **Stars** and the **Free Text Review**, this data is cleaned and loaded into DataIku where it will be used to train our sentiment analysis algorithm. At the same time, the Twitter List Members Extractor uses the Twitter API to get the list of restaurants based in London which have a Twitter Account. With this list, we can use the Twitter API to read the tweets within the last three months that mention those restaurants. This Tweets data is stored, and inside DataIku, the data scientists load this dataset. If we don't have any trained algorithm, now it is time to have it, another way, we will use our previously trained sentiment analysis algorithm to classify each tweet in **good** or **bad**. With the **good/bad** classification performed, now it is time to apply the weight model so we can produce our Ranking and store it.

Also, bellow we show the use cases in B.A.C.O.N.
![uc](images/use_cases.png)
