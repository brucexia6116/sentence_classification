# Sentence Classification

Implementation of sentence classification using CNN, and RNN with LSTM/GRU units.

## Dependencies

This code is written in python. To use it you will need:

* Python 2.7
* Theano 0.7
* A recent version of [NumPy](http://www.numpy.org/) 
* [NLTK 3](http://www.nltk.org/) (for dataset preprocessing)

## Getting started

1. We use TREC Question-Type Classification as a demo to illustrate the usage of CNN/LSTM/GRU classifier.

2. Download the dataset from http://cogcomp.cs.illinois.edu/Data/QA/QC/ (train_5500.label and TREC_10.label) and put these into the data directory. 

3. Since the dataset is relatively small, we use the pretrained word embedding as the initialization of the word embedding parameters (to be refined). 

4. Using the `word2vec` vectors will require downloading the binary file (i.e. `GoogleNews-vectors-negative300.bin` file) from https://code.google.com/p/word2vec/. Put this binary file into the data directory.

5. To process the raw data, run

```
cd ./data
python process_trec.py
```

### Running the models 

This code can be run in CPU/GPU devices directly.  

Example commands:

```
THEANO_FLAGS=mode=FAST_RUN,device=gpu,floatX=float32 python eval_trec_cnn.py 
THEANO_FLAGS=mode=FAST_RUN,device=gpu,floatX=float32 python eval_trec_lstm.py
THEANO_FLAGS=mode=FAST_RUN,device=gpu,floatX=float32 python eval_trec_gru.py 
```

For each classifier, we run the algorithm 10 times and take the average as the final test error. The classification accuracies after running the code should be close to the following numbers. 

```
CNN: 93.30 \pm 0.59   LSTM: 93.14 \pm 0.69    GRU: 92.66 \pm 0.77
```

All the printout information will be stored into a log file. 

#### Acknowledgments
Our implementation utilizes code from the following:

* [deep learning tutorial on lstm](http://deeplearning.net/tutorial/lstm.html)
* [Yoon Kim's CNN_sentence repo](https://github.com/yoonkim/CNN_sentence)
* [Ryan Kiros's skip-thoughts repo](https://github.com/ryankiros/skip-thoughts)

#### Licence
MIT
