A **random variable** is a way to represent outcomes of a random process numerically. There are two main types:
1) **Discrete random variables** e.g. rolling a dice
2) **Continuous random variables** e.g. where outcomes can take any real value in a range

# Probability Distribution
A **probability distribution** describes how likely each outcome of a random variable is.

For a **continuous random variable**, the probability is described using a curve, like the [[Gaussian distribution]] (Normal distribution).

**Key Property:** The sum (or total area) of all probabilities is always **1**. 

# Expectation (Mean)
The **expectation** (or expected value) of a random variable is a measure of its "average" outcome over many trials. This is like the centre of gravity of the probability distribution.

**For Discrete Random Variables:**
If $X$ is a discrete random variable with possible values $x_1, x_2, ...,x_n$ and their probabilities are $P(X=x_i)$, then the expectation is calculated as:
$$
\mathbb{E}[X] = \sum_{i=1}^n x_i \cdot P(X=x_i)
$$
**Example: Rolling a fair die**
- Possible Outcomes: $X = \set{1,2,3,4,5,6}$ 
- Probabilities: $P(X=x) = \frac{1}{6} \text{ for each } x$
- Expectation:
$$
\mathbb{E}[X] = 1 \cdot \frac{1}{6} +  2 \cdot \frac{1}{6} + \cdot\cdot\cdot + 6 \cdot \frac{1}{6} = \frac{1 + 2 + 3 + 4 + 5 + 6}{6} = 3.5 
$$



**For Continuous Random Variables**
For continuous variables an integral is used instead of a sum. If $X$ has a probability density function $f(x)$ the expectation is:
$$
\mathbb{E}[X]=\int_{-\infty}^\infty x \cdot f(x)dx
$$

# Variance and Standard Deviation
To understand Gaussians, you need a feel for **spread** - how much the outcomes deviate from the mean.
- **Variance** ($Var(X)$): Measures the average squared deviation from the mean:
$$
Var(X) = \mathbb{E}[(X - \mathbb{E}[X])^2]
$$
- **Standard Deviation** ($\sigma$): The square root of the variance, giving the spread in the same units as $X$.
For the fair die example:
- Mean: $\mathbb{E}[X] = 3.5$
- Variance: $Var(X) = \mathbb{E}[(X-3.5)^2]$
- Standard Deviation: $\sigma = \sqrt{Var(X)}$

