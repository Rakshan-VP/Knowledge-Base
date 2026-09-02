#type #domain #status #scope
> [!abstract] Summary 
> One or two sentences explaining the main idea.
## Introduction
The Gaussian distribution, or **bell curve**, describes data that naturally bunches up around an average with rare extremes. **Abraham de Moivre** discovered it in **1733** while calculating odds for coin-flip gambling games. Later in **1809**, **Carl Friedrich Gauss** used it to solve a major astronomy problem: tracking planets when telescope measurements were constantly noisy and imprecise. Whenever you measure something in the real world, tiny random errors—like shaking hands, wind, or blurry optics—naturally push your readings slightly off target. Gauss invented this formula to prove that taking the average of all those noisy measurements gives you the closest guess to the real truth.

## Concept
The **Gaussian distribution**, also called the **normal distribution**, is a continuous probability distribution commonly used to model random variables that tend to cluster around a central value.

![[GaussianDistribution.png|798]]

### Expression

The Gaussian distribution is described by the Gaussian probability density function (PDF) as follows :

$$
\boxed{
p(x) =
\frac{1}{\sqrt{2\pi\sigma^2}}
\exp\left(
-\frac{(x-\mu)^2}{2\sigma^2}
\right)}
$$

### Notation

$$
\boxed{X \sim \mathcal{N}(\mu,\sigma^2)}
$$

where:

- $X$ — random variable
- $\sim$ — is distributed as
- $\mathcal{N}$ — notation for Gaussian Distribution
- $\mu$ — mean
- $\sigma^2$ — variance
- $\sigma$ — standard deviation
### Parameters
- **Mean ($\mu$)** : Determines the **center** of the distribution.
	- Increasing $\mu$ → curve shifts to the right
	- Decreasing $\mu$ → curve shifts to the left
	- The peak occurs at $x=\mu$

- **Standard Deviation ($\sigma$)** : Determines the **spread** of the distribution.
	- Larger $\sigma$ → wider and shorter curve
	- Smaller $\sigma$ → narrower and taller curve
	- $\sigma^2$ represents the variance
### Properties
- **Symmetric:** The curve is symmetric about $\mu$.
- **Mean = Median = Mode:** All occur at $\mu$.
- **Total area = 1:**

$$
\int_{-\infty}^{\infty}p(x)\,dx = 1
$$

- **Probability is area:** The probability of a range is the area under the curve.

$$
P(a \leq X \leq b)
=
\int_a^b p(x)\,dx
$$

- **Asymptotic:** The curve approaches the $x$-axis as $x\rightarrow\pm\infty$ but never reaches it.
- **Bell-shaped:** The maximum density occurs at the mean.
- **Unimodal:** It has one peak.
### 68–95–99.7 Rule

For a Gaussian distribution:

- **≈ 68%** of values lie within $\mu \pm 1\sigma$
- **≈ 95%** lie within $\mu \pm 2\sigma$
- **≈ 99.7%** lie within $\mu \pm 3\sigma$

$$
P(\mu-\sigma \leq X \leq \mu+\sigma) \approx 68\%
$$

$$
P(\mu-2\sigma \leq X \leq \mu+2\sigma) \approx 95\%
$$

$$
P(\mu-3\sigma \leq X \leq \mu+3\sigma) \approx 99.7\%
$$

### Interpretation
- Values near $\mu$ are more likely than values far from $\mu$.
- The distance from the mean is measured in units of standard deviation.
- A value of $\mu + 2\sigma$ is two standard deviations above the mean.
- The PDF gives **probability density**, not the probability of an exact value.
### Advantages
- Simple mathematical form.
- Characterized by only two parameters: $\mu$ and $\sigma^2$.
- Symmetry makes it easy to analyze.
- Widely used in statistics, estimation, signal processing, and control.
### Limitations
- Assumes the data follows a bell-shaped symmetric distribution.
- Cannot accurately represent **strongly skewed** or **heavy-tailed data**.
- Real-world data may not be well modeled by a Gaussian distribution.
- The **68–95–99.7** rule applies specifically to Gaussian distributions.

## Related

- [[Related Note 1]]
- [[Related Note 2]]

## References

- [Wikipedia - Normal Distribution](https://en.wikipedia.org/wiki/Normal_distribution)
- [GeeksforGeeks - Normal Distribution](https://www.geeksforgeeks.org/maths/normal-distribution/)