# NFT Tweet Sentiment Analysis

Sentiment analysis of ~11,800 English tweets about NFTs, collected with the Twitter API in May 2022.
Tweets are labelled with two lexicon-based methods (TextBlob and VADER), and the VADER labels are then
used to train and compare three supervised classifiers on TF-IDF features.

## Results

Evaluated on a held-out 5% split (345 tweets, after removing neutral tweets):

| Model | Accuracy | F1 (negative) | F1 (positive) |
|---|---|---|---|
| Bernoulli Naive Bayes | 0.88 | 0.13 | 0.94 |
| **Linear SVC** | **0.93** | **0.66** | **0.96** |
| Logistic Regression | 0.91 | 0.49 | 0.95 |

The data is heavily skewed towards positive sentiment (~87% of the test set), so the negative-class F1
is the more telling number. Because the training labels come from VADER, these classifiers learn to
reproduce VADER's judgement rather than human-annotated sentiment.

## Approach

1. **Collection:** tweets matching `NFT -filter:retweets` pulled with Tweepy (the collection cell is
   kept commented out so the notebook runs on the saved data).
2. **Cleaning:** byte-string decoding, removal of mentions, URLs, emojis and punctuation with
   `tweet-preprocessor` and regex.
3. **Lexicon labelling:** polarity and subjectivity from TextBlob, compound score from VADER;
   distributions of both are compared.
4. **Supervised models:** TF-IDF (unigrams and bigrams) with Bernoulli Naive Bayes, Linear SVC and
   Logistic Regression, compared with classification reports, confusion matrices and ROC curves.

## Repository structure

```
├── nft_tweet_sentiment.ipynb   # Full pipeline: collection, cleaning, labelling, modelling
├── data/
│   ├── tweets_raw.csv          # Tweets as collected (date, text, user, location)
│   └── tweets_clean.csv        # Same tweets with headers, used by the notebook
├── requirements.txt
└── .env.example                # Template for Twitter API credentials
```

## Getting started

```bash
git clone https://github.com/houcem24/nft-tweet-sentiment-analysis.git
cd nft-tweet-sentiment-analysis
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook nft_tweet_sentiment.ipynb
```

The notebook runs end to end on the CSV files in `data/`. To collect fresh tweets, copy `.env.example`
to `.env`, add your own API credentials, load them into your environment and uncomment the collection cell.
Note that the code was written against Tweepy 3 and the v1.1 search endpoint, which X no longer offers on
the free tier.

## Context

Built in 2022 as a Big Data course project at ESPRIT (Tunisia).

## License

[MIT](LICENSE)
