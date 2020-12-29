# The Stanford Question Answering Dataset (SQuAD)

Stanford Question Answering Dataset (SQuAD) is a reading comprehension dataset, consisting of questions posed by crowdworkers on a set of Wikipedia articles, where the answer to every question is a segment of text, or span, from the corresponding reading passage, or the question might be unanswerable.

SQuAD2.0 combines the 100,000 questions in SQuAD1.1 with over 50,000 unanswerable questions written adversarially by crowdworkers to look similar to answerable ones. To do well on SQuAD2.0, systems must not only answer questions when possible, but also determine when no answer is supported by the paragraph and abstain from answering.


# [Model1] (SQuAD_Dataset_Learning_Phrase_Representation_RNN_Encoder_Decoder.ipynb)

Model Architecture

    Seq2Seq(
      (encoder): Encoder(
        (embedding): Embedding(18975, 256)
        (rnn): GRU(256, 512)
        (dropout): Dropout(p=0.5, inplace=False)
      )
      (decoder): Decoder(
        (embedding): Embedding(16465, 256)
        (rnn): GRU(768, 512)
        (fc_out): Linear(in_features=1280, out_features=16465, bias=True)
        (dropout): Dropout(p=0.5, inplace=False)
      )
    )

Training Log

    Epoch: 01 | Time: 3m 29s
      Train Loss: 6.215 | Train PPL: 500.413
       Val. Loss: 5.774 |  Val. PPL: 321.878
    Epoch: 02 | Time: 3m 32s
      Train Loss: 5.764 | Train PPL: 318.576
       Val. Loss: 5.538 |  Val. PPL: 254.253
    Epoch: 03 | Time: 3m 30s
      Train Loss: 5.375 | Train PPL: 215.936
       Val. Loss: 5.387 |  Val. PPL: 218.603
    Epoch: 04 | Time: 3m 30s
      Train Loss: 5.036 | Train PPL: 153.786
       Val. Loss: 5.306 |  Val. PPL: 201.499
    Epoch: 05 | Time: 3m 27s
      Train Loss: 4.661 | Train PPL: 105.735
       Val. Loss: 5.355 |  Val. PPL: 211.761
    Epoch: 06 | Time: 3m 29s
      Train Loss: 4.272 | Train PPL:  71.671
       Val. Loss: 5.474 |  Val. PPL: 238.498
    Epoch: 07 | Time: 3m 30s
      Train Loss: 3.813 | Train PPL:  45.268
       Val. Loss: 5.700 |  Val. PPL: 298.801
    Epoch: 08 | Time: 3m 31s
      Train Loss: 3.307 | Train PPL:  27.314
       Val. Loss: 5.952 |  Val. PPL: 384.513
    Epoch: 09 | Time: 3m 30s
      Train Loss: 2.837 | Train PPL:  17.061
       Val. Loss: 6.188 |  Val. PPL: 486.727
    Epoch: 10 | Time: 3m 29s
      Train Loss: 2.474 | Train PPL:  11.867
       Val. Loss: 6.360 |  Val. PPL: 578.040
       
Test Loss

    | Test Loss: 5.376 | Test PPL: 216.088 |
