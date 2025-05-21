## Transformer Models

![Base transformer encoder decoder layers](transformer.png)

### Positional Encoder
- This is how the model accounts for word order.
- Adds a positional encoding vector to each input embedding
- Positional encoding follows a fixed pattern, enabling the model to determine the position of each word and distance between them.

### Encoder
- The encoder consists of two main components. the Multi-Head Attention layer and the Feed Forward layer.
- The multi-head attention applies [[Self-Attention]] across all tokens in a layer allowing us to model context
- The Feed-forward layer allows the model to learn non-linear hierarchical features.
- Layer norms and residuals keep the network healthy during training

## Attention Mechanism 
Attention allows models to focus on specific parts of the input sequence, enhancing their ability to capture dependencies and relationships in data.

At a high-level **attention** refers to where the focus should be in training the network. **[[Self-Attention]]** refers to focusing on the same layer that is being trained in the network. **Multi-Head attention** refers to paying attention to multiple things at the same time.
- [Attention is All You Need](https://arxiv.org/abs/1706.03762) 
- [Attention Is Not All You Need Anymore](https://arxiv.org/abs/2308.07661)

## Unidirectional (Auto-Regressive) vs Bidirectional (Masked)
Unidirectional models (also known as Auto-regressive) predict the next word in the sequence. Bidirectional models guess a missing word in a sequence based on the sequence in both directions. 

## Selective State Models (SSMs)
- [Mamba Linear-Time Sequence Modelling with Selective State Spaces](https://arxiv.org/abs/2312.00752)  