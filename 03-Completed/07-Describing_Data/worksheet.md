# 📝 Worksheet: 07 - Describing Data

Use this worksheet to reinforce the descriptive workflow: what each column means, what's typical, how much it varies, what's unusual, how groups differ, and which columns move together. Each section ends with an **🤖 Explain It** prompt. Write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🏷️ Section 1: Types of Data

1. Classify each as nominal, ordinal, interval, or ratio: `zip code`, `t-shirt size (S/M/L/XL)`, `year of birth`, `monthly rent`.<br>
   `Answer:` See the completed answer below.

<!-- response answer-1 -->
**Answer:** Zip code: nominal (identifier); t-shirt size: ordinal; year of birth: interval; monthly rent: ratio.
<!-- end response answer-1 -->

2. A column has dtype `int64` and only 4 distinct values. Name two things it might really be, and how you'd decide.<br>
   `Answer:` See the completed answer below.

<!-- response answer-2 -->
**Answer:** It might be a category code (for example four ranked levels) or a genuine discrete count (for example 0-3 children). Consult its definition and actual values: do the codes merely label/rank groups, or do differences and ratios measure a real quantity? Dtype and cardinality alone do not decide.
<!-- end response answer-2 -->

---

### ✏️ Task: Record the Meaning

```python
# Using titanic.csv:
# 1. Convert Embarked to 'category' and map C/Q/S to 'Cherbourg'/'Queenstown'/'Southampton'.
# 2. Create an ordered 'class' column (3rd < 2nd < 1st).
# 3. Print the share of passengers above 3rd class, using a comparison on 'class'.
```

<!-- response task-1 -->
**Completed task:** [Executable code and saved outputs](Worksheet-Support/worksheet_calculations.ipynb) (task 1). `Embarked` is categorical with full port names; `class` is ordered `3rd < 2nd < 1st`. There are **400 / 891 = 44.8934%** passengers above 3rd class. Both missing embarkation ports remain missing; all classes are known. [Result](Worksheet-OutputFiles/meaning_summary.csv).
<!-- end response task-1 -->

### 🤖 Explain It

In your own words: why does it matter whether a variable is nominal or ordinal before you compute anything with it? What could go wrong if you averaged an ordinal column's codes?

<!-- response reflection-1 -->
**Pending learner response:** Write this explanation in your own words. No learner reflection or participation claim has been supplied.
<!-- end response reflection-1 -->

---

## 🎯 Section 2: Center and Spread

3. Why is the median usually reported for house prices instead of the mean?<br>
   `Answer:` See the completed answer below.

<!-- response answer-3 -->
**Answer:** House prices are commonly right-skewed: a few extremely expensive homes pull up the mean. The median better describes a typical sale and resists extreme values.
<!-- end response answer-3 -->

4. You compute a standard deviation with pandas and get 14.53, and a classmate uses NumPy and gets 14.52. Who's wrong?<br>
   `Answer:` See the completed answer below.

<!-- response answer-4 -->
**Answer:** Neither is necessarily wrong. Pandas defaults to sample standard deviation (`ddof=1`, denominator n-1); NumPy defaults to population standard deviation (`ddof=0`, denominator n). On identical non-missing data, matching `ddof` makes them agree apart from rounding. Also check that they handled missing values the same way.
<!-- end response answer-4 -->

---

### ✏️ Task: Compare Center and Spread

```python
# Using pokemon.csv:
# For Attack, print the mean, median, std, and IQR.
# Then do the same for Legendary Pokémon only.
# Which group is more spread out, by std and by IQR? Do the two measures agree?
```

<!-- response task-2 -->
**Completed task:** Support notebook task 2, using sample std (`ddof=1`) and IQR = Q3 - Q1.

| Group | n | Mean Attack | Median | Std | IQR |
|---|---:|---:|---:|---:|---:|
| All Pokemon | 800 | 79.0013 | 75 | 32.4574 | 45 |
| Legendary only | 65 | 116.6769 | 110 | 30.3480 | 31 |

The overall group is more spread out by both std and IQR, so the two measures agree. "All" includes Legendary Pokemon; it is not the non-Legendary subset. [Full precision results](Worksheet-OutputFiles/attack_center_spread.csv).
<!-- end response task-2 -->

### 🤖 Explain It

In your own words: two classes have the same average exam score, but very different standard deviations. Describe what being a student in each class might be like.

<!-- response reflection-2 -->
**Pending learner response:** Write this explanation in your own words. No learner reflection or participation claim has been supplied.
<!-- end response reflection-2 -->

---

## 📐 Section 3: Shape and Outliers

5. A column has mean 50, median 38, and `.skew()` of 2.1. Describe its shape.<br>
   `Answer:` See the completed answer below.

<!-- response answer-5 -->
**Answer:** The distribution is positively/right-skewed, with a long upper tail. The mean exceeding the median and positive skew of 2.1 are consistent with relatively large values pulling the mean upward.
<!-- end response answer-5 -->

6. Name one situation where you **should** remove an outlier, and one where you shouldn't.<br>
   `Answer:` See the completed answer below.

<!-- response answer-6 -->
**Answer:** Remove or correct a verified data-entry error such as an impossible negative age, after checking the source. Keep a valid unusually high Titanic fare when studying all passenger fares; flag it and use robust summaries or a suitable transformation instead of deleting it just for being extreme.
<!-- end response answer-6 -->

---

### ✏️ Task: Outlier Report

```python
# Using penguins.csv (drop the 2 rows with no measurements first):
# 1. Write or copy iqr_fences(series, k=1.5).
# 2. Count outliers in body_mass_g overall, then within each species.
# 3. Print the flagged rows. Are any of them impossible values?
```

<!-- response task-3 -->
**Completed task:** Support notebook task 3 implements `iqr_fences(series, k=1.5)` and drops exactly the two rows lacking all measurements, leaving **342** penguins. Rows with only missing sex are retained.

| Scope | n | Lower fence (g) | Upper fence (g) | Flags |
|---|---:|---:|---:|---:|
| Overall | 342 | 1750 | 6550 | 0 |
| Adelie | 151 | 2375 | 4975 | 0 |
| Chinstrap | 68 | 2793.75 | 4643.75 | 2 |
| Gentoo | 123 | 3500 | 6700 | 0 |

The printed flagged rows are Chinstrap on Dream island: original zero-based row 189 (male, 4800 g, bill 52.0 x 20.7 mm, flipper 210 mm) and row 190 (female, 2700 g, bill 46.9 x 16.6 mm, flipper 192 mm). Neither mass is intrinsically impossible; these are unusual relative to their species, not proven errors. Retain them unless source investigation establishes a problem. [Summary](Worksheet-OutputFiles/penguin_outlier_summary.csv), [complete flagged rows](Worksheet-OutputFiles/penguin_flagged_rows.csv).
<!-- end response task-3 -->

### 🤖 Explain It

In your own words: explain to a classmate why "outlier" and "error" aren't the same thing, using an example from the Titanic fares.

<!-- response reflection-3 -->
**Pending learner response:** Write this explanation in your own words. No learner reflection or participation claim has been supplied.
<!-- end response reflection-3 -->

---

## 👥 Section 4: Comparing Groups

7. When should you compare groups with counts, and when with rates?<br>
   `Answer:` See the completed answer below.

<!-- response answer-7 -->
**Answer:** Use counts for absolute workload or totals, such as how many passengers survived. Use rates to compare outcomes relative to unequal group sizes, such as survivors divided by passengers within each class. Always show the denominator and missing-data exclusions.
<!-- end response answer-7 -->

8. What's the difference between `normalize='index'` and `normalize='columns'` in `pd.crosstab()`? Write a question each one answers.<br>
   `Answer:` See the completed answer below.

<!-- response answer-8 -->
**Answer:** `normalize='index'` divides by each row total; `normalize='columns'` divides by each column total. For `pd.crosstab(titanic['class'], titanic['Sex'])`, row normalization answers "Within each class, what proportion is female?" Column normalization answers "Among women, what proportion traveled in each class?"
<!-- end response answer-8 -->

---

### ✏️ Task: Survival Table

```python
# Using titanic.csv:
# 1. Bin Age into child (0-12), teen (13-18), adult (19-60), senior (61+) with pd.cut().
# 2. Build a pivot_table of survival rate with age group as rows and Sex as columns.
# 3. Add the group sizes (a second pivot_table with aggfunc='size').
# Which cell has the highest rate? Is its group big enough to trust?
```

<!-- response task-4 -->
**Completed task:** Support notebook task 4 uses `pd.cut` with `[0, 12, 18, 60, infinity]`, `include_lowest=True`, and right-closed intervals: child `[0,12]`, teen `(12,18]`, adult `(18,60]`, senior `(60,infinity)`. The integer descriptions in the prompt are interpreted as continuous-age cutoffs so fractional ages have no gaps. The 177 missing ages are excluded, leaving **714** passengers.

| Age group | Female survival | Female n | Male survival | Male n |
|---|---:|---:|---:|---:|
| Child | 59.375% | 32 | 56.757% | 37 |
| Teen | 75.000% | 36 | 8.824% | 34 |
| Adult | 77.895% | 190 | 18.457% | 363 |
| Senior | 100.000% | 3 | 10.526% | 19 |

Senior women have the highest observed rate, **3/3 = 100%**, but only three observations make it too fragile for dependable generalization. [Rate pivot](Worksheet-OutputFiles/age_sex_survival_rates.csv), [size pivot](Worksheet-OutputFiles/age_sex_group_sizes.csv).
<!-- end response task-4 -->

### 🤖 Explain It

In your own words: what's a confounder? Describe one in the Titanic data, and how you'd check for it with a table.

<!-- response reflection-4 -->
**Pending learner response:** Write this explanation in your own words. No learner reflection or participation claim has been supplied.
<!-- end response reflection-4 -->

---

## 🔗 Section 5: Relationships and Correlation

9. When would you use Spearman instead of Pearson?<br>
   `Answer:` See the completed answer below.

<!-- response answer-9 -->
**Answer:** Use Spearman for ordinal/ranked variables or a monotonic relationship that need not be linear, and when extreme magnitudes make Pearson too sensitive. It correlates ranks; inspect a plot because neither coefficient fully describes non-monotonic patterns.
<!-- end response answer-9 -->

10. A news story says "cities with more ice-cream sales have more drownings." Give a likely confounder.<br>
    `Answer:` See the completed answer below.

<!-- response answer-10 -->
**Answer:** Warm weather or season: hotter weather raises ice-cream sales and swimming exposure, which can also increase drownings. The association does not establish that buying ice cream causes drowning; city population may also affect both raw totals.
<!-- end response answer-10 -->

---

### ✏️ Task: Correlation Report

```python
# Using pokemon.csv:
# 1. Compute the Pearson and Spearman correlation matrices of the six stats.
# 2. List the three strongest pairs (use the upper triangle).
# 3. Recompute r(Attack, Defense) for Legendary and non-Legendary separately.
```

<!-- response task-5 -->
**Completed task:** Support notebook task 5 computes both six-stat matrices and ranks the **15 unique pairs** from each strict upper triangle by absolute correlation, retaining signs.

| Method | Strongest pair | Coefficient |
|---|---|---:|
| Pearson | Defense / Sp. Def | 0.510747 |
| Pearson | Sp. Atk / Sp. Def | 0.506121 |
| Pearson | Sp. Atk / Speed | 0.473018 |
| Spearman | Defense / Sp. Def | 0.578816 |
| Spearman | Sp. Atk / Sp. Def | 0.571757 |
| Spearman | HP / Attack | 0.565734 |

Attack/Defense Pearson r is **0.437192** for non-Legendary (n=735), and **-0.210974** for Legendary (n=65), compared with **0.438687** overall. The corresponding within-group Spearman values are 0.501235 and -0.178946. Aggregation masks the different within-group relationships; none of these coefficients establishes causation.

[Pearson matrix](Worksheet-OutputFiles/pearson_matrix.csv), [Spearman matrix](Worksheet-OutputFiles/spearman_matrix.csv), [Pearson pairs](Worksheet-OutputFiles/pearson_pairs.csv), [Spearman pairs](Worksheet-OutputFiles/spearman_pairs.csv), [group correlations](Worksheet-OutputFiles/attack_defense_by_legendary.csv).
<!-- end response task-5 -->

### 🤖 Explain It

In your own words: Anscombe's four datasets all have r = 0.82. What does that teach you about reporting a correlation without a plot? What's the danger of a single summary number?

<!-- response reflection-5 -->
**Pending learner response:** Write this explanation in your own words. No learner reflection or participation claim has been supplied.
<!-- end response reflection-5 -->

---

## 🧾 Submit Checklist

- [ ] I built a data dictionary that separates dtype from measurement scale.
- [ ] I used an ordered category and computed a proportion from a boolean column.
- [ ] I reported center and spread that fit a column's shape, and explained `ddof`.
- [ ] I flagged outliers with the IQR rule, inspected them, and decided what to do with them.
- [ ] I compared groups with sizes and rates, using a crosstab and a pivot table.
- [ ] I computed Pearson and Spearman correlations and explained a possible confounder.
- [ ] I completed the "Explain It" prompts in my own words.
