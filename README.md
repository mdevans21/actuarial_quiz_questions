# Actuarial Quiz Questions

A Jupyter notebook demonstrating actuarial concepts through two quiz questions covering exposure curves and stop loss pricing.

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install jupyter numpy scipy matplotlib
jupyter notebook actuarial_quiz.ipynb
```

---

## Q1: Integral of Exposure Curve

The exposure curve is defined as:
- For 0 ≤ x ≤ 1: Exposure(x) = x
- For 1 < x ≤ 2: Exposure(x) = 1 - (x - 1) = 2 - x

### Step 1: Plot the Exposure Curve

A triangular exposure curve peaking at x = 1.

### Step 2: Integrate Exposure(x) to get Incurred(x)

$$\text{Incurred}(x) = \int_0^x \text{Exposure}(t) \, dt$$

| x | Incurred(x) |
|---|-------------|
| 0 | 0.0000 |
| 1 | 0.5000 |
| 2 | 1.0000 |

### Step 3: Plot Exposure(x) and Incurred(x) Together

Combined line chart showing both the exposure curve and its cumulative integral.

---

## Q2: Stop Loss at Sigma Excess of Mean Plus Sigma

Normal distribution with:
- Mean (μ) = 60%
- Standard deviation (σ) = 6%

**Layer:** 66% xs 6% (attachment at μ + σ, width of σ)

### PDF Visualization

The probability density function is plotted with:
- Vertical lines at 66% (attachment) and 72% (exhaustion)
- Shaded region indicating the stop loss layer

### Step 1: Approximate Loss Cost (Trapezoidal Rule)

Average of 1 - CDF(x) at 66% and 72%, multiplied by layer width (6%).

```
1 - CDF(66%) = 15.9%
1 - CDF(72%) =  2.3%
Average survival probability = 9.1%

Approximate loss cost (trapezoidal) = 0.544%
```

### Step 2: Integrate 1 - CDF(x) between 66% and 72%

The expected loss to the layer computed as:

$$E[\text{Layer Loss}] = \int_{66\%}^{72\%} (1 - F(x)) \, dx$$

```
Integrated loss cost = 0.449%
```

### Step 3: Monte Carlo Simulation

Simulate x 10,000 times and calculate the average of min(max(0, x - 66%), 6%).

```
Simulated loss cost (n=10,000) = 0.452%
Standard error = 0.014%
```

### Step 4: Compare All Answers

```
======================================================
COMPARISON OF METHODS
======================================================
Method                             Loss Cost   % Diff
------------------------------------------------------
1. Trapezoidal Approximation          0.544%        -
2. Numerical Integration              0.449%   -17.5%
3. Monte Carlo Simulation             0.452%   -16.9%
======================================================
```

- The integration method is the most accurate.
- Trapezoidal rule provides a quick approximation.
- Simulation converges to the true value with more iterations.

### Step 5: Simulation Convergence

Demonstrates how the Monte Carlo simulation converges to the numerical integration result as the number of simulations increases (up to 100,000).

The convergence plot shows:
- **Blue line:** Simulation running average
- **Red dashed line:** Numerical integration result (true value)

```
Final simulation result (n=100,000): 0.448%
Numerical integration result:        0.449%
Difference:                          0.001%
```

---

## License

MIT
