# Natural Language to SQL

This repo provides an implementation of our neural networks for predicting SQL queries on [WikiSQL dataset](https://github.com/salesforce/WikiSQL). Our paper is available at [here](https://arxiv.org/abs/1801.00076).

## Citation

> Tong Guo, Huilin Gao. 2018. Bidirectional Attention for SQL Generation.

## Bibtex

```
@article{guo2018bidirectional,
  title={Bidirectional Attention for SQL Generation},
  author={Guo, Tong and Gao, Huilin},
  journal={arXiv preprint arXiv:1801.00076},
  year={2018}
}
```

## Installation
The data is in `data.tar.bz2`. Unzip the code by running
```bash
tar -xjvf data.tar.bz2
```

The code is written using PyTorch in Python 2.7. Check [here](http://pytorch.org/) to install PyTorch. You can install other dependency by running 
```bash
pip install -r requirements.txt
```

## Downloading the glove embedding.
Download the pretrained glove embedding from [here](https://github.com/stanfordnlp/GloVe) using
```bash
bash download_glove.sh
```

## Extract the glove embedding for training.
Run the following command to process the pretrained glove embedding for training the word embedding:
```bash
python extract_vocab.py
```

## Train
The training script is `train.py`. To see the detailed parameters for running:
```bash
python train.py -h
```

Some typical usage are listed as below:

Train a model with bi-attention:
```bash
python train.py --ca
```

Train a model with column attention and trainable embedding (requires pretraining without training embedding, i.e., executing the command above):
```bash
python train.py --ca --train_emb
```

## Test
The script for evaluation on the dev split and test split. The parameters for evaluation is roughly the same as the one used for training. For example, the commands for evaluating the models from above commands are:

Test a trained model with column attention
```bash
python test.py --ca
```

Test a trained model with column attention and trainable embedding:
```bash
python test.py --ca --train_emb
```

## Reference

https://github.com/xiaojunxu/SQLNet
