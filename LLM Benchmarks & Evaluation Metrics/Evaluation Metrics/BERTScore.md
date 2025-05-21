Original Paper: [BERTScore: Evaluating Text Generation with BERT](https://arxiv.org/abs/1904.09675)

Measures the pairwise cosign similarity of BERT embeddings, optionally it includes importance weightings calculated by TF-IDF

$$
\text{Precision} = \frac{1}{m} \sum_{i=1}^{m} \max_{j} \text{cos\_sim}(c_i, r_j)
$$

$$
\text{Recall} = \frac{1}{n} \sum_{j=1}^{n} \max_{i} \text{cos\_sim}(r_j, c_i)
$$
$$
\text{BERTScore} = F_1 = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}
$$
