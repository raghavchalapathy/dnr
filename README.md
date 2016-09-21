# dnr
## An Investigation of Recurrent Neural Architectures for Drug Name Recognition

Drug name recognition (DNR) is an essential step in the Pharmacovigilance (PV) pipeline. DNR aims to find drug name mentions in unstructured biomedical texts and classify them into predefined categories. State-of-the-art DNR approaches heavily rely on hand-crafted features and domain-specific resources which are difficult to collect and tune. For this reason , this paper investigates the effectiveness of contemporary recurrent neural architectures - the Elman and Jordan networks and the bidirectional LSTM with CRF decoding - at performing DNR straight from the text. The experimental results achieved on the author- itative SemEval-2013 Task 9.1 benchmarks show that the bidirectional LSTM-CRF ranks closely to highly-dedicated, hand-crafted systems.

The repository contains code and instructions to execute the recurrent neural architecture models.

## Initial setup

To use the dnr, you need Python 2.7, with Numpy and Theano installed.


## Using DNR-bidirectional LSTM CRF model

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



## Using DrugBank and Medline DataSets in your experiments.

If you plan to use the data DrugBank and Medline  in your experiments kindly cite the below papers.

Isabel Segura-Bedmar, Paloma Mart ́ınez, and Mar ́ıa Her- rero Zazo. 2013. Semeval-2013 task 9: Extraction of drug-drug interactions from biomedical texts (DDIEx- traction 2013). In The 7th International Workshop on Semantic Evaluation



The code was forked and reused from
