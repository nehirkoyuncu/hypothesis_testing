### Hypothesis Test Overview

This project investigates whether more goals are scored in **women’s FIFA World Cup matches** than in **men’s FIFA World Cup matches** since **January 1st, 2002**. The analysis focuses exclusively on **official FIFA World Cup games**, excluding qualifiers and friendly matches.

All matches are assumed to be **independent events**, meaning that factors such as team form, injuries, or tournament stage are not considered.

---

### Research Question

**Are more goals scored in women’s international soccer matches than in men’s?**

---

### Hypotheses

* **Null Hypothesis (H₀):**
  The mean number of goals scored in women’s World Cup matches is **the same** as in men’s matches.
  

* **Alternative Hypothesis (H₁):**
  The mean number of goals scored in women’s World Cup matches is **greater** than in men’s matches.
 

This is a **one-tailed** test, as we are specifically testing whether women’s matches produce **more** goals on average.

---

### Data Sources

Two CSV files are used:

* `women_results.csv` — containing all official women’s international match results.
* `men_results.csv` — containing all official men’s international match results.

From each file, only matches played **on or after 2002-01-01** and belonging to **FIFA World Cups** are included.

For every match, the **total number of goals** is calculated as:
`total_goals = home_score + away_score`

---

### Statistical Method

To compare the mean goals scored in women’s and men’s matches, an **independent two-sample t-test (Welch’s t-test)** is used.
Welch’s t-test is preferred because it does not assume equal variances between the two groups, which is suitable for real-world sports data.

The test produces a **p-value** indicating how likely it is to observe the data assuming the null hypothesis is true.

---

### Decision Rule

* **Significance level (α):** 0.10 (10%)
* **Decision criteria:**

  * If `p_val < 0.10`, we **reject** the null hypothesis.
  * If `p_val ≥ 0.10`, we **fail to reject** the null hypothesis.

---

### Result Format

The outcome of the test is stored in a Python dictionary named `result_dict` as follows:

```
result_dict = {"p_val": p_val, "result": result}
```

Where:

* `p_val` → the p-value obtained from the t-test
* `result` → either `"reject"` or `"fail to reject"`, depending on the test outcome

---

### Interpretation

If the null hypothesis is rejected, it provides statistical evidence (at the 10% significance level) that **women’s FIFA World Cup matches feature more goals on average than men’s**.
If it is not rejected, the analysis concludes that **there is no significant difference** between the average number of goals scored in women’s and men’s matches.
