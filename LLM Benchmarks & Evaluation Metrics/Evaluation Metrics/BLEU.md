[BLEU: A Method for Automatic Evaluation of Machine Translation](https://aclanthology.org/P02-1040.pdf)

Bi-Lingual Evaluation Understudy - machine translation benchmark 

Attempts to measure how close a machine generated (candidate) text is to a human one (reference) by comparing overlapping n-grams. Effectively, the more n-grams the candidate shares with the references, the higher its BLEU score. 

## Metrics
Uses n-gram precision with a brevity penalty.

1) **Calculate n-gram precision for different n-grams:**

Let $C$ represent the candidate text and $R$ the reference text. We denote $\text{Count}_{C}(x)$ as the number of occurrences of an n-gram $x$ in $C$, and $\text{Count}_{R}(x)$ as the number of occurrences in $R$.
$$

\text{Clipped Count}(x) = \min(\text{Count}_{C}(x), \text{Count}_{R}(x))

$$

$$


P_n = \frac{\sum_{x \in \text{n-grams}} \text{Clipped Count}(x)}{\sum_{x \in \text{n-grams of } C} \text{Count}_{C}(x)}


$$

2) **Calculate the Geometric Mean of Precisions:**
Just multiplying the precisions and taking the $n$-th root
 $$
P = \left( \prod_{i=1}^{n} P_i \right)^{\frac{1}{n}}
$$
3) **Apply the Brevity Penalty (BP):**
$$
BP = \begin{cases} 
      1 & \text{if } c > r \\
      e^{1 - \frac{r}{c}} & \text{if } c \leq r 
   \end{cases}
$$
4) **Combine:**
$$
\text{BLEU} = BP \times \exp \left( \sum_{i=1}^{n} w_i \, \log P_i \right)
$$
## Notes
A single low value of $p_n$ will significantly reduce the overall geometric mean. 