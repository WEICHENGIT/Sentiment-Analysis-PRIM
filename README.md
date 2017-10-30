# Sentiment Analysis

## 1 Polarity detection by using mLSTM as feature extractor

Code provided by [Learning to Generate Reviews and Discovering Sentiment](https://arxiv.org/abs/1704.01444) (Alec Radford, Rafal Jozefowicz, Ilya Sutskever).

The code supports using the language model as a feature extractor based on a well trained model. THe mLSTM model with 4,096 units is trained on the Amazon product review dataset introduced in McAuley et al. (2015) (https://arxiv.org/pdf/1609.07959.pdf). The dataset in de-duplicated form contains over 82 million product reviews from May 1996 to July 2014 amounting to over 38 billion training bytes. Training took one month across four NVIDIA Pascal GPUs, with our model processing 12,500 characters per second.

Additionally there is a [PyTorch port](https://github.com/guillitte/pytorch-sentiment-neuron) made by @guillitte which demonstrates how to train a model from scratch (not very sure what scratch means here, if it's this? https://en.wikipedia.org/wiki/Scratch_(programming_language).

### 1.1 Demo on IMDb dataset.
A demo of using the features for sentiment classification for the binary version of the Stanford Sentiment Treebank (SST, derived from the same base dataset as IMDB, containing 6920 training samples, 872 validation samples, 1821 test samples) (Socher et al., 2013) is included in `sst_binary_demo.ipynb`. Additionally this demo visualizes the distribution of the sentiment unit, which turns out to be the trXt[:, 2388], like Figure 3 in the paper.

![Sentiment Unit Visualization](/data/sst_binary_sentiment_unit_vis.png)

### 1.2 Demo on twitter dataset
Description of dataset: Collection of tweets in the year of 2016 and their trinary labels (pos, neg, neu), containing 6000 training samples, 1999 validation samples and 20632 test samples.

Due to the limit of the performance of machine and the time cost for the fitting process, I only did the 4-folder cross validation on the  training set by using logistic regression classifier. Cross validation score for trinary classification: 0.60692871  0.61292472  0.58866667  0.64686248.

After deleting all the neutral samples and doing the binary classification, cross validation socre increased to: 0.83535354  0.85858586  0.8554095   0.87449393.

Again we try to verify the so called sentiment unit still exists for this dataset. The histogram blow seems to give us a negative answer. 

![Sentiment Unit Visualization](/tweets_data/untitled1.png)

![Sentiment Unit Visualization](/tweets_data/untitled2.png)


