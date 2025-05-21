Original Paper: [Deep Contextualised Word Representations](https://aclanthology.org/N18-1202/)

![ELMo base model](static/img/ELMo-base-model.png)

- Two [[LSTM]]s are applied to the sequence of embeddings, one making a forward pass and another a backwards pass. 
- The forward and backwards probabilities are combined using a [[softmax]] function.  
- Where the first layer had the context of the word embeddings either side of the target word, the second layer takes in context an additional word in either direction.