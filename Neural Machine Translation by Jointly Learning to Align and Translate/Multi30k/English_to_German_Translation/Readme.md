
# English to German Translation

Dataset

Multik30 dataset - This is a dataset with ~30,000 parallel English, German and French sentences, each with ~12 words per sentence taken from PyTorch dataset


Model Architecture

    Seq2Seq(
      (encoder): Encoder(
        (embedding): Embedding(2197, 256)
        (rnn): GRU(256, 512, bidirectional=True)
        (fc): Linear(in_features=1024, out_features=512, bias=True)
        (dropout): Dropout(p=0.5, inplace=False)
      )
      (decoder): Decoder(
        (attention): Attention(
          (attn): Linear(in_features=1536, out_features=512, bias=True)
          (v): Linear(in_features=512, out_features=1, bias=False)
        )
        (embedding): Embedding(1504, 256)
        (rnn): GRU(1280, 512)
        (fc_out): Linear(in_features=1792, out_features=1504, bias=True)
        (dropout): Dropout(p=0.5, inplace=False)
      )
    )
    
 # [Model 1](01_English_to_German_Translation_using_Attention.ipynb)
    
 Training Log
    
      Epoch: 01 | Time: 1m 31s
        Train Loss: 5.039 | Train PPL: 154.270
         Val. Loss: 4.988 |  Val. PPL: 146.571
      Epoch: 02 | Time: 1m 34s
        Train Loss: 4.060 | Train PPL:  57.950
         Val. Loss: 4.249 |  Val. PPL:  70.014
      Epoch: 03 | Time: 1m 34s
        Train Loss: 3.388 | Train PPL:  29.618
         Val. Loss: 3.526 |  Val. PPL:  33.979
      Epoch: 04 | Time: 1m 35s
        Train Loss: 2.803 | Train PPL:  16.491
         Val. Loss: 3.266 |  Val. PPL:  26.205
      Epoch: 05 | Time: 1m 34s
        Train Loss: 2.366 | Train PPL:  10.657
         Val. Loss: 3.159 |  Val. PPL:  23.558
      Epoch: 06 | Time: 1m 35s
        Train Loss: 2.051 | Train PPL:   7.774
         Val. Loss: 3.010 |  Val. PPL:  20.295
      Epoch: 07 | Time: 1m 34s
        Train Loss: 1.793 | Train PPL:   6.005
         Val. Loss: 3.076 |  Val. PPL:  21.666
      Epoch: 08 | Time: 1m 34s
        Train Loss: 1.577 | Train PPL:   4.842
         Val. Loss: 3.174 |  Val. PPL:  23.903
      Epoch: 09 | Time: 1m 34s
        Train Loss: 1.438 | Train PPL:   4.213
         Val. Loss: 3.160 |  Val. PPL:  23.578
      Epoch: 10 | Time: 1m 34s
        Train Loss: 1.322 | Train PPL:   3.750
         Val. Loss: 3.198 |  Val. PPL:  24.491
      Epoch: 11 | Time: 1m 35s
        Train Loss: 1.212 | Train PPL:   3.360
         Val. Loss: 3.303 |  Val. PPL:  27.201
      Epoch: 12 | Time: 1m 34s
        Train Loss: 1.102 | Train PPL:   3.011
         Val. Loss: 3.351 |  Val. PPL:  28.518
      Epoch: 13 | Time: 1m 33s
        Train Loss: 1.009 | Train PPL:   2.742
         Val. Loss: 3.393 |  Val. PPL:  29.752
      Epoch: 14 | Time: 1m 34s
        Train Loss: 0.937 | Train PPL:   2.553
         Val. Loss: 3.497 |  Val. PPL:  33.018
      Epoch: 15 | Time: 1m 34s
        Train Loss: 0.872 | Train PPL:   2.391
         Val. Loss: 3.545 |  Val. PPL:  34.639
      Epoch: 16 | Time: 1m 34s
        Train Loss: 0.799 | Train PPL:   2.224
         Val. Loss: 3.610 |  Val. PPL:  36.961
      Epoch: 17 | Time: 1m 34s
        Train Loss: 0.737 | Train PPL:   2.090
         Val. Loss: 3.662 |  Val. PPL:  38.927
      Epoch: 18 | Time: 1m 34s
        Train Loss: 0.676 | Train PPL:   1.965
         Val. Loss: 3.753 |  Val. PPL:  42.643
      Epoch: 19 | Time: 1m 34s
        Train Loss: 0.636 | Train PPL:   1.889
         Val. Loss: 3.774 |  Val. PPL:  43.555
      Epoch: 20 | Time: 1m 34s
        Train Loss: 0.588 | Train PPL:   1.801
         Val. Loss: 3.898 |  Val. PPL:  49.322
  
 Test Loss
 
      | Test Loss: 3.023 | Test PPL:  20.559 |
      
      
# [Model 2](02_English_to_German_Translation_using_Attension_with_Packed_Padded_Sequences_and_masking.ipynb)
 
 Used packed padded sequences and masking - to the model from the previous notebook. Packed padded sequences are used to tell our RNN to skip over padding tokens in our encoder. Masking explicitly forces the model to ignore certain values, such as attention over padded elements.
 
 Training Log
 
       Epoch: 01 | Time: 0m 51s
        Train Loss: 5.164 | Train PPL: 174.828
         Val. Loss: 4.823 |  Val. PPL: 124.306
      Epoch: 02 | Time: 0m 54s
        Train Loss: 4.093 | Train PPL:  59.893
         Val. Loss: 4.080 |  Val. PPL:  59.164
      Epoch: 03 | Time: 0m 56s
        Train Loss: 3.297 | Train PPL:  27.032
         Val. Loss: 3.518 |  Val. PPL:  33.709
      Epoch: 04 | Time: 0m 55s
        Train Loss: 2.732 | Train PPL:  15.366
         Val. Loss: 3.246 |  Val. PPL:  25.676
      Epoch: 05 | Time: 0m 55s
        Train Loss: 2.318 | Train PPL:  10.160
         Val. Loss: 3.136 |  Val. PPL:  23.019
      Epoch: 06 | Time: 0m 55s
        Train Loss: 1.982 | Train PPL:   7.257
         Val. Loss: 3.128 |  Val. PPL:  22.839
      Epoch: 07 | Time: 0m 55s
        Train Loss: 1.742 | Train PPL:   5.707
         Val. Loss: 3.161 |  Val. PPL:  23.596
      Epoch: 08 | Time: 0m 55s
        Train Loss: 1.570 | Train PPL:   4.807
         Val. Loss: 3.144 |  Val. PPL:  23.190
      Epoch: 09 | Time: 0m 55s
        Train Loss: 1.427 | Train PPL:   4.165
         Val. Loss: 3.150 |  Val. PPL:  23.331
      Epoch: 10 | Time: 0m 55s
        Train Loss: 1.322 | Train PPL:   3.753
         Val. Loss: 3.224 |  Val. PPL:  25.127
      Epoch: 11 | Time: 0m 55s
        Train Loss: 1.211 | Train PPL:   3.356
         Val. Loss: 3.334 |  Val. PPL:  28.048
      Epoch: 12 | Time: 0m 55s
        Train Loss: 1.109 | Train PPL:   3.032
         Val. Loss: 3.297 |  Val. PPL:  27.043
      Epoch: 13 | Time: 0m 55s
        Train Loss: 1.021 | Train PPL:   2.776
         Val. Loss: 3.438 |  Val. PPL:  31.138
      Epoch: 14 | Time: 0m 55s
        Train Loss: 0.967 | Train PPL:   2.629
         Val. Loss: 3.480 |  Val. PPL:  32.471
      Epoch: 15 | Time: 0m 55s
        Train Loss: 0.891 | Train PPL:   2.437
         Val. Loss: 3.512 |  Val. PPL:  33.519
      Epoch: 16 | Time: 0m 55s
        Train Loss: 0.833 | Train PPL:   2.301
         Val. Loss: 3.574 |  Val. PPL:  35.677
      Epoch: 17 | Time: 0m 56s
        Train Loss: 0.756 | Train PPL:   2.130
         Val. Loss: 3.671 |  Val. PPL:  39.301
      Epoch: 18 | Time: 0m 55s
        Train Loss: 0.713 | Train PPL:   2.041
         Val. Loss: 3.726 |  Val. PPL:  41.529
      Epoch: 19 | Time: 0m 55s
        Train Loss: 0.679 | Train PPL:   1.972
         Val. Loss: 3.742 |  Val. PPL:  42.185
      Epoch: 20 | Time: 0m 55s
        Train Loss: 0.642 | Train PPL:   1.901
         Val. Loss: 3.832 |  Val. PPL:  46.164

Test Loss

      | Test Loss: 3.163 | Test PPL:  23.643 |

# BLEU Score

In the previous model  we have only cared about the loss/perplexity of the model. However there metrics that are specifically designed for measuring the quality of a translation - the most popular is BLEU. BLEU looks at the overlap in the predicted and actual target sequences in terms of their n-grams. It will give us a number between 0 and 1 for each sequence, where 1 means there is perfect overlap, i.e. a perfect translation, although is usually shown between 0 and 100. BLEU was designed for multiple candidate translations per source sequence, however in this dataset we only have one candidate per source. Higher BLEU score is "better".

      We get a BLEU of around 26.56 .
