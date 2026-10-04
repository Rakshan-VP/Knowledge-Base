#type/concept #domain/math #status/learning #scope/fundamental
> [!abstract] Summary 
> One or two sentences explaining the main idea.

## Expected Value ($\mathbb{E}[X]$)
### Definition

The **expected value** of a random variable $X$, denoted $\mathbb{E}[X]$, represents its probability-weighted average across all possible outcomes.

* **Discrete Random Variable:** If $X$ takes countable distinct values $x_i$ with probabilities $P(X = x_i)$:
$$
\mathbb{E}[X] = \sum_{i} x_i P(X = x_i)
$$

* **Continuous Random Variable:** If $X$ is defined continuously with probability density function (PDF) $f(x)$:
$$
\mathbb{E}[X] = \int_{-\infty}^{\infty} x f(x) \, dx 
$$

* **Existence Condition:** The expectation exists if and only if it is absolutely convergent, satisfying $\mathbb{E}[|X|] < \infty$.

### Properties
- **Linearity** (holds regardless of independence): $\mathbb{E}[aX + bY] = a\mathbb{E}[X] + b\mathbb{E}[Y]$
- **Constants**: $\mathbb{E}[c] = c \quad (\text{for constant } c \in \mathbb{R})$ 
- **Product Rule** (requires $X, Y$ to be independent): $\mathbb{E}[XY] = \mathbb{E}[X] \cdot \mathbb{E}[Y]$


> [!EXAMPLE] Rolling a Fair Die
> Let $X$ be the result of a 6-sided die roll, where each outcome has probability $P(X = x) = \frac{1}{6}$:
> 
> $$
> \mathbb{E}[X] = \sum_{x=1}^{6} x \left(\frac{1}{6}\right) = \frac{1 + 2 + 3 + 4 + 5 + 6}{6} = 3.5
> $$

## Mean ($\mu$ / $\bar{x}$)
### Definition

The **mean** is the center value of a dataset. It is calculated by summing all values and dividing by the total count, giving a baseline number that represents the entire group.

* **Sample Mean ($\bar{x}$):** The average of $n$ observed data points in a sample:
$$
\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_i 
$$

* **Population Mean ($\mu$):** The average of all $N$ values in an entire population:
$$
\mu = \frac{1}{N} \sum_{i=1}^{N} x_i
$$

* **Equivalence to Expectation:** For a probability distribution, the population mean equals the expected value: $\mu = \mathbb{E}[X]$.

### Properties
- **Zero Deviation Sum:** The sum of deviations of all values from their mean is always zero: $\sum (x_i - \bar{x}) = 0$
- **Sensitivity to Outliers:** Extreme values pull the mean toward them, altering its value significantly
- **Linear Scaling:** If each value is transformed by $y_i = a x_i + b$, the new mean is $\bar{y} = a\bar{x} + b$

> [!EXAMPLE] Exam Scores
> Given the scores of 5 students: $70, 80, 85, 90, 100$ ($n = 5$):
> 
> $$
> \bar{x} = \frac{70 + 80 + 85 + 90 + 100}{5} = \frac{425}{5} = 85
> $$

## Median
### Definition

The **median** is the middle value in a sorted dataset. It splits the ordered numbers into two equal halves, so that 50% of the values fall below it and 50% fall above it.

* **Odd Number of Values ($n$ is odd):** The median is the exact single value sitting at position $\frac{n+1}{2}$:
  $$\text{Median} = x_{\left(\frac{n+1}{2}\right)}$$

* **Even Number of Values ($n$ is even):** The median is the average of the two central values at positions $\frac{n}{2}$ and $\frac{n}{2} + 1$:
  $$\text{Median} = \frac{x_{\left(\frac{n}{2}\right)} + x_{\left(\frac{n}{2} + 1\right)}}{2}$$

* **Continuous Distribution:** For a continuous random variable with cumulative distribution function (CDF) $F(x)$, the median $m$ solves:
  $$F(m) = P(X \le m) = 0.5$$

### Properties
- **Robustness to Outliers:** Unlike the mean, extreme high or low values do not distort the median
- **Invariance under Monotonic Shifts:** Applying an order-preserving transformation strictly preserves relative rank
- **Minimizes Absolute Deviation:** The median minimizes the sum of absolute errors: $\sum |x_i - c|$ is minimized when $c = \text{Median}$

> [!EXAMPLE] Finding the Center
> Dataset of 5 numbers (sorted): $3, 7, \mathbf{9}, 12, 40$
> 
> Since $n = 5$ (odd), the median is the 3rd number:
> $$\text{Median} = 9$$
> **Even if $40$ was replaced by $1000$, the median stays $9$.**

## Mode
### Definition

The **mode** is the value that occurs most frequently in a dataset. It represents the most common or most frequently observed value.

* **Discrete Dataset:** If a value $x$ occurs more frequently than any other value, then:
  $$\text{Mode} = x$$

* **Multiple Modes:** If two or more values have the same highest frequency, the dataset is **multimodal**, and all such values are modes.

* **Continuous Distribution:** For a continuous random variable with probability density function (PDF) $f(x)$, the mode is the value $m$ at which the density is maximum:
  $$f(m) = \max_x f(x)$$

### Properties
- **Represents the Most Common Value:** The mode identifies the value with the highest frequency
- **Works with Categorical Data:** Unlike the mean and median, the mode can be used for non-numerical categories
- **Not Necessarily Unique:** A dataset can have one mode, multiple modes, or no unique mode
- **Unaffected by Extreme Values:** Changing values that are not modes does not affect the mode
- **Depends on Frequency:** The mode is determined by how often values occur, not by their magnitude

> [!EXAMPLE] Finding the Most Common Value
> Dataset: $2, 3, 3, 5, 7, 3, 9$
>
> The value $3$ occurs **three times**, which is more frequent than any other value:
> $$\text{Mode} = 3$$
>
> **Even if $9$ was replaced by $1000$, the mode would remain $3$.**

## Variance & Standard Deviation
### Definition

**Variance** and **standard deviation** both measure how much the values in a dataset **spread out from their mean**.

Variance is the **average of the squared deviations** from the mean, while standard deviation is the **square root of the variance**.

* **Population Variance:** When the dataset contains all the values of interest:
  $$
  \sigma^2 = \frac{1}{N}\sum_{i=1}^{N}(x_i-\mu)^2
  $$

* **Sample Variance:** When the dataset is a sample from a larger population:
  $$
  s^2 = \frac{1}{n-1}\sum_{i=1}^{n}(x_i-\bar{x})^2
  $$

* **Random Variable:** For a random variable $X$ with mean $\mu=\mathbb{E}[X]$, the variance is:
  $$
  \operatorname{Var}(X)=\mathbb{E}\left[(X-\mu)^2\right]
  $$

  An equivalent and useful form is:
  $$
  \boxed{\operatorname{Var}(X)=\mathbb{E}[X^2]-\left(\mathbb{E}[X]\right)^2}
  $$

  This means:
  $$\text{Variance}=\text{expected value of }X^2-(\text{expected value of }X)^2$$

* **Standard Deviation:** The standard deviation is the square root of the variance:
  $$
  \sigma=\sqrt{\operatorname{Var}(X)}
  $$

### Properties
- **Measures Spread:** Larger variance or standard deviation means the values are more spread out from the mean
- **Always Non-Negative:** Both variance and standard deviation are always $\geq 0$
- **Zero Spread:** Both are $0$ when all values are identical
- **Sensitive to Outliers:** Extreme values can significantly increase both measures
- **Units:** Variance has squared units, while standard deviation has the same units as the original data
- **Adding a Constant:** Adding the same constant to every value does not change the variance or standard deviation:
  $$\operatorname{Var}(X+c)=\operatorname{Var}(X)$$
- **Scaling:** Multiplying every value by a constant $a$ multiplies the variance by $a^2$ and the standard deviation by $|a|$:
  $$\operatorname{Var}(aX)=a^2\operatorname{Var}(X)$$
  $$\operatorname{SD}(aX)=|a|\operatorname{SD}(X)$$

> [!EXAMPLE] Measuring the Spread
> Dataset: $2, 4, 6$
>
> First, calculate the mean:
> $$\bar{x}=\frac{2+4+6}{3}=4$$
>
> Calculate the squared deviations:
> $$(-2)^2=4,\qquad(4-4)^2=0,\qquad(6-4)^2=4$$
>
> Therefore, the **population variance** is:
> $$\sigma^2=\frac{4+0+4}{3}=\frac{8}{3}$$
>
> The **population standard deviation** is:
> $$\sigma=\sqrt{\frac{8}{3}}\approx1.63$$
>
> Therefore:
> $$\boxed{\text{Variance}=\frac{8}{3},\qquad\text{Standard Deviation}\approx1.63}$$
>
> **Variance** measures the squared spread, while **standard deviation** measures the spread in the same units as the original data.
## Related

- [[Related Note 1]]
- [[Related Note 2]]

## References

- www.google.com