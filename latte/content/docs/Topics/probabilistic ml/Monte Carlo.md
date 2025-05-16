## 🏃‍♂️The Steps to Obtain Our Quantity of Interest
### Step 1 : Generate $S_n$ from the distribution $X_1, ...X_n$
 Various Methods: 
 1. Markov Chain Monto Carlo
 2. Binomial distribution
### Step 2: Given the Random Samples on $f(x_{s})$ we approximate the empirical distribution of $\{f(x_s)\}^n_1$
Monto Carlo approximation
- Developed in statistical physics during atomic bomb period
- Named after the plush gambling casino

The **expected values** are what typically asked

$$
\mathbb{E}[f(X)] = \int f(s) p(x)dx \approx \frac{1}{N}\sum^{N}_{s = 1}f(x_{s}), \text{ where } s \in N,  x_{s} \sim p(x)
$$
**aka. Monte Carlo Integration (canonical form)**

---

## 😜 The Advantage of Monto Carlo Over Numerical Integration 

 **Numerical integration** (like Simpson's Rule, Trapezoidal Rule, or grid-based methods) evaluates the function f(x) at **uniform intervals** across the entire domain—even in regions where the function contributes **very little or nothing** to the integral (e.g., $p(x) \approx 0$)
 
- In contrast, **Monte Carlo integration** samples values of x **according to the probability distribution p(x)**. This ensures that:
    - Most samples fall in **high-probability regions**
**Note**:
- In short, Monte Carlo is simply just an expected value calculation on top of random function $f\left( \cdot \right)$ sample

> [! hint] It was never the formula that made Monto Carlo unique, but from the **analytical standpoint**; it is a useful perspective to estimate $f(x)$ based on important *weights*; and it **fits well on high dimension space** 

---
## 📘Example
### $\Delta$ Example 1.  Change of Variables, the MC way

$$y = f(x)$$
$$x \sim \text{Uni(-1,1)}, y = x^2$$
Approximate p(y) by drawing many samples from $p(x)$ and create distribution


> insert mcapproximated code simulation

Figure 2.19 Estimating π by Monte Carlo integration. Blue points are inside the circle, red crosses are outside.

### 🎤 Example 2. Estimating $\pi$ by Monte Carlo Integration
**Function definition**:
$$f(x,y) = \begin{cases}
1 & (x^2 + y^2 \leq r^2) \\
0 & \text{otherwise}
\end{cases}
$$
We know that $\pi = A / r^2$. Here we define the raw **Area Integral of Circle** as
$$
 A = \int^{r}_{-r} \int^{r}_{-r} \mathbb{I}(x^2 +y^2 \leq r^2) \,dx\,dy
$$
- $\mathbb{I}()$ is an indicator function that is going to evaluate 1 or 0 based on the condition
Now, let $p(x)$ and $p(y)$ be defined as part of the uniform distribution on $[-r, r]$ range. Therefore probabilities are as $p(x) = p(y) =\frac{1}{2r}$

**The Monte Carlo Integral**
$$
A = (2r)(2r) \iint f(x, y) \cdot p(x) \cdot p(y)\, dx\, dy \\
\approx 4r^2 \cdot \frac{1}{S} \sum_{s=1}^S f(x_s, y_s)
$$

**Note:**
- The $4r^2$ factor scales back up after uniform sampling over $[-r, r]^2$, whose joint density is $p(x)p(y) = \frac{1}{4r^2}$.
- Since uniform sampling gives us $\mathbb{E}[f(x, y)] = \frac{1}{4r^2} \iint f(x, y)\, dx\, dy$, we multiply by $4r^2$ to recover the original integral.


### 🎯Example 3. Accuracy of Monte Carlo

Relatinship of Normail Distrbution to Monte Carlo

$$(\hat{\mu} - \mu) \rightarrow \mathcal{N}(0, \frac{\sigma^2}{S})$$
where 

**Variance** is defined as
$$\sigma^2 = \mathbb{E}[f(X)^2] -\mathbb{E}[f(X)]^2 \Leftrightarrow \frac{1}{S}\sum^S_{1}(f(x_{s} - \hat{\mu}))^2$$

**Confidence** Interval is defined as

$$
P\left\{ \mu - 1.96 \cdot \frac{\hat{\sigma}}{\sqrt{S}} 
\leq \hat{\mu} \leq 
\mu + 1.96 \cdot \frac{\hat{\sigma}}{\sqrt{S}} \right\} \approx 0.95
$$
















---
## Reference
[1] K. P. Murphy, *Probabilistic Machine Learning: An Introduction*, MIT Press, 2023.
	- ch 2.7


