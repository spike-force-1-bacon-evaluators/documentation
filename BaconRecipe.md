# EPIC: 

## As a USER I want to have a rating for the best restaurants in LONDON.


# USER STORIES:

## Create model to determine the rating (good/bad) based on a review:
* Get basic Yelp review dataset.
* Extract review/star data.
* Apply binary classification (bad: [1,3[ ; good: [3,5]).
* Clean data.
* Split data in training set and test set.
* Run algorithms and get corresponding models.
* Determine the best model using the test set.


## Extract restaurant data from review website (yelp, zomato, tripadvisor,...):
* Get review dataset (restricted to London).
* Extract relevant parameter from dataset (name/restaurant id, review, star rating, location, date, reviewer id, category, price range) rating for restaurants.
* Prune dataset (e.g. remove closed restaurants, etc.)
* Clean data.

## Extract restaurant reviews from Twitter:
* Define how to filter restaurant tweets.
* Filter tweet from the desired region (London).
* Setup twitter stream connector (Kafka).
* Get sample collection of tweets.
* Apply ML model to data sample and verify performance.

## Create weighing model (WM):
* Insert magic here.

## Apply WM to restaurants:
* Profit.
