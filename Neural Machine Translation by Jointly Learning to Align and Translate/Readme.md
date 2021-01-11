In this notebook on sequence-to-sequence models using PyTorch and TorchText, we'll be implementing the model from [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473) on 
following datasets :

1. [Multi30k dataset] (https://github.com/multi30k/dataset) This is a dataset with ~30,000 parallel English, German and French sentences, each with ~12 words per sentence. 

2.  [Question-and-answer dataset](http://www.cs.cmu.edu/~ark/QA-data/): This corpus includes Wikipedia articles, factual questions manually generated from them, and answers to these manually generated questions for use in academic research.
    [Link to Code](Question_Answer_Seq_2_Seq)

3. [Customer Support on Twitter](https://www.kaggle.com/thoughtvector/customer-support-on-twitter) : This Kaggle dataset includes more than 3 million tweets and responses from leading brands on Twitter.
    [Link to Code](Twitter_Seq_2_Seq)

4. [The Stanford Question Answering Dataset (SQuAD)](https://rajpurkar.github.io/SQuAD-explorer/) is a set of reading comprehension data consisting of questions asked by social workers on a set of Wikipedia articles, where the answer to each question is a segment of text, or span, of the corresponding reading passage. With more than 100,000 question-answer pairs on more than 500 articles, SQuAD is significantly larger than previous reading comprehension datasets. SQuAD2.0 combines the 100,000 questions from SQuAD1.1 with more than 50,000 new unanswered questions written in a contradictory manner by crowd workers to look like answered questions.
    [Link to Code](SQuAD_Seq_2_Seq)

5. [CoQA](https://stanfordnlp.github.io/coqa/) is a large-scale data set for the construction of conversational question answering systems. The CoQA contains 127,000 questions with answers, obtained from 8,000 conversations involving text passages from seven different domains.
    [Link to Code](CoQA_Seq_2_Seq)
    
    
    
The models can be applied to any problem that involves going from one sequence to another, such as summarization, i.e. going from a sequence to a shorter sequence in the same language.


## Introduction:
Here is the general encoder-decoder model:

![](https://github.com/bentrevett/pytorch-seq2seq/blob/master/assets/seq2seq1.png?raw=1)

The most common sequence-to-sequence (seq2seq) models are encoder-decoder models, which commonly use a recurrent neural network (RNN) to encode the source (input) sentence into a single vector.We can think of the context vector as being an abstract representation of the entire input sentence. This vector is then decoded by a second RNN which learns to output the target (output) sentence by generating it one word at a time.

One downside of the previous model is that the decoder is trying to cram lots of information into the hidden states. Whilst decoding, the hidden state will need to contain information about the whole of the source sequence, as well as all of the tokens have been decoded so far. By alleviating some of this information compression, we can create a better model!

Here is the another model,

![](https://github.com/bentrevett/pytorch-seq2seq/blob/master/assets/seq2seq7.png?raw=1)

Architecture in this is set-up in a way to reduce "information compression" by explicitly passing the context vector, z, to the decoder at every time-step and by passing both the context vector and embedded input word, d(y_t), along with the hidden state, s_t, to the linear layer, f, to make a prediction.

In this model, even though we could reduce some of this compression, our context vector still needs to contain all of the information about the source sentence. 

Next, is the attention model from [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473)

![](https://github.com/bentrevett/pytorch-seq2seq/blob/master/assets/seq2seq10.png?raw=1)


The model implemented in this notebook avoids this compression by allowing the decoder to look at the entire source sentence (via its hidden states) at each decoding step! How does it do this? It uses *attention*. 

Attention works by first, calculating an attention vector, a, that is the length of the source sentence. The attention vector has the property that each element is between 0 and 1, and the entire vector sums to 1. We then calculate a weighted sum of our source sentence hidden states, H, to get a weighted source vector, w. 

$$w = \sum_{i}a_ih_i$$

We calculate a new weighted source vector every time-step when decoding, using it as input to our decoder RNN as well as the linear layer to make a prediction. 


Also, as an improvment Packed padded sequences and Masking is been added to the model to reduce the training time, Packed padded sequences are used to tell our RNN to skip over padding tokens in our encoder. Masking explicitly forces the model to ignore certain values, such as attention over padded elements.

