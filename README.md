## An Investigation of Recurrent Neural Architectures for Drug Name Recognition

Drug name recognition (DNR) is an essential step in the Pharmacovigilance (PV) pipeline. DNR aims to find drug name mentions in un- structured biomedical texts and classify them into predefined categories. State-of-the-art DNR approaches heavily rely on hand-crafted features and domain-specific resources which are difficult to collect and tune. For this reason, this paper investigates the effectiveness of contemporary recurrent neural architectures - the Elman and Jordan networks and the bidi- rectional LSTM with CRF decoding - at performing DNR straight from the text. The experimental results achieved on the authoritative SemEval-2013 Task 9.1 benchmarks show that the bidirectional LSTM-CRF ranks closely to highly-dedicated, hand-crafted systems.

This repository contains the code and  sample data (DrugBank, MedLine) data sets used in the accepted paper "An Investigation of Recurrent Neural Architectures for Drug Name Recognition"  at LOUHI 2016 : EMNLP 2016 Workshop - The Seventh International Workshop on Health Text Mining and Information Analysis (LOUHI 2016)

## If you use this code  in your scientific publications  kindly cite the papers below .


["An Investigation of Recurrent Neural Architectures for Drug Name Recognition"  at LOUHI 2016 : EMNLP 2016 Workshop - The Seventh International Workshop on Health Text Mining and Information Analysis (LOUHI 2016)](http://128.84.21.199/pdf/1609.07585.pdf)


##If you plan to use the  data(DrugBank and Medline) 
Kindly send a e-mail request to ISABEL SEGURA BEDMAR <isegura@inf.uc3m.es> in order to obtain  complete data. 


## Initial setup

To use the dnr, you need Python 2.7, with Numpy and Theano installed.


## Using DNR

The fastest way to use the dnr  is to use one of the pretrained models:

```
./dnr.py --model models/english/ --input input.txt --output output.txt
```

The input file should contain one sentence by line, and they have to be tokenized.
Otherwise, the DNR will perform poorly.


## Train a model

To train your own model, you need to use the train.py script and provide the location of the training,
development and testing set:

```
./train.py --train train.txt --dev dev.txt --test test.txt
```

The training script will automatically give a name to the model and store it in ./models/
There are many parameters you can tune (CRF, dropout rate, embedding dimension, LSTM hidden layer size, etc).
To see all parameters, simply run:

```
./train.py --help
```

Input files for the training script have to follow the same format than the CoNLL2003 sharing task:
each word has to be on a separate line, and there must be an empty line after each sentence.
 A line must contain at least 2 columns, the first one being the word itself, the last one being the named entity.
 It does not matter if there are extra columns that contain tags or chunks in between.
 Tags have to be given in the IOB format (it can be IOB1 or IOB2).


## Train a model in a loop using the Hyper parameters

To train your own model, you need to use the train_loop.py script and provide the location of the training,
development and testing set: if not specified the default locations of ./dnr/data/conll2003/ would be choosen

```
./train_loop.py --train train.txt --dev dev.txt --test test.txt
```

The training script will automatically give a name to the model and store it in ./models/
There are many parameters you can tune (CRF, dropout rate, embedding dimension, LSTM hidden layer size, etc).
To see all parameters, simply run:



