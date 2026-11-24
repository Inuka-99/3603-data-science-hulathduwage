# 📝 Quiz: 07 - Describing Data

36 questions covering types of data, center and spread, shape and outliers, comparing groups, and relationships and correlation. Mix of multiple choice, true/false, code-tracing, and short answer.

Try every question on your own first. The Answer Key is at the bottom, no peeking. If you're using an AI tutor, paste in *your answer* and ask it to check your reasoning rather than asking it to solve the question first.

---

## Section A — Types of Data

**1.** (Short Answer) What's the difference between a column's **dtype** and its **measurement scale**?


<!-- RESPONSE Q1 -->
**Answer:** A dtype describes how pandas stores values, such as integer, float, string, or category. A measurement scale describes what those values mean (nominal, ordinal, interval, or ratio) and which comparisons and calculations make sense. Numeric storage does not make an ID a quantitative measurement.
<!-- END RESPONSE Q1 -->
**2.** (Multiple Choice) Titanic's `Pclass` is stored as `1`, `2`, `3`. Its measurement scale is:
A) Nominal  B) Ordinal  C) Interval  D) Ratio


<!-- RESPONSE Q2 -->
**Answer:** **B) Ordinal.** The classes have an order, but the gaps between class codes are not equal measurements of service or wealth.
<!-- END RESPONSE Q2 -->
**3.** (Multiple Choice) Which scale has a true zero that means "none of it"?
A) Nominal  B) Ordinal  C) Interval  D) Ratio


<!-- RESPONSE Q3 -->
**Answer:** **D) Ratio.** Its zero represents none of the measured quantity, making ratios meaningful.
<!-- END RESPONSE Q3 -->
**4.** (True/False) Temperature in °C is ratio data, because 20°C is twice 10°C.


<!-- RESPONSE Q4 -->
**Answer:** **False.** Celsius is interval data: temperature differences are meaningful, but its zero is not an absence of temperature, so 20°C is not twice 10°C in an absolute-temperature sense.
<!-- END RESPONSE Q4 -->
**5.** (Short Answer) Is "number of siblings aboard" discrete or continuous? How can you tell?


<!-- RESPONSE Q5 -->
**Answer:** Discrete: siblings are counted in whole numbers (0, 1, 2, …), rather than measured at arbitrary fractional values.
<!-- END RESPONSE Q5 -->
**6.** (Code Tracing) What prints?
```python
s = pd.Series([True, False, True, True])
print(s.mean())
```


<!-- RESPONSE Q6 -->
**Answer:** `0.75` prints. True contributes 1 and False contributes 0, so the mean is 3/4, the proportion of True values.
<!-- END RESPONSE Q6 -->
**7.** (Short Answer) Why is `titanic['PassengerId'].mean()` meaningless, even though pandas computes it without complaint?


<!-- RESPONSE Q7 -->
**Answer:** PassengerId is an identifier, so its numbers are labels rather than measured quantities. Their average depends on arbitrary numbering and has no useful meaning as an average passenger characteristic.
<!-- END RESPONSE Q7 -->
**8.** (Short Answer) What does `ordered=True` in `pd.CategoricalDtype([...], ordered=True)` let you do that a plain `str` column can't?

<!-- RESPONSE Q8 -->
**Answer:** It records an explicit meaningful category order. Pandas can sort by that declared order and make ordered comparisons (for example, low < medium < high), rather than using a string column's alphabetical ordering.
<!-- END RESPONSE Q8 -->

---

## Section B — Center and Spread

**9.** (Short Answer) Which is more robust to outliers, the mean or the median? Why?


<!-- RESPONSE Q9 -->
**Answer:** The median: it depends on the middle position after sorting, so making a few extreme values still more extreme usually has little effect. The mean uses every magnitude, so extremes pull it toward them.
<!-- END RESPONSE Q9 -->
**10.** (Code Tracing) What prints?
```python
s = pd.Series([2, 4, 4, 6, 100])
print(s.median(), s.mode()[0])
```


<!-- RESPONSE Q10 -->
**Answer:** `4.0 4` prints: the middle sorted value is 4, and 4 is also the most frequent value. The median is represented as a float and the mode here as an integer.
<!-- END RESPONSE Q10 -->
**11.** (Short Answer) A column's mean is much larger than its median. What does that suggest?


<!-- RESPONSE Q11 -->
**Answer:** It suggests a right-skewed distribution or a few large values pulling the mean above the median. Inspect the distribution and records before deciding whether those values are errors.
<!-- END RESPONSE Q11 -->
**12.** (Multiple Choice) `pd.Series(data).std()` and `np.std(data)` give slightly different answers because:
A) NumPy rounds  B) pandas skips NaN  C) they use different default `ddof`  D) one is variance


<!-- RESPONSE Q12 -->
**Answer:** **C) They use different default `ddof`.** Pandas uses `ddof=1` (denominator n−1, sample standard deviation); NumPy uses `ddof=0` (denominator n, population standard deviation). Missing-value handling can also differ, but this choice explains different results for the same complete numeric input.
<!-- END RESPONSE Q12 -->
**13.** (Short Answer) What's the IQR, and how do you compute it in pandas?


<!-- RESPONSE Q13 -->
**Answer:** IQR is the interquartile range, the width of the middle 50%: Q3 − Q1. In pandas, use `s.quantile(0.75) - s.quantile(0.25)`; these quantiles exclude missing values by default.
<!-- END RESPONSE Q13 -->
**14.** (Short Answer) In `.describe()`, a column's `count` is 714 but the DataFrame has 891 rows. What does that tell you?


<!-- RESPONSE Q14 -->
**Answer:** The column has 714 observed values and 177 missing values. `.describe()` counts nonmissing entries, not all DataFrame rows.
<!-- END RESPONSE Q14 -->
**15.** (Short Answer) You fill 177 missing ages with the median age. What happens to the standard deviation, and why?


<!-- RESPONSE Q15 -->
**Answer:** For these Titanic ages, the sample standard deviation decreases from about 14.53 to 13.02 years. Adding 177 copies of the median concentrates the data near its center and makes the filled column appear less variable; it does not recover the real missing ages.
<!-- END RESPONSE Q15 -->
**16.** (Short Answer) Which spread statistic pairs naturally with the median, and which with the mean?

<!-- RESPONSE Q16 -->
**Answer:** Pair the median with IQR (both robust to extremes), and the mean with standard deviation.
<!-- END RESPONSE Q16 -->

---

## Section C — Shape and Outliers

**17.** (Multiple Choice) A column with `.skew()` of 4.8 is:
A) roughly symmetric  B) strongly left-skewed  C) strongly right-skewed  D) heavy-tailed but symmetric


<!-- RESPONSE Q17 -->
**Answer:** **C) Strongly right-skewed.** The positive sign identifies the long right tail, and 4.8 is well beyond the rough strong-skew threshold of 1.
<!-- END RESPONSE Q17 -->
**18.** (Short Answer) Write the formulas for the lower and upper fences of the 1.5 × IQR rule.


<!-- RESPONSE Q18 -->
**Answer:** Lower fence = Q1 − 1.5 × (Q3 − Q1); upper fence = Q3 + 1.5 × (Q3 − Q1). Flag values strictly below the lower fence or strictly above the upper fence; a value on a fence is not outside it.
<!-- END RESPONSE Q18 -->
**19.** (Short Answer) On Titanic fares, the IQR rule flags 116 values but the |z| > 3 rule flags only 20. Why are z-scores less sensitive on a skewed column?


<!-- RESPONSE Q19 -->
**Answer:** The high fares inflate both the mean and the standard deviation used in z-scores. The inflated standard deviation makes the threshold farther away, masking many unusual fares. IQR uses more robust quartiles, so it flags 116 here while the sample-standard-deviation z-score rule flags 20.
<!-- END RESPONSE Q19 -->
**20.** (True/False) Any value flagged as an outlier should be removed before analysis.


<!-- RESPONSE Q20 -->
**Answer:** **False.** A flag means unusual, not automatically incorrect. Inspect the record and context; fix errors when justified and retain genuine extreme observations when they belong in the analysis.
<!-- END RESPONSE Q20 -->
**21.** (Short Answer) Name two things you can do with a real-but-extreme value instead of deleting it.


<!-- RESPONSE Q21 -->
**Answer:** Keep the original values and summarize with robust statistics such as median and IQR; or analyze a documented log-transformed version to reduce skew. Retain the original column in either case.
<!-- END RESPONSE Q21 -->
**22.** (Short Answer) Why can a value be an outlier within its group but not in the whole dataset (or the other way around)?

<!-- RESPONSE Q22 -->
**Answer:** Each group has its own center and spread, so its quartile-based fences differ from the pooled fences. A moderately high third-class fare may exceed the third-class fence but not the overall fence; an expensive first-class fare may exceed the overall fence but still be ordinary within first class.
<!-- END RESPONSE Q22 -->

---

## Section D — Comparing Groups

**23.** (Short Answer) More 3rd-class passengers survived than 2nd-class passengers, but 3rd class had the lower survival rate. How can both be true?


<!-- RESPONSE Q23 -->
**Answer:** Third class had many more passengers: 119 of 491 survived (24.2%), compared with 87 of 184 in second class (47.3%). The larger starting group can yield more survivors even with a lower proportion surviving.
<!-- END RESPONSE Q23 -->
**24.** (Code Tracing) What does this compute?
```python
titanic.groupby('Sex')['Survived'].mean()
```


<!-- RESPONSE Q24 -->
**Answer:** It computes the survival proportion separately for each Sex group by averaging the 0/1 Survived values. For this CSV it returns female ≈ 0.742038 (74.2%) and male ≈ 0.188908 (18.9%), as a Series indexed by Sex.
<!-- END RESPONSE Q24 -->
**25.** (Multiple Choice) In `pd.crosstab(df['class'], df['Sex'], normalize='index')`, what adds up to 100%?
A) each row  B) each column  C) the whole table  D) nothing; it's counts


<!-- RESPONSE Q25 -->
**Answer:** **A) Each row.** `normalize='index'` divides each cell by its row total, so the row proportions sum to 1 (100%).
<!-- END RESPONSE Q25 -->
**26.** (Short Answer) What's the difference between what `pd.crosstab()` and `pivot_table()` compute?


<!-- RESPONSE Q26 -->
**Answer:** By default, `pd.crosstab()` counts the frequency of combinations of categorical values and can normalize those counts. `pivot_table()` aggregates a supplied value column, such as mean or median Fare, across row and column groups. Crosstab can also aggregate values when `values` and `aggfunc` are supplied, so the distinction describes their usual/default roles.
<!-- END RESPONSE Q26 -->
**27.** (Short Answer) Why should a group summary always include the group's size?


<!-- RESPONSE Q27 -->
**Answer:** Size shows how much evidence supports the summary: tiny groups can have unstable means or extreme rates. Also distinguish total rows (`size`) from known values of the summarized column (`count`), since missing data can reduce the effective sample.
<!-- END RESPONSE Q27 -->
**28.** (Short Answer) Cherbourg passengers survived at a higher rate than other ports. Explain how ticket class could be a **confounder** here.


<!-- RESPONSE Q28 -->
**Answer:** Cherbourg had a higher share of first-class passengers, and first-class passengers also had higher survival rates. Class composition can therefore explain part of the apparent port difference; compare ports within the same ticket class before attributing survival differences to the embarkation port itself.
<!-- END RESPONSE Q28 -->
**29.** (Short Answer) What does `observed=True` do in a `groupby` on a categorical column?

<!-- RESPONSE Q29 -->
**Answer:** It includes only category levels (or category combinations) actually observed in the data, rather than materializing unused categorical groups. Missing grouping keys are a separate issue controlled by `dropna`.
<!-- END RESPONSE Q29 -->

---

## Section E — Relationships and Correlation

**30.** (Short Answer) Why is covariance hard to interpret on its own, and how does correlation fix that?


<!-- RESPONSE Q30 -->
**Answer:** Covariance's size changes with measurement units and has product units, so it lacks a common strength scale. Pearson correlation divides covariance by the two standard deviations, producing a unitless value between −1 and 1 for nonconstant variables; sign shows direction and magnitude summarizes linear strength.
<!-- END RESPONSE Q30 -->
**31.** (Multiple Choice) r = −0.85 means:
A) a weak negative linear relationship  B) a strong negative linear relationship  C) 85% of y is caused by x  D) no relationship


<!-- RESPONSE Q31 -->
**Answer:** **B) A strong negative linear relationship.** Larger x values tend to accompany smaller y values; this does not establish causation or a percentage caused.
<!-- END RESPONSE Q31 -->
**32.** (Short Answer) Give two situations where Spearman is a better choice than Pearson.


<!-- RESPONSE Q32 -->
**Answer:** When the data are ordinal/ranked, and when the relationship is curved but monotonic (consistently increasing or decreasing). Spearman correlates ranks, so it does not require equally spaced scores or a straight-line pattern.
<!-- END RESPONSE Q32 -->
**33.** (True/False) If r = 0, the two columns have no relationship at all.


<!-- RESPONSE Q33 -->
**Answer:** **False.** Pearson r = 0 means no linear association in that summary, but a nonlinear relationship can still be strong, such as y = x² for x values symmetric around zero.
<!-- END RESPONSE Q33 -->
**34.** (Short Answer) Name three explanations for a correlation besides "A causes B."


<!-- RESPONSE Q34 -->
**Answer:** Reverse causation (B causes A); a third variable influencing both (confounding); or chance/coincidence, especially when many candidate relationships are tested.
<!-- END RESPONSE Q34 -->
**35.** (Short Answer) What is Anscombe's quartet, and what lesson does it teach?


<!-- RESPONSE Q35 -->
**Answer:** Four datasets with 11 (x, y) pairs each have nearly identical means, variances, correlations, and fitted linear regressions, yet very different patterns, including curvature and influential points. Numerical summaries alone can hide important structure, so inspect or plot the data.
<!-- END RESPONSE Q35 -->
**36.** (Short Answer) In the penguins data, bill length and depth correlate at −0.24 overall but +0.39 to +0.65 within each species. What's this called, and what causes it here?


<!-- RESPONSE Q36 -->
**Answer:** This is Simpson's paradox: an association reverses direction when groups are pooled. Species is the confounder here: Gentoos tend to have longer but shallower bills than the other species, while length and depth increase together within each species. Between-species differences create the negative pooled correlation despite positive within-species correlations.
<!-- END RESPONSE Q36 -->
