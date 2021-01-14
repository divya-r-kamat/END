
# German to English Translation

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
    
 # [Model 1](01_German_to_English_Translation_using_Attention.ipynb)
    
 Training Log
    
       Epoch: 01 | Time: 1m 19s
        Train Loss: 5.021 | Train PPL: 151.526
         Val. Loss: 4.812 |  Val. PPL: 122.932
      Epoch: 02 | Time: 1m 22s
        Train Loss: 4.123 | Train PPL:  61.719
         Val. Loss: 4.576 |  Val. PPL:  97.084
      Epoch: 03 | Time: 1m 23s
        Train Loss: 3.464 | Train PPL:  31.956
         Val. Loss: 3.712 |  Val. PPL:  40.955
      Epoch: 04 | Time: 1m 25s
        Train Loss: 2.913 | Train PPL:  18.412
         Val. Loss: 3.431 |  Val. PPL:  30.919
      Epoch: 05 | Time: 1m 24s
        Train Loss: 2.516 | Train PPL:  12.385
         Val. Loss: 3.229 |  Val. PPL:  25.261
      Epoch: 06 | Time: 1m 25s
        Train Loss: 2.226 | Train PPL:   9.261
         Val. Loss: 3.238 |  Val. PPL:  25.479
      Epoch: 07 | Time: 1m 24s
        Train Loss: 1.986 | Train PPL:   7.286
         Val. Loss: 3.156 |  Val. PPL:  23.472
      Epoch: 08 | Time: 1m 24s
        Train Loss: 1.771 | Train PPL:   5.879
         Val. Loss: 3.177 |  Val. PPL:  23.976
      Epoch: 09 | Time: 1m 25s
        Train Loss: 1.597 | Train PPL:   4.938
         Val. Loss: 3.252 |  Val. PPL:  25.848
      Epoch: 10 | Time: 1m 24s
        Train Loss: 1.487 | Train PPL:   4.422
         Val. Loss: 3.343 |  Val. PPL:  28.309
      Epoch: 11 | Time: 1m 24s
        Train Loss: 1.355 | Train PPL:   3.876
         Val. Loss: 3.358 |  Val. PPL:  28.726
      Epoch: 12 | Time: 1m 24s
        Train Loss: 1.261 | Train PPL:   3.528
         Val. Loss: 3.421 |  Val. PPL:  30.587
      Epoch: 13 | Time: 1m 24s
        Train Loss: 1.167 | Train PPL:   3.213
         Val. Loss: 3.431 |  Val. PPL:  30.914
      Epoch: 14 | Time: 1m 24s
        Train Loss: 1.080 | Train PPL:   2.944
         Val. Loss: 3.599 |  Val. PPL:  36.553
      Epoch: 15 | Time: 1m 24s
        Train Loss: 1.033 | Train PPL:   2.808
         Val. Loss: 3.565 |  Val. PPL:  35.337
      Epoch: 16 | Time: 1m 24s
        Train Loss: 0.955 | Train PPL:   2.600
         Val. Loss: 3.614 |  Val. PPL:  37.101
      Epoch: 17 | Time: 1m 24s
        Train Loss: 0.888 | Train PPL:   2.430
         Val. Loss: 3.716 |  Val. PPL:  41.111
      Epoch: 18 | Time: 1m 24s
        Train Loss: 0.842 | Train PPL:   2.322
         Val. Loss: 3.743 |  Val. PPL:  42.225
      Epoch: 19 | Time: 1m 24s
        Train Loss: 0.785 | Train PPL:   2.193
         Val. Loss: 3.896 |  Val. PPL:  49.223
      Epoch: 20 | Time: 1m 24s
        Train Loss: 0.731 | Train PPL:   2.076
        Val. Loss: 3.947 |  Val. PPL:  51.781

 Test Loss
 
      | Test Loss: 3.178 | Test PPL:  24.009 |
      
      
# [Model 2](02_German_to_English_Translation_using_Attension_with_Packed_Padded_Sequences_and_masking.ipynb)
 
 Used packed padded sequences and masking - to the model from the previous notebook. Packed padded sequences are used to tell our RNN to skip over padding tokens in our encoder. Masking explicitly forces the model to ignore certain values, such as attention over padded elements.
 
 Training Log
 
        Epoch: 01 | Time: 0m 45s
          Train Loss: 5.038 | Train PPL: 154.181
           Val. Loss: 4.750 |  Val. PPL: 115.532
        Epoch: 02 | Time: 0m 47s
          Train Loss: 4.036 | Train PPL:  56.573
           Val. Loss: 4.020 |  Val. PPL:  55.721
        Epoch: 03 | Time: 0m 47s
          Train Loss: 3.300 | Train PPL:  27.123
           Val. Loss: 3.572 |  Val. PPL:  35.583
        Epoch: 04 | Time: 0m 47s
          Train Loss: 2.807 | Train PPL:  16.565
           Val. Loss: 3.337 |  Val. PPL:  28.132
        Epoch: 05 | Time: 0m 47s
          Train Loss: 2.435 | Train PPL:  11.416
           Val. Loss: 3.238 |  Val. PPL:  25.489
        Epoch: 06 | Time: 0m 47s
          Train Loss: 2.153 | Train PPL:   8.612
           Val. Loss: 3.359 |  Val. PPL:  28.773
        Epoch: 07 | Time: 0m 47s
          Train Loss: 1.922 | Train PPL:   6.834
           Val. Loss: 3.138 |  Val. PPL:  23.054
        Epoch: 08 | Time: 0m 47s
          Train Loss: 1.726 | Train PPL:   5.617
           Val. Loss: 3.241 |  Val. PPL:  25.555
        Epoch: 09 | Time: 0m 47s
          Train Loss: 1.585 | Train PPL:   4.877
           Val. Loss: 3.262 |  Val. PPL:  26.108
        Epoch: 10 | Time: 0m 47s
          Train Loss: 1.472 | Train PPL:   4.356
           Val. Loss: 3.297 |  Val. PPL:  27.034
        Epoch: 11 | Time: 0m 47s
          Train Loss: 1.315 | Train PPL:   3.724
           Val. Loss: 3.461 |  Val. PPL:  31.864
        Epoch: 12 | Time: 0m 47s
          Train Loss: 1.235 | Train PPL:   3.439
           Val. Loss: 3.455 |  Val. PPL:  31.657
        Epoch: 13 | Time: 0m 47s
          Train Loss: 1.134 | Train PPL:   3.107
           Val. Loss: 3.522 |  Val. PPL:  33.845
        Epoch: 14 | Time: 0m 47s
          Train Loss: 1.046 | Train PPL:   2.845
           Val. Loss: 3.603 |  Val. PPL:  36.716
        Epoch: 15 | Time: 0m 47s
          Train Loss: 0.992 | Train PPL:   2.695
           Val. Loss: 3.621 |  Val. PPL:  37.367
        Epoch: 16 | Time: 0m 47s
          Train Loss: 0.923 | Train PPL:   2.516
           Val. Loss: 3.732 |  Val. PPL:  41.757
        Epoch: 17 | Time: 0m 47s
          Train Loss: 0.849 | Train PPL:   2.337
           Val. Loss: 3.742 |  Val. PPL:  42.179
        Epoch: 18 | Time: 0m 47s
          Train Loss: 0.792 | Train PPL:   2.207
           Val. Loss: 3.855 |  Val. PPL:  47.218
        Epoch: 19 | Time: 0m 47s
          Train Loss: 0.744 | Train PPL:   2.105
           Val. Loss: 3.969 |  Val. PPL:  52.923
        Epoch: 20 | Time: 0m 47s
          Train Loss: 0.706 | Train PPL:   2.025
           Val. Loss: 4.020 |  Val. PPL:  55.685

Test Loss

     | Test Loss: 3.184 | Test PPL:  24.147 |

# BLEU Score

In the previous model  we have only cared about the loss/perplexity of the model. However there metrics that are specifically designed for measuring the quality of a translation - the most popular is BLEU. BLEU looks at the overlap in the predicted and actual target sequences in terms of their n-grams. It will give us a number between 0 and 1 for each sequence, where 1 means there is perfect overlap, i.e. a perfect translation, although is usually shown between 0 and 100. BLEU was designed for multiple candidate translations per source sequence, however in this dataset we only have one candidate per source. Higher BLEU score is "better".

      We get a BLEU of around 30.63.
