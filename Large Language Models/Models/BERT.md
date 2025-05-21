# Bi-directional Encoder Representations from Transformers
Original Paper: [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805)

- Each token in BERT is a sum of three embeddings:
	- Token level embedding (e.g. E$_{\text{my}}$, E$_{\text{dog}}$,...)
	- Segment embedding - divides segments denoted by the special E$_{\text{[SEP]}}$ token
	- Position - absolute position in the sequence
- 30,000 WordPiece vocabulary -> morphology -> better representations for rare words
- Sentences are separated by a special "SEP" token
- A special "CLS" token is added at the beginning of the chunk.

BERT is a Masked Language Model.

## Pre-training
- **Data:** 
  Wikipedia (2.5b words) + BookCorpus (800m words)
- **Batch Size:** 
  131,072 words (1024 sequences * 128 length or 256 sequences * 512 length)
- **Training Time:** 
  1m steps (~40 epochs)
- **Optimiser:** 
  AdamW, 1e-4 learning rate, linear decay
  
- *BERT-Base*: 12-layer, 768-hidden, 12-head
- *BERT-Large*: 24-layer, 1024-hidden, 16-head

## Fine-tuning