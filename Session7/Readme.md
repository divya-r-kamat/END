Stanford Sentiment Treebank V1.0

# Goal
The goal is to build a sentiment analysis model using  StanfordSentimentAnalysis Dataset.
- Use "Back Translate", "random_swap" and "random_delete" to augment the data you are training on
- Download the StanfordSentimentAnalysis Dataset from this link  (http://nlp.stanford.edu/~socherr/stanfordSentimentTreebank.zip) 
  Use "datasetSentences.txt" and "sentiment_labels.txt" files from the zip you just downloaded as your dataset. This dataset contains just over 10,000 pieces of Stanford data from HTML files of Rotten Tomatoes. The sentiments are rated between 1 and 25, where one is the most negative and 25 is the most positive.
- Train your model and try and achieve 60%+ accuracy. Upload your colab file on git with the the training logs

# Dataset 

This is the dataset of the paper:

Recursive Deep Models for Semantic Compositionality Over a Sentiment Treebank
Richard Socher, Alex Perelygin, Jean Wu, Jason Chuang, Christopher Manning, Andrew Ng and Christopher Potts
Conference on Empirical Methods in Natural Language Processing (EMNLP 2013)

This file includes:
1. original_rt_snippets.txt contains 10,605 processed snippets from the original pool of Rotten Tomatoes HTML files. Please note that some snippet may contain multiple sentences.

2. dictionary.txt contains all phrases and their IDs, separated by a vertical line |

3. sentiment_labels.txt contains all phrase ids and the corresponding sentiment labels, separated by a vertical line.
Note that you can recover the 5 classes by mapping the positivity probability using the following cut-offs:
[0, 0.2], (0.2, 0.4], (0.4, 0.6], (0.6, 0.8], (0.8, 1.0]
for very negative, negative, neutral, positive, very positive, respectively.
Please note that phrase ids and sentence ids are not the same.

4. SOStr.txt and STree.txt encode the structure of the parse trees. 
STree encodes the trees in a parent pointer format. Each line corresponds to each sentence in the datasetSentences.txt file. The Matlab code of this paper will show you how to read this format if you are not familiar with it.

5. datasetSentences.txt contains the sentence index, followed by the sentence string separated by a tab. These are the sentences of the train/dev/test sets.

6. datasetSplit.txt contains the sentence index (corresponding to the index in datasetSentences.txt file) followed by the set label separated by a comma:
	1 = train
	2 = test
	3 = dev

Please note that the datasetSentences.txt file has more sentences/lines than the original_rt_snippet.txt. 
Each row in the latter represents a snippet as shown on RT, whereas the former is each sub sentence as determined by the Stanford parser.

For comparing research and training models, please use the provided train/dev/test splits.


# Model Architecture

	classifier(
	  (embedding): Embedding(20896, 300)
	  (encoder): LSTM(300, 100, num_layers=2, batch_first=True, dropout=0.2)
	  (fc): Linear(in_features=100, out_features=3, bias=True)
	)
	The model has 6,510,703 trainable parameters


# Training log

	Train Loss: 0.933 | Train Acc: 61.09%
	 Val. Loss: 0.864 |  Val. Acc: 67.80% 

	Train Loss: 0.835 | Train Acc: 71.13%
	 Val. Loss: 0.838 |  Val. Acc: 70.32% 

	Train Loss: 0.801 | Train Acc: 74.69%
	 Val. Loss: 0.817 |  Val. Acc: 73.30% 

	Train Loss: 0.781 | Train Acc: 76.79%
	 Val. Loss: 0.818 |  Val. Acc: 72.67% 

	Train Loss: 0.767 | Train Acc: 78.27%
	 Val. Loss: 0.811 |  Val. Acc: 73.81% 

	Train Loss: 0.755 | Train Acc: 79.51%
	 Val. Loss: 0.809 |  Val. Acc: 73.77% 

	Train Loss: 0.746 | Train Acc: 80.46%
	 Val. Loss: 0.810 |  Val. Acc: 73.81% 

	Train Loss: 0.738 | Train Acc: 81.30%
	 Val. Loss: 0.803 |  Val. Acc: 74.34% 

	Train Loss: 0.731 | Train Acc: 82.04%
	 Val. Loss: 0.814 |  Val. Acc: 73.39% 

	Train Loss: 0.725 | Train Acc: 82.66%
	 Val. Loss: 0.817 |  Val. Acc: 73.11% 
	 
## Test Loss and Accuracy  
	Test Loss: 0.777 | Test Acc: 76.78%
