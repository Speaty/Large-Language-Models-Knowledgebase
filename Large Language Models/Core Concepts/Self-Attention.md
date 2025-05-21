## How to calculate Self-attention
- Step 1: From the encoder's input vector (e.g. word embedding), create three trainable vectors:
	- Query: $Q$
	- Key: $K$
	- Value: $V$
- Step 2: Compute how much a word in position$_i$ should pay attention to a word in position$_j$ in a sentence, we take the **dot product** of the $Q_i$ with the $K_i$ 
$$
  \text{SelfAtt}(w_i,w_j) = Q_i\cdot K_i

$$
- Step 3: Divide all the scores by the square root of the dimension of the key vectors.
	- This is typically 8 as the vectors are typically of length 64
	- This is the default and seems to lead to more stable gradients
- Step 4: Apply a softmax to the scores
	- This results in them all being positive and summing to 1
	- Can be thought of as a probability "What proportion of my attention should I pay to word$_j$?"
- Step 5: For each word w$_i$, multiply the value vector ($V_j)$ of each other word w$_j$ by its softmax score with w$_i$ 
- Step 6: Sum to produce the output embedding (a this later for w$_i$) 
$$
Z_i = \sum_j{\text{softmax\_score}(w_i,w_j)\cdot V_j}
$$
