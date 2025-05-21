
## Low-Rank Adaptation (LoRA)
Original Paper: [LoRA: Low-Rank Adaptation of Large Language Models](https://arxiv.org/abs/2106.09685)

LLMs have *huge* weight matrices, especially in attention layers. Fine-tuning them directly means updating **billions of parameters**, which is expensive and memory-intensive. LoRA solves this by:
- **Freezing** the original model weights
- Adding **small trainable low-rank matrices** (typically rank 4-8) to specific layers (often the attention weights)
- During training, only the **low-rank matrices are updated,** not the full model.
instead of directly updating a weight matrix `W` (say in attention), LoRA rewrites it like:
$$
W' = W + \Delta W 
$$
$$
\Delta W = A @ B
$$
Where:
- $W$ is the original frozen matrix
- $A$ and $B$ are small **learnable** matrices with shapes that make $A@B$ a low-rank approximation
- Only $A$ and $B$ are trained

**Rank** refers to the dimensionality of the low-rank matrices (A and B)