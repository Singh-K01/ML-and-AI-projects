# Project Description
Perform sentiment analysis of a labelled set of IMDB movie reviews by using both the Lexicon approach and the Machine Learning approach and compare the two.

## Dataset
The Dataset has user reviews from IMDB users about movies. It primarily has the below 4 columns:
Structure:
UID	SCORE	SENTIMENT	REVIEW
(101)	(1-4 and 7-8) (Positive or Negative)	(“This film simply has no redeeming features. The story is incomprehensible and the script is gross sadistic and stupid…”)

### Length of Reviews: 
The Average Length of Reviews is: ~250 words
The Median Length of Reviews is: ~180 words
### About the Reviews: 
The reviews are unstructured text data or sentences that users used while expressing their views about the movies on IMDB. The views are either Positive or Negative. No reviews are Neutral.
### Number of Reviews:
There are approx. 49,000 reviews in the dataset. Approx. 24,000 Positive;  approx. 24,000 Negative, so it is a balanced dataset.

### Note about the labelling
Since the users DO NOT explicitly express the sentiment in their reviews on IMDB, the dataset was either labelled by a human subjectively or was labelled based on User Ratings. In the Human approach, the subjectivity can introduce bias and every individual would label a dataset differently based on their knowledge, which means there is no standardization, and hence the labels cannot be 100% trusted!

## Lexicon Approach
Lexicon used: VADER Lexicon
Python package used: vaderSentiment
“VADER (Valence Aware Dictionary and sEntiment Reasoner) is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media”
Ref.: https://github.com/cjhutto/vaderSentiment

### How does VADER work under the hood?
Looking at the original GitHub source (https://github.com/cjhutto/vaderSentiment) of this package, it has the below primary resources (in my opinion) to make VADER predict the sentiment:
#### 1.	The original paper for the social media dataset that Vader was tried on
Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.

#### 2.	vader_lexicon.txt
This is the lexicon text file, tab delimited, with the below columns for each token:
Token_name; Mean_Sentiment_Rating; Standard_Deviation; Raw_human_sentiment_ratings

Algorithm workings: 
“The VADER sentiment lexicon is sensitive both the polarity and the intensity of sentiments expressed in social media contexts, and is also generally applicable to sentiment analysis in other domains.” As mentioned at https://github.com/cjhutto/vaderSentiment 
The current version of the algorithm that VADER uses, utilizes only the Token name and Mean Valence. The other two columns have more advanced uses as per the author. "Sentiment ratings from 10 independent human raters (all pre-screened, trained, and quality checked for optimal inter-rater reliability). Over 9,000 token features were rated on a scale from "[–4] Extremely Negative" to "[4] Extremely Positive", with allowance for "[0] Neutral (or Neither, N/A)". We kept every lexical feature that had a non-zero mean rating, and whose standard deviation was less than 2.5 as determined by the aggregate of those ten independent raters. This left us with just over 7,500 lexical features with validated valence scores that indicated both the sentiment polarity (positive/negative), and the sentiment intensity on a scale from –4 to +4. For example, the word "okay" has a positive valence of 0.9, "good" is 1.9, and "great" is 3.1, whereas "horrible" is –2.5, the frowning emoticon :( is –2.2, and "sucks" and it's slang derivative "sux" are both –1.5."

#### 3.	vaderSentiment.py
This is the python script that helped us derive sentiment for our texts. Per the source https://github.com/cjhutto/vaderSentiment:
“They incorporate word-order sensitive relationships between terms. For example, degree modifiers (also called intensifiers, booster words, or degree adverbs) impact sentiment intensity by either increasing or decreasing the intensity. Consider these examples:
i "The service here is extremely good"
ii "The service here is good"
iii "The service here is marginally good"
From Table 3 in the paper, we see that for 95% of the data, using a degree modifier increases the positive sentiment intensity of example (a) by 0.227 to 0.36, with a mean difference of 0.293 on a rating scale from 1 to 4. Likewise, example (c) reduces the perceived sentiment intensity by 0.293, on average.”

#### Scoring of the algorithm:
Sourcing from https://github.com/cjhutto/vaderSentiment: “The compound score is computed by summing the valence scores of each word in the lexicon, adjusted according to the rules, and then normalized to be between -1 (most extreme negative) and +1 (most extreme positive). This is the most useful metric if you want a single unidimensional measure of sentiment for a given sentence.”


## Machine Learning approach - Building various Text Classifiers
The idea was to build the best Text classifier possible, and the iterations involved trying out various algorithms, hyperparameters, and text pre-processing techniques to get the best Accuracy, Specificity and Sensitivity.

### Text Pre-processing Techniques used
Tokenization, Stop words removal, Stemming, Bi-grams, Tri-grams, CountVectorize, TF-IDF

### ML classifier algorithms tried
LogisticRegression, Random Forest, Decision Trees
GridSearchCV Hyperparameter tuning:
For LogisticRegression: [{'C': [0.01, 0.1, 0.5, 1.0, 10, 100], 'class_weight': ['balanced']}]
For RandomForestClassifier: [{'n_estimators':[5,10],'criterion':['entropy',’gini’]}]
For DecisionTreeClassifier: [{'criterion':['entropy','gini'], 'max_features':['auto','sqrt','log2']}]
Measure of fit for GridSearchCV was chosen to be Accuracy.

### Vectorization Techniques used
CountVectorizer: min_df = 15, max_df = 0.3
TFIDF Vectorizer: min_df = 15, max_df = 0.3

### Performance measures for Classifiers
Accuracy, Sensitivity, Specificity
Since I have ZERO faith in the under-the-hood calculations of the sklearn.metrics performance measures, I went ahead and wrote my own custom functions for calculating measures.

## Things I could have tried
•	Try to topic model the dataset, and add Topics as features for sentiment prediction
•	Doc2Vec as features

## Results
LogisticRegression with hyperparameters: {'C': 0.1, 'class_weight': 'balanced'} and Vectorization = Count-Vectorizer gave the best performance. (Logistic Regression with TF-IDF gave slightly better accuracy but other metrics were low)

## Comparing the two approaches
1. Lexicon (VADER) was not that impressive, with lower scores on each of the metrics Accuracy, Sensitivity and Specificity compared to the ML model. ML performed better.
2. Out of 100% total reviews, 50% were Negative and 50% were Positive, however this is how the different approaches performed:
o	Lexicon: Was only able to correctly predict 54% of the total Negative Reviews but was able to predict 85% of the total Positive Reviews
o	Machine Learning Classifier: Was able to predict 86% of the total Negative Reviews and 87% of the Positive Reviews which is great.
o	Therefore, performance at predicting positive reviews was nearly equal for both Lexicon and ML approach for this dataset.
3. Another observation was that Lexicon approach was fast in training, but ML took some more time to train, comparatively.




