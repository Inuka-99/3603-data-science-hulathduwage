# 📝 Quiz: 06 - Working with Data (Advanced)

47 questions covering Pandas Series/DataFrames, loading/exploring data, indexing/selection, cleaning, column operations, sorting/filtering/searching, grouping and combining tables, and a "going further" bonus. Mix of multiple choice, true/false, code-tracing, and short answer.

Try every question on your own first — the Answer Key is at the bottom, no peeking. If you're using an AI tutor, paste in *your answer* and ask it to check your reasoning rather than asking it to solve the question first.

---

## Section A — Series and DataFrames

**1.** (Short Answer) What's the difference between a Pandas `Series` and a `DataFrame`?

<!-- response 1 -->
**Answer:** A `Series` is one-dimensional data with index labels. A `DataFrame` is a two-dimensional table with row and column labels; each column is a Series sharing the table's index.
<!-- end response 1 -->

**2.** (Code Tracing) What prints?
```python
s = pd.Series({'a': 1, 'b': 2})
print(s['a'])
```

<!-- response 2 -->
**Answer:** `1`.
<!-- end response 2 -->

**3.** (Short Answer) What does `df.shape` return?

<!-- response 3 -->
**Answer:** A tuple `(number_of_rows, number_of_columns)`.
<!-- end response 3 -->

**4.** (Short Answer) If you add two `Series` together and one has a label the other doesn't, what happens at that label?

<!-- response 4 -->
**Answer:** Pandas aligns by index label. A label present in only one Series gets a missing result (`NaN` for ordinary numeric Series) because the other operand is missing there.
<!-- end response 4 -->

**5.** (Short Answer) You have a list of dictionaries, one per student (the way you stored records in Module 03b). What does `pd.DataFrame(that_list)` turn each dictionary into?

<!-- response 5 -->
**Answer:** Each dictionary becomes one row; its keys become column names. Missing keys produce missing cells.
<!-- end response 5 -->

**6.** (Code Tracing) What prints?
```python
scores = pd.Series([70, 95, 88])
print(scores[scores > 80].tolist())
```

<!-- response 6 -->
**Answer:** `[95, 88]`.
<!-- end response 6 -->

---

## Section B — Loading and Exploring Data

**7.** (Multiple Choice) Which method shows summary statistics (mean, std, min/max) for numeric columns?
A) `.head()`  B) `.columns`  C) `.describe()`  D) `.shape`

<!-- response 7 -->
**Answer:** C) `.describe()`.
<!-- end response 7 -->

**8.** (Short Answer) What's the difference between what `.head()` and `.info()` each tell you about a DataFrame?

<!-- response 8 -->
**Answer:** `.head()` shows the first five rows by default, including actual values. `.info()` prints a structural summary: index, columns, non-null counts, dtypes, and memory usage.
<!-- end response 8 -->

**9.** (Short Answer) How do you count how many missing values are in *each column* of a DataFrame?

<!-- response 9 -->
**Answer:** `df.isna().sum()` (equivalently, `df.isnull().sum()`). The sum counts missing cells separately in each column.
<!-- end response 9 -->

**10.** (Short Answer) What do `df.duplicated().sum()` and `df['col'].value_counts(dropna=False)` each tell you?

<!-- response 10 -->
**Answer:** `df.duplicated().sum()` counts rows identical to an earlier row across all columns, excluding each first occurrence. `df['col'].value_counts(dropna=False)` counts each distinct column value, including missing values.
<!-- end response 10 -->

**11.** (Short Answer) Titanic's `Age` column holds whole numbers, but its dtype is `float64`. Why?

<!-- response 11 -->
**Answer:** The intended reason is that ordinary NumPy `int64` cannot represent `NaN`, while `float64` can; the supplied file has 177 missing ages. The premise is slightly simplified: this Titanic file also contains fractional ages (for example, 0.83), so floating point is appropriate for those values too.
<!-- end response 11 -->

---

## Section C — Indexing and Selection

**12.** (Short Answer) What's the difference between `.loc[]` and `.iloc[]`?

<!-- response 12 -->
**Answer:** `.loc[]` selects by index/column labels; `.iloc[]` selects by zero-based integer row/column positions.
<!-- end response 12 -->

**13.** (Short Answer) Is `df.loc[0:4]` inclusive or exclusive of row `4`? What about `df.iloc[0:4]` and position `4`?

<!-- response 13 -->
**Answer:** `.loc[0:4]` includes label `4`; `.iloc[0:4]` excludes position `4` and selects positions 0 through 3.
<!-- end response 13 -->

**14.** (Short Answer) What symbols does Pandas require for combining conditions when filtering a DataFrame (instead of the `and`/`or` keywords)?

<!-- response 14 -->
**Answer:** Use `&` for elementwise AND and `|` for elementwise OR, with parentheses around each comparison. Use `~` to negate a boolean mask.
<!-- end response 14 -->

**15.** (Short Answer) What does `df[df['Age'] < 10]` return?

<!-- response 15 -->
**Answer:** A DataFrame containing all columns for passengers whose recorded `Age` is below 10. Missing ages do not satisfy this comparison.
<!-- end response 15 -->

**16.** (Short Answer) Rewrite `df[(df['Embarked'] == 'C') | (df['Embarked'] == 'Q')]` using `.isin()`. Does `df['Age'].between(13, 19)` include ages 13 and 19?

<!-- response 16 -->
**Answer:** `df[df['Embarked'].isin(['C', 'Q'])]`. Yes, `.between(13, 19)` includes both endpoints by default (`inclusive='both'`).
<!-- end response 16 -->

**17.** (Multiple Choice) Which one returns a `DataFrame` rather than a `Series`?
A) `df['Age']`  B) `df[['Age']]`  C) `df.Age`  D) `df.loc[0]`

<!-- response 17 -->
**Answer:** B) `df[['Age']]` returns a one-column DataFrame; the others return a Series in this example with unique columns/index labels.
<!-- end response 17 -->

**18.** (Short Answer) After `by_id = df.set_index('PassengerId')`, what does `by_id.loc[2]` select, and how is that different from `df.loc[2]`?

<!-- response 18 -->
**Answer:** `by_id.loc[2]` selects PassengerId 2, the second passenger in the supplied CSV. `df.loc[2]` still uses the original default index and selects its label 2, the third passenger (PassengerId 3). `set_index()` did not modify `df`.
<!-- end response 18 -->

**19.** (Code Tracing) After `by_id = titanic.set_index('PassengerId')`, do `by_id.loc[3]` and `by_id.iloc[3]` select the same passenger? Why or why not?

<!-- response 19 -->
**Answer:** No. `by_id.loc[3]` selects PassengerId 3 (Heikkinen, Miss. Laina); `by_id.iloc[3]` selects the fourth row, PassengerId 4 (Futrelle, Mrs. Jacques Heath (Lily May Peel)). Labels and zero-based positions differ after setting the index.
<!-- end response 19 -->

**20.** (Short Answer) Write a filter for passengers who did **not** board at Southampton (`'S'`), using `~` and `.isin()`.

<!-- response 20 -->
**Answer:** `df[~df['Embarked'].isin(['S'])]`. This also retains missing embarkation values because they are not members of `['S']`; add `& df['Embarked'].notna()` inside the mask if only known non-S ports should be kept.
<!-- end response 20 -->

**21.** (Short Answer) What's wrong with `df[df['Age'] < 10]['child'] = True`, and what should you write instead?

<!-- response 21 -->
**Answer:** This is chained assignment: it assigns through an intermediate filtered object and does not reliably update `df` (under copy-on-write it does not update the original). Use `df.loc[df['Age'] < 10, 'child'] = True`. Initialize `df['child'] = False` first if every other row should be False.
<!-- end response 21 -->

---

## Section D — Cleaning

**22.** (Short Answer) What's the difference between `.dropna()` and `.fillna()`?

<!-- response 22 -->
**Answer:** `.dropna()` removes rows with missing values by default (or columns with `axis=1`, according to the specified criteria). `.fillna()` replaces missing cells with supplied values instead of removing their rows.
<!-- end response 22 -->

**23.** (Short Answer) What does `pd.to_numeric(col, errors='coerce')` do to a value like `'ninety'` in that column?

<!-- response 23 -->
**Answer:** It converts numeric-looking values to numbers and coerces the unparseable value `'ninety'` to a missing numeric value, normally `NaN`.
<!-- end response 23 -->

**24.** (True/False) `NaN` and an empty string `""` are always treated identically by `.isnull()`.

<!-- response 24 -->
**Answer:** False. `NaN` is missing, but an existing empty string `''` is not missing to `.isnull()`. CSV loading may convert empty fields to missing values first.
<!-- end response 24 -->

**25.** (Short Answer) Two rows have the same `order_id` but different `amount`s. Does `df.drop_duplicates()` remove one of them? What would you write to keep only the last row for each `order_id`?

<!-- response 25 -->
**Answer:** No: different amounts make the full rows different. Use `df = df.drop_duplicates(subset=['order_id'], keep='last')`. Here 'last' means current row order; sort by a timestamp first if it should mean latest in time.
<!-- end response 25 -->

**26.** (Short Answer) A survey stores missing ages as `-1`. Why is that a problem for `df['age'].mean()`, and how do you fix it?

<!-- response 26 -->
**Answer:** Pandas treats `-1` as a real age, so it lowers the mean. Replace the placeholder first: `df['age'] = df['age'].replace(-1, float('nan'))`, then `df['age'].mean()` skips missing values by default.
<!-- end response 26 -->

**27.** (Short Answer) A date column holds `'2022-01-01'`, `'2022/03/01'`, and `'April 5, 2022'`. Why can `pd.to_datetime(col, errors='coerce')` turn two perfectly valid dates into `NaT`, and how do you fix it?

<!-- response 27 -->
**Answer:** Modern pandas infers one consistent format from the first non-missing value; other formats may fail that format and become `NaT` under `errors='coerce'`. Use `pd.to_datetime(col, errors='coerce', format='mixed')` to infer each element's format, then inspect conversion failures. Specify an exact format when the data uses a single known format.
<!-- end response 27 -->

**28.** (Short Answer) Why does `.astype('int64')` fail on a column with missing values, while `.astype('Int64')` works?

<!-- response 28 -->
**Answer:** Lowercase `int64` is a NumPy integer dtype that cannot hold missing values. Pandas' nullable `Int64` stores integers plus `<NA>`, so it works for otherwise valid whole-number data with gaps. It does not make non-integer values valid integers.
<!-- end response 28 -->

**29.** (Short Answer) Before deleting rows with a repeated `order_id`, why would you look at `df[df.duplicated(subset=['order_id'], keep=False)]` first?

<!-- response 29 -->
**Answer:** `keep=False` reveals every row in each repeated-ID group, including the first. Inspect them to distinguish exact copies from corrections, legitimate separate records, or conflicting data before choosing a deletion rule.
<!-- end response 29 -->

---

## Section E — Column Operations, Sorting, Filtering, and Searching

**30.** (Short Answer) How do you create a new column that's the sum of two existing numeric columns?

<!-- response 30 -->
**Answer:** For columns `a` and `b`: `df['total'] = df['a'] + df['b']`.
<!-- end response 30 -->

**31.** (Short Answer) What does `.apply()` do that you could also do with a `for` loop over rows — and why is `.apply()` usually preferred?

<!-- response 31 -->
**Answer:** `Series.apply(func)` calls a function for each value; `df.apply(func, axis=1)` calls it for each row and combines the results. It packages custom transformations more concisely than a manual loop and preserves index alignment, but Python-function `.apply()` still loops internally and is not automatically faster. Prefer whole-column operations when available.
<!-- end response 31 -->

**32.** (Short Answer) What does `ascending=False` do inside `df.sort_values(by='score', ascending=False)`?

<!-- response 32 -->
**Answer:** Sorts `score` from highest to lowest (descending). Missing values remain last by default.
<!-- end response 32 -->

**33.** (Short Answer) What's the main advantage of `.query()` over bracket-based boolean filtering (`df[df['col'] > 5]`)?

<!-- response 33 -->
**Answer:** Readability for longer conditions: column names and `and`/`or` can appear directly in an expression string, for example `df.query('col > 5')`, without repeating `df[...]`.
<!-- end response 33 -->

**34.** (Code Tracing) `bonus` is a brand-new column. What value do the rows with `score >= 80` get in it?
```python
df.loc[df['score'] < 80, 'bonus'] = 5
```

<!-- response 34 -->
**Answer:** Missing values (`NaN` in this numeric column). Only rows with `score < 80` receive 5; pandas creates the other cells as missing because `bonus` did not previously exist.
<!-- end response 34 -->

**35.** (Short Answer) To compute `price * qty` for every row, why should you write `df['price'] * df['qty']` instead of looping with `.iterrows()`? When *is* a loop (preferably `.itertuples()`) the right tool?

<!-- response 35 -->
**Answer:** Whole-column multiplication is concise, vectorized, usually much faster, and avoids `.iterrows()`'s per-row Series creation and possible dtype coercion. Use a loop when each row requires a distinct action or sequential processing that cannot be expressed as a whole-column operation, such as writing a separate file per record; prefer `.itertuples()` then.
<!-- end response 35 -->

**36.** (Short Answer) What do `case=False` and `na=False` each do in `df['name'].str.contains('an', case=False, na=False)`?

<!-- response 36 -->
**Answer:** `case=False` ignores letter case while matching `'an'`; `na=False` makes a missing name produce False (no match), yielding a usable boolean filter.
<!-- end response 36 -->

**37.** (Code Tracing) A student has `math = 95` and `average = 91`. What is their `award` after these three lines, and what would it be if the last two lines were swapped?
```python
df['award'] = 'None'
df.loc[df['average'] >= 85, 'award'] = 'Honor Roll'
df.loc[df['math'] >= 90, 'award'] = 'Math Star'
```

<!-- response 37 -->
**Answer:** `'Math Star'` as written. Both conditions match, and the final assignment wins. Swapping the last two lines yields `'Honor Roll'`.
<!-- end response 37 -->

**38.** (Short Answer) What does `pd.cut(df['score'], bins=[0, 70, 90, 101], labels=['Low', 'Mid', 'High'], right=False)` do, and why is it usually better than `.apply()` with an `if`/`elif` function for the same job?

<!-- response 38 -->
**Answer:** It returns a categorical Series assigning `Low` to `[0, 70)`, `Mid` to `[70, 90)`, and `High` to `[90, 101)`. Left endpoints are included; right endpoints are excluded. Missing scores and scores outside these bins receive missing labels. `pd.cut()` handles the whole Series with explicit boundaries and categorical output, avoiding a Python function call for every score.
<!-- end response 38 -->

**39.** (Short Answer) What's the difference between `df.query('math_score >= minimum')` and `df.query('math_score >= @minimum')`?

<!-- response 39 -->
**Answer:** Without `@`, `minimum` refers to a DataFrame column; if no such column exists, the query raises an undefined-variable error. `@minimum` refers to the external Python variable named `minimum`.
<!-- end response 39 -->

**40.** (Code Tracing) What does each line return, and why are they different?
```python
books = pd.Series(['C++ Primer', 'C Programming'])
books.str.contains('C++').tolist()
books.str.contains('C++', regex=False).tolist()
```

<!-- response 40 -->
**Answer:** The first returns `[True, True]`: the default regex search interprets `+` as a quantifier, so the pattern matches `C` in both strings (Python 3.11+ accepts `++` as a possessive quantifier). The second returns `[True, False]` because `regex=False` searches for the literal substring `C++`.
<!-- end response 40 -->

---

## Section F — Grouping and Combining

**41.** (Code Tracing) What does this return?
```python
df = pd.DataFrame({'team': ['A', 'B', 'A', 'B'], 'points': [10, 4, 20, 6]})
df.groupby('team')['points'].mean()
```

<!-- response 41 -->
**Answer:** A Series indexed by `team`, named `points`, with `A: 15.0` and `B: 5.0` (float64). These are `(10 + 20) / 2` and `(4 + 6) / 2`.
<!-- end response 41 -->

**42.** (Short Answer) Write a `groupby` with `.agg()` that gives, for each `team`, the number of rows and the total `points`, as columns named `games` and `total`.

<!-- response 42 -->
**Answer:** `df.groupby('team', as_index=False).agg(games=('points', 'size'), total=('points', 'sum'))`. `size` counts rows even if `points` is missing. For question 41's data: A has games 2 and total 30; B has games 2 and total 10.
<!-- end response 42 -->

**43.** (Short Answer) When would you use `pd.concat()` instead of `.merge()`? What does `ignore_index=True` do?

<!-- response 43 -->
**Answer:** Use `pd.concat([df1, df2], ignore_index=True)` to stack compatible tables vertically, such as two batches with the same columns. `.merge()` joins related rows by key values. With vertical concatenation, `ignore_index=True` replaces the original row labels with a fresh index `0, 1, ..., n-1`.
<!-- end response 43 -->

**44.** (Short Answer) In `orders.merge(prices, on='product_id', how='left')`, what happens to an order whose `product_id` isn't in `prices`? What would `how='inner'` do instead? And why does a merge on state codes fail when one table uses `'tx'` and the other uses `'TX'`?

<!-- response 44 -->
**Answer:** A left join keeps the unmatched order and fills its added price-table fields with missing values. An inner join drops that unmatched order. String key matching is case-sensitive, so `'tx'` and `'TX'` do not match; standardize both keys, for example with `.str.strip().str.upper()`, before merging.
<!-- end response 44 -->

**45.** (Short Answer) In Titanic, `groupby('Pclass').size()` gives 216 for 1st class, but `groupby('Pclass')['Age'].count()` gives 186. Why are they different?

<!-- response 45 -->
**Answer:** `.size()` counts all 216 first-class passenger rows, while `['Age'].count()` counts only the 186 non-missing ages. The other 30 first-class passengers have missing ages.
<!-- end response 45 -->

**46.** (Short Answer) `purchases` has 6 rows. After `purchases.merge(buyers, on='buyer_id', how='left')`, it has 8. What probably happened, and how can `validate=` protect you?

<!-- response 46 -->
**Answer:** A matched `buyer_id` probably appears more than once in `buyers`, creating multiple output rows for some purchases. Use `purchases.merge(buyers, on='buyer_id', how='left', validate='many_to_one')` to require unique keys in `buyers`; pandas raises `MergeError` if that expectation fails. Inspect and resolve duplicate buyer records before retrying.
<!-- end response 46 -->

---

## Section G — Going Further (Bonus)

**47.** (Short Answer) What do the `usecols` and `nrows` arguments to `pd.read_csv()` do, and when would you reach for them?

<!-- response 47 -->
**Answer:** `usecols=[...]` loads only the chosen columns. `nrows=N` reads only the first N data rows, excluding the header. Use them to reduce memory and load time, or to inspect a manageable preview of a large file; a first-N preview is not a random sample. Example: `pd.read_csv('ufo.csv', usecols=['state', 'country'], nrows=500)`.
<!-- end response 47 -->
