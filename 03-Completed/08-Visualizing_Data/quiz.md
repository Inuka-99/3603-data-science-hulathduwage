# 📝 Quiz: 08 - Visualizing Data

36 questions covering object-oriented Matplotlib, plotting with pandas, Seaborn distributions, Seaborn relationships and categories, and choosing and designing charts. Mix of multiple choice, true/false, code-tracing, and short answer.

Try every question on your own first. The Answer Key is at the bottom, no peeking. If you're using an AI tutor, paste in *your answer* and ask it to check your reasoning rather than asking it to solve the question first.

---

## Section A — Matplotlib, Object-Oriented

**1.** (Short Answer) In `fig, ax = plt.subplots()`, what's the difference between `fig` and `ax`?


<!-- RESPONSE Q1 -->
**Answer:** `fig` is the whole Figure canvas, containing the layout, subplots, and figure-wide title and saving operations. `ax` is one Axes, the individual plotting area with its own scales, labels, title, and plotted artists.
<!-- END RESPONSE Q1 -->
**2.** (Short Answer) Why does the object-oriented style scale better than `plt.title()`/`plt.xlabel()` calls when a figure has several charts?


<!-- RESPONSE Q2 -->
**Answer:** Each call targets a named Axes, such as `axes[1].set_title(...)`, so it is clear which panel changes. Stateful `plt.title()` or `plt.xlabel()` acts on whichever axes is currently active, which is easier to mix up in multi-panel figures.
<!-- END RESPONSE Q2 -->
**3.** (Code Tracing) How many axes does this create, and how do you reach the bottom-right one?
```python
fig, axes = plt.subplots(2, 3)
```


<!-- RESPONSE Q3 -->
**Answer:** It creates **six Axes**, arranged in two rows and three columns. The bottom-right Axes is `axes[1, 2]` because NumPy array indexing starts at zero.
<!-- END RESPONSE Q3 -->
**4.** (Short Answer) What does `sharey=True` do, and why does it matter when comparing panels?


<!-- RESPONSE Q4 -->
**Answer:** It links the panels' y-axis scales and limits. Equal vertical distances then represent equal quantities across panels, preventing an automatically rescaled small group from appearing as large as a bigger group.
<!-- END RESPONSE Q4 -->
**5.** (Short Answer) When is a log-scale axis a good idea? What value can't it show?


<!-- RESPONSE Q5 -->
**Answer:** A logarithmic axis helps show positive values spanning orders of magnitude or a long right tail, making relative/multiplicative differences easier to compare. A standard real logarithmic axis cannot show zero or negative values; any exclusions or alternative transformation must be stated.
<!-- END RESPONSE Q5 -->
**6.** (Multiple Choice) Which formatter displays `0.25` on an axis as `25%`?
A) `StrMethodFormatter('{x:.0%}')`  B) `PercentFormatter(xmax=1)`  C) `PercentFormatter(xmax=100)`  D) `ax.set(percent=True)`


<!-- RESPONSE Q6 -->
**Answer:** **B) `PercentFormatter(xmax=1)`** is the course's intended answer: 1 represents 100%, so 0.25 represents 25%. **A also produces `25%`**, because Python's `.0%` format multiplies by 100. Thus this question has two technically correct options; C uses a 0–100 input scale, and D is not the relevant Axes API.
<!-- END RESPONSE Q6 -->
**7.** (Short Answer) Why should you call `fig.savefig()` before `plt.show()`, and why `plt.close(fig)` inside a loop?


<!-- RESPONSE Q7 -->
**Answer:** Save before showing because some display backends close or clear a figure when it is shown. Close each finished figure inside a loop to release its resources and prevent many open figures from accumulating.
<!-- END RESPONSE Q7 -->
**8.** (Short Answer) In `ax.annotate('Peak', xy=(5, 10), xytext=(7, 12), arrowprops=...)`, what do `xy` and `xytext` each mean?

<!-- RESPONSE Q8 -->
**Answer:** `xy` is the point being annotated, normally in data coordinates. `xytext` is where the annotation text is positioned, also in data coordinates by default. The arrow connects the text to the annotated point.
<!-- END RESPONSE Q8 -->

---

## Section B — Plotting with Pandas

**9.** (Short Answer) When pandas plots a DataFrame, what becomes the x-axis, and what becomes each line or set of bars?


<!-- RESPONSE Q9 -->
**Answer:** For a normal wide DataFrame `.plot()` call, the index supplies the x-axis and each selected numeric column supplies a separate line or bar series, usually identified in the legend. Explicit `x=`, `y=`, or a different plot kind can change that mapping.
<!-- END RESPONSE Q9 -->
**10.** (Code Tracing) What kind of chart does this draw, and what are the bar labels?
```python
titanic['Embarked'].value_counts().plot.barh()
```


<!-- RESPONSE Q10 -->
**Answer:** A horizontal bar chart of embarkation-port counts. The category labels are **S, C, Q**, in descending frequency: 644, 168, and 77 respectively. Missing Embarked values are excluded by `value_counts()` by default; the labels appear on the y-axis and counts on the x-axis.
<!-- END RESPONSE Q10 -->
**11.** (Short Answer) You plot a `pivot_table` with classes as the index and sexes as the columns. How do you switch the chart to group by sex instead?


<!-- RESPONSE Q11 -->
**Answer:** Transpose the summary table before plotting: `table.T.plot.bar()`. Sexes become the index and x-axis groups, while classes become the columns and separate bar series.
<!-- END RESPONSE Q11 -->
**12.** (Short Answer) What does a 100% stacked bar chart show, and which `crosstab` argument produces the right table for it?


<!-- RESPONSE Q12 -->
**Answer:** It shows each group's category composition as proportions of a common whole, so every full bar totals 100%. Use `pd.crosstab(group, category, normalize='index')` for row-wise shares, then plot the result with `stacked=True` and a percent-formatted axis.
<!-- END RESPONSE Q12 -->
**13.** (Short Answer) What's the difference between wide and long data? Which does pandas `.plot` expect, and which does Seaborn expect?


<!-- RESPONSE Q13 -->
**Answer:** Wide data store different series in separate columns; long data store one observation per row with category labels and measured values in columns. Pandas DataFrame `.plot()` commonly uses wide summary tables, while Seaborn's named `data=`, `x=`, `y=`, and `hue=` mappings commonly use long observation-level data. Both libraries also have other supported input forms.
<!-- END RESPONSE Q13 -->
**14.** (Short Answer) Should you sort the bars of an ordinal category (like ticket class) by value? Why or why not?

<!-- RESPONSE Q14 -->
**Answer:** Usually no: keep ordinal categories in their meaningful order, such as first, second, and third class. Sorting them by counts or values would obscure that ordered structure. Value sorting is more suitable for unordered nominal categories when ranking is the question.
<!-- END RESPONSE Q14 -->

---

## Section C — Seaborn: Distributions

**15.** (Short Answer) What's the difference between an axes-level and a figure-level Seaborn function? Give one example of each.


<!-- RESPONSE Q15 -->
**Answer:** An axes-level function draws on a single Axes, can receive `ax=`, and usually returns that Axes; `sns.histplot()` is an example. A figure-level function creates and manages a whole figure or facet grid; `sns.displot()` returns a FacetGrid and uses options such as `col=`, `row=`, `height=`, and `aspect=`.
<!-- END RESPONSE Q15 -->
**16.** (Short Answer) What does `hue='species'` do in `sns.histplot()`?


<!-- RESPONSE Q16 -->
**Answer:** It splits the observations by species and assigns a different color to each species' histogram, with a legend explaining the colors. Other arguments control whether those group distributions overlap, stack, or appear side by side.
<!-- END RESPONSE Q16 -->
**17.** (Multiple Choice) Two groups have 500 and 50 rows. To compare the **shapes** of their distributions, use:
A) `stat='count'`  B) `multiple='stack'`  C) `stat='percent', common_norm=False`  D) `binwidth=1`


<!-- RESPONSE Q17 -->
**Answer:** **C) `stat='percent', common_norm=False`.** Each group's histogram independently sums to 100%, allowing shape comparisons despite different sample sizes; counts would also reflect the tenfold size difference.
<!-- END RESPONSE Q17 -->
**18.** (Short Answer) Explain each part of a box plot: the box, the line inside it, the whiskers, and the dots.


<!-- RESPONSE Q18 -->
**Answer:** The box spans Q1 to Q3, so its height is the IQR. The line inside is the median. With the default 1.5 × IQR rule, whiskers reach the most extreme observed values still within Q1 − 1.5 × IQR and Q3 + 1.5 × IQR; they are not the fences themselves. Dots show observed values strictly beyond those fences, which are unusual rather than automatically erroneous.
<!-- END RESPONSE Q18 -->
**19.** (Short Answer) Name one thing a violin plot shows that a box plot hides, and one thing a strip plot shows that a violin hides.


<!-- RESPONSE Q19 -->
**Answer:** A violin shows a smoothed distribution's shape, including peaks or shoulders that a box summary hides. A strip plot shows individual observed values and their point density/sample size; a violin alone does not identify every observation and its width is not automatically a count.
<!-- END RESPONSE Q19 -->
**20.** (Short Answer) How do you read a group's median from an ECDF plot?


<!-- RESPONSE Q20 -->
**Answer:** Find cumulative share 0.5 on the y-axis and read the corresponding x value where the group's ECDF reaches that level. For an even sample, pandas' median averages the two middle observations, so a flat ECDF interval at 0.5 may contain that numerical median rather than identifying a unique x value.
<!-- END RESPONSE Q20 -->
**21.** (True/False) A KDE curve always stays within the actual range of the data.


<!-- RESPONSE Q21 -->
**Answer:** **False.** KDE smoothing can extend beyond the observed minimum and maximum. `cut=0` restricts the displayed estimate to the data range; the smooth estimate is still model-based rather than a list of observed values.
<!-- END RESPONSE Q21 -->
**22.** (Short Answer) Why does `showfliers=False` make sense when you draw a strip plot on top of a box plot?

<!-- RESPONSE Q22 -->
**Answer:** The strip already draws each individual observation, including the outliers. Hiding the box plot's separate flier markers avoids displaying those outlying observations twice while retaining the box and whiskers.
<!-- END RESPONSE Q22 -->

---

## Section D — Seaborn: Relationships and Categories

**23.** (Short Answer) Name two ways to reduce overplotting in a scatter plot.


<!-- RESPONSE Q23 -->
**Answer:** Use partially transparent markers (`alpha` below 1) and smaller markers (`s` in Matplotlib or a suitable Seaborn size setting). These make overlapping points and dense regions easier to see.
<!-- END RESPONSE Q23 -->
**24.** (Short Answer) In the penguins data, one `regplot` line through all the points slopes down, but one line per species slopes up. What's this called, and what's the lesson for fitting trend lines?


<!-- RESPONSE Q24 -->
**Answer:** Simpson's paradox: the pooled bill-length/depth association reverses within species. Species differ in their typical bill dimensions, so the between-species pattern pulls the combined line downward. Inspect groups and fit or compare trends within relevant groups before interpreting one pooled regression; a fitted trend alone does not establish causation.
<!-- END RESPONSE Q24 -->
**25.** (Short Answer) Why did the four Anscombe datasets get identical lines from `lmplot`?


<!-- RESPONSE Q25 -->
**Answer:** Their summary statistics yield essentially the same least-squares slope and intercept: approximately y = 3 + 0.5x. The small rounding differences in the supplied CSV do not change the visual lesson: matching fitted lines can conceal very different point patterns, including curvature and influential observations.
<!-- END RESPONSE Q25 -->
**26.** (Short Answer) What's the difference between `countplot` and `barplot`?


<!-- RESPONSE Q26 -->
**Answer:** `countplot` counts rows in each category. `barplot` computes a numeric estimate for each category—the mean by default—and draws uncertainty/error bars according to its settings. It can use other estimators, so bar height is not automatically a count.
<!-- END RESPONSE Q26 -->
**27.** (Multiple Choice) `sns.barplot(..., errorbar='sd')` draws error bars showing:
A) the 95% confidence interval  B) the standard error  C) one standard deviation of the individual values  D) the IQR


<!-- RESPONSE Q27 -->
**Answer:** **C) One standard deviation of the individual values.** The bars extend approximately one sample standard deviation above and below the group mean, showing individual-value spread rather than confidence in the mean.
<!-- END RESPONSE Q27 -->
**28.** (Short Answer) What does Seaborn's default error bar on a `barplot` represent?


<!-- RESPONSE Q28 -->
**Answer:** A 95% confidence interval for the estimated group mean by default (`errorbar=('ci', 95)`), normally obtained through bootstrap resampling. It describes uncertainty in the estimate, not a range containing 95% of individual observations; a fixed `seed` makes the resampling repeatable.
<!-- END RESPONSE Q28 -->
**29.** (Short Answer) What does a `pointplot` with crossing or diverging lines tell you?


<!-- RESPONSE Q29 -->
**Answer:** It suggests an interaction: the difference or pattern across x categories varies with the hue group, rather than staying parallel. Crossing lines can show a reversal of group ordering. This descriptive pattern should be assessed with uncertainty and context before claiming a population interaction or causal effect.
<!-- END RESPONSE Q29 -->
**30.** (Short Answer) Should a correlation heatmap use a diverging or a sequential color map? What about a heatmap of survival rates? Why?

<!-- RESPONSE Q30 -->
**Answer:** Use a **diverging** color map for correlations, centered at zero with common limits −1 to 1, because positive and negative associations have opposite meanings. Use a **sequential** color map for survival rates, typically fixed at 0 to 1, because these values run from low to high without a special neutral midpoint.
<!-- END RESPONSE Q30 -->

---

## Section E — Choosing and Telling

**31.** (Short Answer) Why must bar charts start at zero, when line charts don't have to?


<!-- RESPONSE Q31 -->
**Answer:** Bar length encodes the magnitude from its baseline; truncating that baseline exaggerates ratios and apparent differences. Line charts principally encode point positions and change, so a clearly labeled nonzero axis can reveal meaningful variation. Compared panels should still use compatible scales.
<!-- END RESPONSE Q31 -->
**32.** (Short Answer) Name the chart you'd choose for each: (a) the distribution of one numeric column, (b) the mix of categories within each group, (c) the relationship between two numeric columns.


<!-- RESPONSE Q32 -->
**Answer:** (a) A histogram for one numeric distribution. (b) A 100% stacked bar chart for category composition within groups. (c) A scatter plot for two numeric columns, using group colors when relevant.
<!-- END RESPONSE Q32 -->
**33.** (Short Answer) What's a palette dictionary, and why use one across a whole report?


<!-- RESPONSE Q33 -->
**Answer:** A dictionary mapping category labels to colors, such as `{'Adelie': ..., 'Chinstrap': ..., 'Gentoo': ...}`. Passing the same palette dictionary throughout the report keeps each category's meaning visually consistent even when a chart's ordering or category subset changes.
<!-- END RESPONSE Q33 -->
**34.** (Short Answer) Rewrite this descriptive title as a finding title: "Mean Body Mass by Species."


<!-- RESPONSE Q34 -->
**Answer:** **Gentoo Penguins Have the Highest Mean Body Mass.** This states the finding supported by the supplied data instead of only naming the variables.
<!-- END RESPONSE Q34 -->
**35.** (True/False) Every bar in a bar chart should have its own distinct color.


<!-- RESPONSE Q35 -->
**Answer:** **False.** Color should encode meaningful groups or highlight a finding. A single color is often sufficient for one bar series; giving every bar a different color adds unnecessary distinctions and can make a report harder to follow.
<!-- END RESPONSE Q35 -->
**36.** (Short Answer) Give two reasons to look at a chart **and** the matching numbers, rather than just one of them.


<!-- RESPONSE Q36 -->
**Answer:** First, charts reveal distribution shape, clusters, nonlinear patterns, and influential points that summary numbers can hide. Second, matching numbers verify exact values, sample sizes, missingness, and the magnitude of apparent differences, helping detect misleading scaling, normalization, or visual impressions.
<!-- END RESPONSE Q36 -->
