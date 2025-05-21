When an LLM is generating text, it outputs a **probability distribution over the vocabulary** at each step. The decoding strategy is used to select the next token. 

- **Greedy Decoding:** Just take the most probable token
- **Sampling:** Randomly sample from the probability distribution
- **Beam Search:** Keep track of the top `k` partial sequences as you go and select the best one at the end