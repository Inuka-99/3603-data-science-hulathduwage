# 📝 Worksheet: 08 - Visualizing Data

Use this worksheet to reinforce object-oriented Matplotlib, pandas plotting, Seaborn, and chart design. Each section ends with an **🤖 Explain It** prompt. Write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🖼️ Section 1: Matplotlib, Object-Oriented

1. What's the difference between `plt.title('X')` and `ax.set_title('X')`? When does the difference matter?<br>
   `Answer:` `plt.title('X')` changes the current axes using pyplot's hidden state; `ax.set_title('X')` changes the specific axes object named `ax`. Explicit axes matter when there are multiple panels or a reusable plotting function, because the target is unambiguous.

2. You're comparing three histograms in a 1 × 3 figure. Name two settings that make the panels fair to compare.<br>
   `Answer:` Use identical histogram bin edges and shared axis limits/scales (for example `sharex=True, sharey=True` for the same variable). When group sizes differ, compare normalized within-group densities and display sample sizes rather than interpreting raw heights as distribution shapes.

---

### ✏️ Task: A Reusable Chart Function

```python
# Write plot_distribution(ax, series, title, unit) that draws a histogram on ax,
# marks the mean and median with vertical lines, and labels everything.
# Use it to build a 2 x 2 figure of Titanic Age, Fare (log scale!), SibSp, and Parch.
# Save the figure with fig.savefig().
```

**Completed task:** [Reusable distribution chart](Worksheet-OutputFiles/titanic_distributions.png), implemented in [the support notebook](Worksheet-Support/visualizing_data_worksheet.ipynb). Fare uses a log x-axis with geometric bins and includes only positive fares (876 records); 15 zero fares are explicitly excluded and its mean/median lines describe that same positive-fare subset. Age uses 714 known ages; SibSp and Parch each use all 891 records and integer-centered bins.


### 🤖 Explain It

In your own words: why is a function that takes an `ax` argument more useful than a function that calls `plt.` directly?

**Generated answer:** An ax argument tells a plotting function exactly which panel to draw on. The same function can then be reused in different positions of a multi-panel figure, and the caller controls the layout and saving. Calls such as plt.title() depend on the currently active axes, which can change as figures and panels are created. Explicit axes make the destination clear and reduce accidental changes to another panel.

**Status:** Technical answer generated at Inuka's request; learner own-word review remains pending.

---

## 🐼 Section 2: Plotting with Pandas

3. When you call `.plot.bar()` on a DataFrame, what does the index become, and what do the columns become?<br>
   `Answer:` The index supplies category labels along the x-axis, while each numeric column becomes a separate bar series and usually a legend entry. The values determine bar heights; with `stacked=True`, the column series stack within each index category.

4. Give one example of wide data and the same data in long form.<br>
   `Answer:` Wide example: one row `Generation=1, False=160, True=6`. The same counts in long form are two rows: `(Generation=1, Legendary=False, count=160)` and `(Generation=1, Legendary=True, count=6)`. Long form stores category names as values in a column instead of separate column headings.

---

### ✏️ Task: Summary Table to Chart

```python
# Using pokemon.csv:
# 1. Build a crosstab of Generation vs. Legendary, normalized by row.
# 2. Plot it as a 100% stacked bar chart with a percent-formatted axis.
# 3. Melt the (un-normalized) crosstab into long form with columns Generation, Legendary, count.
```

**Completed task:** [100% stacked generation chart](Worksheet-OutputFiles/legendary_share_by_generation.png). The support notebook displays both the count crosstab and its row-normalized version, then melts the original counts into `Generation`, `Legendary`, and `count`. Each generation sums to 100%; sample sizes are displayed because denominators range from 82 to 166 records.


### 🤖 Explain It

In your own words: when would you plot with pandas `.plot`, and when would you switch to Seaborn?

**Generated answer:** Pandas .plot is convenient for a quick chart of a Series or an already summarized wide table, such as counts by port or a pivot table of survival rates. Seaborn is useful when columns in a long table should map to x, y, hue or facets, or when the chart needs statistical summaries such as distribution comparisons, regression lines or clearly specified uncertainty intervals. Choose the tool that expresses the question clearly; both still require checking grouping, normalization and scales.

**Status:** Technical answer generated at Inuka's request; learner own-word review remains pending.

---

## 🌊 Section 3: Seaborn Distributions

5. Why can a histogram with `hue` and raw counts be misleading when the groups are very different sizes? What's the fix?<br>
   `Answer:` A larger group can have taller bars simply because it contributes more records, even when its relative distribution has the same shape. Use common bins and `stat='density', common_norm=False` to normalize each group separately, and report the group sizes; separate panels with shared scales can also help.

6. Explain how a box plot's whiskers and dots connect to the 1.5 × IQR rule from Module 07.<br>
   `Answer:` Let IQR = Q3 - Q1; the fences are Q1 - 1.5*IQR and Q3 + 1.5*IQR. Box-plot whiskers end at the most extreme observed values still within those fences, rather than necessarily at the fence coordinates. Dots flag observations strictly outside the fences; they are not automatically data errors.

---

### ✏️ Task: Compare Distributions Four Ways

```python
# Using penguins.csv, for flipper_length_mm by species, make a 2 x 2 figure:
# a step histogram with hue, a KDE with hue, a box plot, and a violin plot.
# Use the same species order and the same colors in every panel.
```

**Completed task:** [Four distribution views](Worksheet-OutputFiles/flipper_distributions.png). All panels use Adelie, Chinstrap, Gentoo in the same order and with the same colorblind-safe colors. Step histograms and KDEs use separate within-species density normalization (`common_norm=False`), common x limits, and n labels (151, 68, 123); violin smoothing is limited to observed ranges with `cut=0`.


### 🤖 Explain It

In your own words: the overall penguin body-mass histogram looked like one lumpy pile, and its skew was only 0.47. What did coloring by species reveal, and why couldn't the skew statistic reveal it?

**Generated answer:** Coloring by species revealed that Gentoo penguins form the heavier group near 5,076 g, while Adelie and Chinstrap means are near 3,701 and 3,733 g. Their different distributions create the pooled histogram's lumpy right shoulder. Skew is a single measure of overall asymmetry: a value near 0.47 does not establish that the data come from one population or have one peak. Species-colored distributions and the matching group summaries reveal structure that the pooled skew cannot describe.

**Status:** Technical answer generated at Inuka's request; learner own-word review remains pending.

---

## 🔍 Section 4: Seaborn Relationships and Categories

7. What do the error bars on a default `sns.barplot()` mean? How would `errorbar='sd'` change them?<br>
   `Answer:` By default, a Seaborn barplot estimates each group's mean and shows a 95% bootstrap confidence interval for that estimate. `errorbar='sd'` instead shows mean plus/minus one sample standard deviation, describing the spread of individual observations rather than uncertainty in the mean. Label the interval type and use `seed=` for reproducible bootstrap results.

8. Why should you color a scatter plot by group before adding a trend line?<br>
   `Answer:` Groups can form separate clusters with different intercepts or slopes. Coloring them first reveals structure that one pooled line may hide or reverse, as in Simpson's paradox; correlations and regression slopes alone do not establish causation.

---

### ✏️ Task: Reveal the Paradox

```python
# Using penguins.csv:
# 1. Draw one regplot of bill_length_mm vs. bill_depth_mm for all penguins.
# 2. Draw one regplot per species on a second panel, with r in each label.
# 3. Give each panel a title that states what it shows.
```

**Completed task:** [Pooled versus species regression chart](Worksheet-OutputFiles/penguin_paradox.png). Across 342 complete bill pairs, r = -0.235053; within Adelie (n=151), Chinstrap (n=68), and Gentoo (n=123), r = +0.391492, +0.653536, and +0.643384. Both panels share scales; species composition reverses the direction of the pooled association. Bands are 95% bootstrap confidence intervals for fitted mean trends, not prediction intervals or causal effects.


### 🤖 Explain It

In your own words: explain Simpson's paradox to someone who has never heard of it, using your chart from the task above.

**Generated answer:** In the pooled bill chart, the fitted line slopes downward: longer bills appear to be shallower. When points are separated by species, every fitted line slopes upward. Gentoo penguins tend to have longer, shallower bills than the other species, so differences between species outweigh the positive relationships within species. This reversal is Simpson's paradox. Here the pooled correlation is about -0.235, while the species correlations are positive, about 0.391, 0.654 and 0.643. The chart shows why group structure matters; it does not show that changing bill length causes a change in depth.

**Status:** Technical answer generated at Inuka's request; learner own-word review remains pending.

---

## 🗣️ Section 5: Choosing and Telling

9. Name three things a bar chart's y-axis can do to mislead a reader.<br>
   `Answer:` It can truncate the baseline above zero, exaggerating differences in bar lengths; use unequal tick spacing while presenting it as linear; or give compared panels different limits without making that difference clear. An unexplained log scale on a bar-length chart can also distort the intended comparison. Use a zero baseline and honest, clearly labeled common scales for ordinary comparison bars.

10. What's the difference between a descriptive title and a finding title? Write one of each for the same chart.<br>
    `Answer:` A descriptive title names the variables, such as 'Median Titanic fare by embarkation port.' A finding title states the result, such as 'Cherbourg passengers had the highest median recorded fare.' Both can describe the same chart, but the finding title tells the reader what the evidence shows.

---

### ✏️ Task: Makeover

```python
# Start with: titanic.groupby('Embarked')['Fare'].mean().plot.bar()
# Redesign it with the notebook 05 checklist: the right statistic for skewed data,
# readable port names, sorted bars, a highlight color, bar labels, and a finding title.
# Save the before and after versions.
```

**Completed task:** [Before](Worksheet-OutputFiles/embarked_fare_before.png) and [after](Worksheet-OutputFiles/embarked_fare_after.png). The redesign uses median fare for the skewed distribution, full port names, bars sorted by value, a zero baseline, currency units, direct labels, sample sizes, a Cherbourg highlight, and a finding title. Recorded median fares are Cherbourg GBP 29.70 (n=168), Southampton GBP 13.00 (n=644), and Queenstown GBP 7.75 (n=77); two records with missing embarkation port are excluded and disclosed, while zero fares remain in the medians.


### 🤖 Explain It

In your own words: what's the difference between a chart made for exploration and a chart made for communication? Why do they need different amounts of polish?

**Generated answer:** An exploration chart helps the analyst discover patterns, compare alternatives and decide what to investigate next. A communication chart presents a selected finding to a particular audience, so it needs a clear finding title, readable units, meaningful ordering, consistent colors and enough context about sample sizes and exclusions. Exploration can use quick defaults because the analyst is present to interpret them; a shared chart needs more explanation because its reader may not know the analysis. Both kinds still need accurate data and honest scales.

**Status:** Technical answer generated at Inuka's request; learner own-word review remains pending.

---

## 🧾 Submit Checklist

- [ ] I built a multi-panel Matplotlib figure with `fig, ax`, shared axes, and `fig.savefig()`.
- [ ] I used a log scale, a reference line, and a tick formatter where they helped.
- [ ] I turned a pandas summary table into a chart, and reshaped data between wide and long.
- [ ] I compared distributions across groups fairly (`common_norm=False`, shared axes, sample sizes).
- [ ] I showed a relationship with a scatter plot colored by group, and explained my error bars.
- [ ] I redesigned a default chart using the checklist, with a finding title.
- [ ] I completed the "Explain It" prompts in my own words.
