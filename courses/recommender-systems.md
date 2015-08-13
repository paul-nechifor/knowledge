# 01
  - Information Retrieval (IR) vs Information Filtering (IF)
  - TFIDF (term frequency inverse document frequency)
  - Nearest-Neighbor aproach

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
  - percentaga of X-buyers who also bought Y
    - Banana problem:
      - Almost everyone buys bananas from supermarkets.
      - 99% of people who buy achovy paste also bought bananas, but that doesn't
        mean we should be recomending bananas if you buy anchovy paste since you
        were going to do that anyway.
  - does X make Y more likely?

Prediction:
  Estimates how much you'll like an item.

Recomendation:
  Suggestions for items you might like.

# 03

Assumptions/Limitations:

  - our past agreement predicts our future agreement.
