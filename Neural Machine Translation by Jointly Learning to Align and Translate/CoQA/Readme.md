# CoQA - A Conversational Question Answering Challenge

CoQA is a large-scale dataset for building Conversational Question Answering systems. The goal of the CoQA challenge is to measure the ability of machines to understand a text passage and answer a series of interconnected questions that appear in a conversation. CoQA is pronounced as coca

CoQA contains 127,000+ questions with answers collected from 8000+ conversations. Each conversation is collected by pairing two crowdworkers to chat about a passage in the form of questions and answers. The unique features of CoQA include 1) the questions are conversational; 2) the answers can be free-form text; 3) each answer also comes with an evidence subsequence highlighted in the passage; and 4) the passages are collected from seven diverse domains. CoQA has a lot of challenging phenomena not present in existing reading comprehension datasets, e.g., coreference and pragmatic reasoning.

## License
CoQA contains passages from seven domains. We make five of these public under the following licenses:
- Literature and Wikipedia passages are shared under CC BY-SA 4.0 license.
- Children's stories are collected from MCTest which comes with MSR-LA license.
- Middle/High school exam passages are collected from RACE which comes with its own license.
- News passages are collected from the DeepMind CNN dataset which comes with Apache license.

Model Architecture

    Seq2Seq(
      (encoder): Encoder(
        (embedding): Embedding(24009, 256)
        (rnn): GRU(256, 512, bidirectional=True)
        (fc): Linear(in_features=1024, out_features=512, bias=True)
        (dropout): Dropout(p=0.5, inplace=False)
      )
      (decoder): Decoder(
        (attention): Attention(
          (attn): Linear(in_features=1536, out_features=512, bias=True)
          (v): Linear(in_features=512, out_features=1, bias=False)
        )
        (embedding): Embedding(23030, 256)
        (rnn): GRU(1280, 512)
        (fc_out): Linear(in_features=1792, out_features=23030, bias=True)
        (dropout): Dropout(p=0.5, inplace=False)
      )
    )


# [Model1](01_CoQA_Dataset_Sequence_to_Sequence_using_Attention.ipynb)



Training Log

    Epoch: 01 | Time: 10m 17s
        Train Loss: 6.186 | Train PPL: 486.004
         Val. Loss: 5.626 |  Val. PPL: 277.518
    Epoch: 02 | Time: 10m 19s
        Train Loss: 5.367 | Train PPL: 214.246
         Val. Loss: 5.341 |  Val. PPL: 208.736
    Epoch: 03 | Time: 10m 22s
        Train Loss: 4.675 | Train PPL: 107.207
         Val. Loss: 5.264 |  Val. PPL: 193.284
    Epoch: 04 | Time: 10m 21s
        Train Loss: 3.839 | Train PPL:  46.499
         Val. Loss: 5.287 |  Val. PPL: 197.722
    Epoch: 05 | Time: 10m 25s
        Train Loss: 3.097 | Train PPL:  22.135
         Val. Loss: 5.421 |  Val. PPL: 226.052
    Epoch: 06 | Time: 10m 23s
        Train Loss: 2.562 | Train PPL:  12.957
         Val. Loss: 5.607 |  Val. PPL: 272.382
    Epoch: 07 | Time: 10m 21s
        Train Loss: 2.215 | Train PPL:   9.165
         Val. Loss: 5.761 |  Val. PPL: 317.798
    Epoch: 08 | Time: 10m 20s
        Train Loss: 1.958 | Train PPL:   7.085
         Val. Loss: 5.919 |  Val. PPL: 371.877
    Epoch: 09 | Time: 10m 19s
        Train Loss: 1.767 | Train PPL:   5.855
         Val. Loss: 6.068 |  Val. PPL: 431.622
    Epoch: 10 | Time: 10m 23s
        Train Loss: 1.611 | Train PPL:   5.008
         Val. Loss: 6.198 |  Val. PPL: 491.986

Test Loss

     | Test Loss: 5.687 | Test PPL: 294.983 |
       
    
# [Model2](02_CoQA_Seq2Seq_using_Attention_with_packed_padded_sequence_and_masking.ipynb)

Used packed padded sequences and masking - to the model from the previous notebook. Packed padded sequences are used to tell our RNN to skip over padding tokens in our encoder. Masking explicitly forces the model to ignore certain values, such as attention over padded elements.
   
Training Log

    Epoch: 01 | Time: 6m 9s
        Train Loss: 6.195 | Train PPL: 490.211
         Val. Loss: 5.579 |  Val. PPL: 264.675
    Epoch: 02 | Time: 6m 12s
        Train Loss: 5.347 | Train PPL: 210.056
         Val. Loss: 5.310 |  Val. PPL: 202.292
    Epoch: 03 | Time: 6m 11s
        Train Loss: 4.638 | Train PPL: 103.378
         Val. Loss: 5.179 |  Val. PPL: 177.560
    Epoch: 04 | Time: 6m 11s
        Train Loss: 3.787 | Train PPL:  44.129
         Val. Loss: 5.225 |  Val. PPL: 185.832
    Epoch: 05 | Time: 6m 11s
        Train Loss: 3.053 | Train PPL:  21.173
         Val. Loss: 5.359 |  Val. PPL: 212.460
    Epoch: 06 | Time: 6m 11s
        Train Loss: 2.528 | Train PPL:  12.525
         Val. Loss: 5.516 |  Val. PPL: 248.647
    Epoch: 07 | Time: 6m 9s
        Train Loss: 2.191 | Train PPL:   8.941
         Val. Loss: 5.688 |  Val. PPL: 295.203
    Epoch: 08 | Time: 6m 11s
        Train Loss: 1.949 | Train PPL:   7.025
         Val. Loss: 5.836 |  Val. PPL: 342.487
    Epoch: 09 | Time: 6m 12s
        Train Loss: 1.765 | Train PPL:   5.843
         Val. Loss: 5.950 |  Val. PPL: 383.678
    Epoch: 10 | Time: 6m 9s
        Train Loss: 1.620 | Train PPL:   5.053
         Val. Loss: 6.090 |  Val. PPL: 441.535
       
Test Loss
   
       | Test Loss: 5.631 | Test PPL: 278.868 |

