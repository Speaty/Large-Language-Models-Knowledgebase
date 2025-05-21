Original Paper: [METEOR: An Automatic Metric for MT Evaluation with Improved Correlation with Human Judgements](https://aclanthology.org/W05-0909/)
[Wikipedia](https://en.wikipedia.org/wiki/METEOR)

Based on harmonic mean of unigram precision and recall, with recall weighted higher than precision. Designed to fix some problems with BLEU not accounting for recall.

1) **Preprocessing**
   lowercase, remove punctuation, tokenize

2) **Match Words**
   $$ 
M_{\text{exact}} = \{ w \in H \mid w \in R \}
$$
$$
M_{\text{stem}} = \{ w \in H \mid \text{stem}(w) \in \text{stem}(R) \}
$$
$$
M_{\text{syn}} = \{ w \in H \mid \text{synonyms}(w) \cap R \neq \emptyset \}
$$

3) **Compute Precision and Recall**
$$
P = \frac{|M|}{|H|}
$$
$$
R = \frac{|M|}{|R|}
$$
4) **Compute F-mean Score**
   $$
   F_{mean} = \frac{10PR}{R+9P}
   $$
5) **Compute Fragmentation Penalty**
   chunks are unbroken runs of unigrams matched. *Why is the fraction cubed?*
   $$
   Penalty = 0.5* \bigg(\frac{\text{\#chunks}}{\text{\#unigrams matched}}\bigg)^3
   $$
6) **Compute METEOR Score**
$$
\text{METEOR} = F_{mean}.(1-Penalty)
$$



