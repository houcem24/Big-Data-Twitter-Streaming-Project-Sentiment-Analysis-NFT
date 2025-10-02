Twitter Sentiment Analysis
📌 Project Overview

This project performs sentiment analysis on Twitter data. Tweets are collected using the Twitter API, cleaned and preprocessed, and then analyzed using both lexicon-based methods (TextBlob, VADER) and machine learning models (Logistic Regression, Naive Bayes, Linear SVC).

The workflow includes:

Collecting tweets via Tweepy.

Cleaning and preprocessing text data.

Performing sentiment classification.

Training and evaluating ML models with TF-IDF features.

Visualizing model performance (confusion matrix, ROC/AUC).

⚙️ Installation

Clone this repository and install dependencies:

git clone https://github.com/yourusername/twitter-sentiment-analysis.git
cd twitter-sentiment-analysis
pip install -r requirements.txt

Main Dependencies

Python 3.x

Tweepy

Pandas, NumPy

TextBlob, VADER Sentiment

scikit-learn

(see requirements.txt for the full list).

🚀 Usage

Get your Twitter API keys from Twitter Developer Portal
.

Add your credentials in the notebook under:

consumer_key = "YOUR_KEY"
consumer_secret = "YOUR_SECRET"
access_key = "YOUR_ACCESS_KEY"
access_secret = "YOUR_ACCESS_SECRET"


Run the notebook step by step to:

Collect tweets.

Clean text.

Perform sentiment analysis.

Train and evaluate ML models.

📊 Results

Lexicon-based methods (TextBlob, VADER) provide quick insights.

ML models (Logistic Regression, Naive Bayes, Linear SVC) achieve higher accuracy on labeled data.

Confusion matrix and ROC/AUC metrics are used for evaluation.

📂 Project Structure
.
├── Projet.ipynb         # Main Jupyter Notebook
├── requirements.txt     # Python dependencies
├── README.md            # Project documentation

✨ Future Improvements

Expand dataset size for better model generalization.

Integrate deep learning approaches (LSTM, BERT).

Deploy as a web app/dashboard for real-time sentiment tracking.
