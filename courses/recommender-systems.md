# 01
  - Information Retrieval (IR) vs Information Filtering (IF)
  - TFIDF (term frequency inverse document frequency)
  - Nearest-Neighbour approach

  - Personalization level:

    - Everyone received same recommendations
    - Matched to a target group
    - Matched to current activity
    - Matched to long-term interests

  - Types:

    - Non-personalized summary stats (just average the ratings)
    - Content-based filtering:
      - create a model out of user ratings and item attributes
      - apply model to new items via attributes
    - Personalized collaborative filtering
      - create a user model (set of ratings) and a item model (set of ratings)
      - this creates a sparse matrix of ratings
      - prediction is filling in the missing values
      - recomendation is selecting the most promissing cells

# 02

People who X also Y...

  - user profiles: people who ever bought one and the other:
    - bad example:
      The most popular sause bought by people who like icecream is ketchup, when
      in fact we should be selling them caramel sauce.
  - transaction date: people who bought items at the same time
    - bad example:
      Not good for follow-up sales.
  - time-constrained user profiles

Ranking:
  - percentage of X-buyers who also bought Y
    - Banana problem:
      - Almost everyone buys bananas from supermarkets.
      - 99% of people who buy achovy paste also bought bananas, but that doesn't
        mean we should be recomending bananas if you buy anchovy paste since you
        were going to do that anyway.
  - does X make Y more likely?

Prediction:
  Estimates how much you'll like an item.

Recommendation:
  Suggestions for items you might like.

# 03

Representing an item through a keyword vector:

  - simple 0/1 (exists or not)
  - simple occurrence count
  - TFIDF:
    - # occurrences in doc * log (# docs / #docs with term)

How to accumulate profiles?
  - add together item vectors?
    - normalization?
    - weigh the vectors?
      - give more importance to more recent item vectors?

  - how to factor in ratings?
    - aggregate profiles of items we rated without weights
    - only put items above a certain rating into the profile
    - weight
      - heigher weight for things with high scores
      - heigher/lower weight for things with high/low scores

How to compute predictions?
  - prediction is the cosine of the angle between the two vectors (profile and
    item) (so the result is between -1 and 1)

Use MoreLikeThis from Lucene for content based recommendations.

# 04

Assumptions/Limitations:

  - our past agreement predicts our future agreement.

# 05

Simple accuracy measurements:
  - RMSE (is probably the best)

Decision support measurements:
  - precision: percentage of relevant items from my selected items
  - recall: percentage of relevant items that are selected

The best way to measure is to release to live, with an actual userbase, not by
using dead data.

One of the best ways of evaluating:

  - Split into 5 chunks. For every chunk, use the rest as the training data and
    test on that chunk.
  - It's best to split by users, because you're trying to optimize for user
    experience.
  - Since you need to know something about every user you're testing, you also
    need to move a large part of a test user's data into the training data.
    Tipically, you segment a user's ratings by time (i.e. move 80% of the user's
    oldest ratings into the training data).
  - Measurement: compute RMSE for every user in the chunk and average that. Then
    average all the RMSE's for the chunks.

# 06

User-user CF doesn't work so well with very sparse ratings.

Works better when there are much more users than items.

Structure of Item-item CF:
  - pre-compute item similarities over all pairs of items
  - look for items similar to those the user likes, or has purchases, or has in
    their basket, &c.

Picking item neighbours:
  - the k most similar items that the user has rated (usually k = 20)

Precompute the similarities for all pairs of items.

For binary data (bought/not bought), you can user conditional probability to
estimate the similarity of items.

# 07

Singular Value Decomposition
  - reduces space to a smaller taste space that is compact and robust.
  - reduces overfitting

# 08

Multi-Criteria Recommenders
  - This works better with implicit data.
