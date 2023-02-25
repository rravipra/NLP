# Natural Language Processing

1) Classifiers:
The Jupyter Notebook Text.classifiers.ipynb contains the code for two types of text classifiers.
- A Sentiment Lexicon Classifier.
- Logistic Regression Classifier from scratch.

2) Unigram Model:
The code to build a unigram model from scratch,

3) The Viterbi algorithm for decoding masked characters by maximizing the probability under the bi-gram model.
The code for the algorithm.

# Contents

1) Text.classifiers.ipynb - The Jupyter notebook for both the classifiers inclding training and testing the classifiers
2) Unigram.ipynb - The Jupyter notebook for the unigram model
3) Viterbi.ipynb - The Jupyter notebook for the Viterbi algorithm under the bigram model.

# Data

1) You can use your own datasets. The datasets should be text files which has already been classified as positive and negative documents which you will be using to train the logisistic regression classifier. The dataset can be the same for the lexicon based classifier but you will only be using it as a test set about 20% of the data or less than that depending on the number of files you have as your data. You should also have two files that contain a list of positive and negative sentiment words so that you can use that to test the sentiment lexicon classifier.

2) You can use your own datasets. The datasets should be text files that contains sentences of words line by line.

3) You can use your own datasets. The dataset has to be of the format where each line contains characters separated by a space and some characeters are "masked",
in the sense they are unknown and you need to predict them.
For the bi-gram data, you need to have the bi-grams and their respective pretrained probabilities in a text file line by line (Please refer to the code for further details)

# Methods used

1) Classifiers:

- Lexicon Classifier: Based on the negative and positive sentiment words you classify the document with more positive sentiment words that negative sentiment words if not classify it as negative.

- Logistic Regression Classifier: Using a matrix X which contains the vectors of the count of all the words in the vocabulary (remove stop words if you have to) and y being the true labels {0,1} I train my Logistic regression model from scratch.

# Feature selection for logistic regression.

The logistic regression classifier in my case uses a similar model as the bag of words to pick the
features. In my case first I have a set of stop words that I can use to remove it from my vocabulary so
that the number of features can be decreased and further so that since the stop words occur more
frequently this might affect how the weights give priorities to the features. 

I want my weights to prioritize to classify as a positive or a negative document.
I have coded a function that given a list of documents converts it to a matrix where each row
contains the vector of values of each document in order which is going to be our X.

The way that I have picked my features is as I mentioned similar to the bag of words model
where I take into account the whole set of vocabulary contained in all the documents. The
size of my vocabulary is the number of features that I have used. In my case I ran my model by
removing some of the features such as stop words using my stop words list since it is always better
to have a lesser number of "more relevant" features but as I noticed in my model removing the stop
words did not change my accuracy by a lot. Removing the stop words did not make too much of a
difference other than the fact that the loss dropped slower in the first few epochs compared to the
model with the stop words and it also started with a lower loss. So, my features are the number
of words in our vocabulary and the values of each row would be the counts of that word in that
particular document if it exists in the document that we are looking at, if not set to 0.
Another point that I wanted to add was that I have not Normalized the matrix since we would
not really need that in my case so there is no need to handle the fact that the matrix is sparse.

I have picked my features in this manner since this method of feature selection for text classification worked well in a manner that since it offers a lot of flexibility for customization on my data. Since it also takes into account each of the words or the words excluding stop words as such
it assigns weights based on how relevant the feature is based on our model.It is also simple to understand and to implement, this method is scalable and can handle large amounts of data but sometimes is it better to have lesser features than too many features.

# Training parameters for logistic regression.

I have trained my model with a learning rate of 0.01, a batch size of 100 and 1500 epochs.

# Results

1) Sentiment Lexicon Classifier:

Accuracy: 0.695 //
Precision: 0.732 //
Recall: 0.640 //
F1 Score: 0.682 //

2) Logistic Regression Classifier:

Accuracy: 0.860 //
Precision: 0.857 //
Recall: 0.849 //
F1 Score: 0.850 //

(Note: I will add further details for the method used for each of the files if needed, but the code and the comments in the code should be very helpful and straight forward in understanding further)
