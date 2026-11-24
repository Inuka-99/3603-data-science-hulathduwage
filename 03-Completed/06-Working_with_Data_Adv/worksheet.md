# 📝 Worksheet: 06 - Working with Data (Advanced)

Use this worksheet to reinforce Pandas Series/DataFrames and the core data-wrangling workflow: load, explore, select, clean, transform, sort/filter/search, group, and combine. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🐼 Section 1: Series and DataFrames

1. What's the difference between a Pandas `Series` and a `DataFrame`? How does a list of dictionaries (from Module 03) turn into one?<br>
   `Answer:` A Series is a one-dimensional labeled array; a DataFrame is a two-dimensional table with labeled rows and columns. `pd.DataFrame(list_of_dicts)` makes each dictionary a row and its keys column labels; absent keys become missing values.

2. If you add two `Series` together and a label appears in only one of them, what value do you get at that label, and why?<br>
   `Answer:` The result is missing (`NaN`) at that label because addition aligns labels, and there is no value from the other Series to add. `.add(other, fill_value=0)` can treat an absent operand as zero when appropriate.

---

### ✏️ Task: Series Basics

```python
# Create a Series from a dictionary mapping 4 of your classes to your grade in each.
# Print the Series, then print the average of all grades (hint: .mean()).
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# Series Basics: course names and numeric grades supplied by Inuka.
grades = pd.Series({
    'Advanced Data Structures': 96,
    'Programming Techniques': 70,
    'Network Security': 85,
    'Linear Algebra': 90,
}, name='Grade')
print(grades)
print('Average grade:', grades.mean())
assert grades.mean() == 85.25
```


### 🤖 Explain It

In your own words: how is a Pandas `Series` similar to a Python dictionary, and how is it similar to a list? What does it borrow from each?

**Inuka’s supplied response:** A pandas Series is like a dictionary because I can look up a value by its label, such as "Network Security" to get 85. It’s also like a list because the values stay in order, so .iloc[0] gives me the first grade.

---

## 📂 Section 2: Loading and Exploring

3. What does `df.info()` tell you that `df.describe()` doesn't?<br>
   `Answer:` `df.info()` reports column names, dtypes, non-null counts, index information, and memory usage. `df.describe()` reports summary statistics (numeric columns by default), rather than this structural overview.

4. If `df.isnull().sum()` shows `Age: 177`, what does that number mean?<br>
   `Answer:` There are 177 rows with a missing Age value; this is a count of missing entries in that column, not an age or a percentage.

5. In `titanic.csv`, what does **one row** represent, and which column identifies each row?<br>
   `Answer:` One row records one passenger. `PassengerId` identifies the passenger; the automatically generated DataFrame index is separate.

---

### ✏️ Task: First Look at a Dataset

```python
# Load pokemon.csv.
# Print its shape, its columns, and .describe() for just the numeric columns.
# Which column has the most missing values, if any?
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# First Look at a Dataset
print('Shape:', pokemon.shape)
print('Columns:', pokemon.columns.tolist())
print(pokemon.select_dtypes(include='number').describe().to_string())
missing = pokemon.isnull().sum()
print('Missing values:', missing.to_dict())
print('Most missing:', missing.idxmax(), int(missing.max()))
pokemon.info()
```


### 🤖 Explain It

In your own words: why is it worth running `.info()` and `.isnull().sum()` on a dataset *before* you start analyzing it, rather than jumping straight to the questions you actually care about?

**Inuka’s supplied response:** I’d run .info() to check what each column contains and whether pandas read it as the right type. Then .isnull().sum() tells me how many values are missing in each column. That helps me catch problems before I trust a calculation.

---

## 🎯 Section 3: Indexing and Selection

6. Rewrite this using `.loc[]` instead of bracket + `.iloc[]` mixed together — or explain why you can't mix them the way it's written:
```python
df.iloc[df['Age'] < 10]  # this is actually broken — why?
```
   `Answer:` Use `df.loc[df['Age'] < 10]`. The comparison produces a labeled Boolean Series; `.iloc` expects positional indexing and does not accept this index-bearing Series as a Boolean indexer. `.iloc[(df['Age'] < 10).to_numpy()]` would explicitly use a positional Boolean array.

7. What's wrong with `df[df['Age'] < 10 and df['Fare'] > 100]`, and how would you fix it?<br>
   `Answer:` Python `and` asks for one truth value from each whole Series, which is ambiguous. Use elementwise `&` with parentheses: `df[(df['Age'] < 10) & (df['Fare'] > 100)]`.

8. Rewrite `df[(df['Pclass'] == 1) | (df['Pclass'] == 2)]` with `.isin()`. Why is `.isin()` easier to read when there are five values to match instead of two?<br>
   `Answer:` `df[df['Pclass'].isin([1, 2])]`. A list of five acceptable values is easier to scan and maintain than five repeated comparisons joined with `|`.

---

### ✏️ Task: Titanic Slicing

```python
# Using titanic.csv:
# 1. Select passengers in 3rd class (Pclass == 3) who survived (Survived == 1).
# 2. Of those, show only the Name, Age, and Fare columns.
# 3. Sort the result by Fare, descending.
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# Titanic Slicing
third_class_survivors = titanic.loc[
    (titanic['Pclass'] == 3) & (titanic['Survived'] == 1),
    ['Name', 'Age', 'Fare'],
].sort_values('Fare', ascending=False)
print(third_class_survivors.to_string(index=False))
third_class_survivors.to_csv(OUT / 'third_class_survivors.csv', index=False)
assert third_class_survivors['Fare'].is_monotonic_decreasing
```


### 🤖 Explain It

In your own words: why does `df.iloc[df['Age'] < 10]` not work, when `df.loc[df['Age'] < 10]` and `df[df['Age'] < 10]` both do?

**Inuka’s supplied response:** df['Age'] < 10 returns a Series of True and False values indexed by row label. Both .loc and df[...] accept that Series as a filter. .iloc works by position, so it needs the boolean values as an array, like df.iloc[(df['Age'] < 10).to_numpy()].

---

## 🧼 Section 4: Cleaning

9. If a column has the values `['25', 'thirty', '35']`, what happens when you run `pd.to_numeric(col, errors='coerce')` on it?<br>
   `Answer:` It converts the valid strings to numbers and replaces 'thirty' with `NaN`: `[25.0, NaN, 35.0]`. The usual resulting dtype is float because it accommodates NaN.

10. When would you choose `.dropna()` over `.fillna()`, and vice versa?<br>
   `Answer:` Use `.dropna(subset=[...])` when required fields are missing and those records cannot support the intended analysis. Use `.fillna(...)` when a justified replacement is available and keeping the record is useful. A replacement should reflect the field and analysis; filling unknown numeric measurements with zero can distort results.

11. A survey stores missing ages as `-1`. Why is that *worse* for analysis than a blank (`NaN`), and what one-line fix turns them into real missing values?<br>
   `Answer:` -1 looks like a real numeric observation and incorrectly affects averages, minima, and filters. Use `df['Age'] = df['Age'].replace(-1, float('nan'))`.

12. Two rows share an `order_id` but have different amounts. Will `df.drop_duplicates()` remove one? What argument makes it compare only `order_id`?<br>
   `Answer:` No: by default all columns are compared, so different amounts make the rows distinct. `df.drop_duplicates(subset=['order_id'])` compares only the ID and keeps the first by default; first decide which amount should be retained.

---

### ✏️ Task: Clean a Column

```python
# Using ufo.csv:
# 1. Check .isnull().sum() for the whole dataset.
# 2. Pick the column with the most missing values.
# 3. Decide (and justify in a comment) whether dropping or filling makes more
#    sense for that specific column, then do it.
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# Clean a Column
missing_ufo = ufo.isnull().sum()
print(missing_ufo.to_string())
most_missing = missing_ufo.idxmax()
clean_ufo = ufo.copy()
# Country is categorical. Keep sightings with unknown country for overall
# reporting; use an explicit category rather than guessing a country or
# discarding records. Exclude Unknown when computing actual country rates.
clean_ufo[most_missing] = clean_ufo[most_missing].fillna('Unknown')
print('Filled column:', most_missing)
print('Filled entries:', int(missing_ufo[most_missing]))
assert clean_ufo[most_missing].isna().sum() == 0
assert len(clean_ufo) == len(ufo)
pd.DataFrame({'missing_before': missing_ufo,
              'missing_after': clean_ufo.isnull().sum()}).to_csv(OUT / 'ufo_missing_audit.csv')
```


### 🤖 Explain It

In your own words: why might dropping rows with missing data be a bad idea if a large fraction of your dataset has at least one missing value somewhere?

**Inuka’s supplied response:** Dropping every row with a missing value could throw away a lot of useful data. If older respondents are more likely to skip one question, dropping those rows could make the remaining sample look younger than the original.

---

## 🧱 Section 5: Column Operations, Sorting, and Filtering

13. What's the difference between `df.rename(columns={'a': 'b'})` and `df.columns = ['b', 'c', 'd']`?<br>
   `Answer:` `.rename(columns={'a': 'b'})` changes only the specified label and returns a DataFrame unless assigned or used with `inplace=True`. Assigning `df.columns = ['b', 'c', 'd']` replaces every label in positional order and requires exactly as many labels as columns.

14. Rewrite this bracket-filter as a `.query()` call:
```python
df[(df['math_score'] >= 80) & (df['science_score'] >= 80)]
```
   `Answer:` `df.query('math_score >= 80 and science_score >= 80')`.

15. If `status` is a brand-new column, what do the rows with `score >= 70` contain after `df.loc[df['score'] < 70, 'status'] = 'review'`? How do you give every row a default first?<br>
   `Answer:` Those rows have a missing status (`NaN`) because the assignment only writes to rows below 70. Initialize first with `df['status'] = 'ok'`, then run the conditional assignment to mark low scores as 'review'.

---

### ✏️ Task: Build a Feature

```python
# Using students.csv:
# 1. Create a "total_score" column (math + science).
# 2. Sort by total_score, descending.
# 3. Print just the top 3 students' first_name and total_score.
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# Build a Feature
students['total_score'] = students['math_score'] + students['science_score']
top_three = students.sort_values('total_score', ascending=False)[['first_name', 'total_score']].head(3)
print(top_three.to_string(index=False))
top_three.to_csv(OUT / 'top_three_students.csv', index=False)
```


### ✏️ Task: Loop vs. Vectorized

```python
# Using students.csv:
# 1. Build a list of each student's total score with an .itertuples() loop.
# 2. Compute the same totals with one whole-column expression.
# 3. Confirm they match, then use %timeit to compare the two.
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# Loop vs. Vectorized
loop_totals = [row.math_score + row.science_score for row in students.itertuples(index=False)]
vector_totals = students['math_score'] + students['science_score']
assert loop_totals == vector_totals.tolist()
print('All', len(loop_totals), 'totals match.')
%timeit -r 3 -n 100 [row.math_score + row.science_score for row in students.itertuples(index=False)]
%timeit -r 3 -n 100 students['math_score'] + students['science_score']
```


### 🤖 Explain It

In your own words: what does "feature engineering" mean in the context of `total_score` or `average_score` — why create a new column instead of just computing the value fresh every time you need it?

**Inuka’s supplied response:** Feature engineering means using existing data to create a useful new column. For example, I could calculate average_score from several test scores and then use that same column to sort students, filter results, or make a chart. That keeps the formula consistent.

---

## 🧩 Section 6: Grouping and Combining

16. Describe the three steps of `df.groupby('Pclass')['Survived'].mean()` (split, apply, combine) in plain words. What does the result tell you?<br>
   `Answer:` Split passengers into one group per Pclass, apply the mean to each group's 0/1 Survived values, then combine those means into a Series indexed by class. Each mean is that class's survival proportion; multiply by 100 for a percentage.

17. What's the difference between `pd.concat()` and `.merge()`, and between a `'left'` and an `'inner'` merge?<br>
   `Answer:` `pd.concat()` stacks objects along rows or columns, aligning the other axis by labels. `.merge()` joins rows using matching key values. A left merge retains every left-table row and supplies missing values for unmatched right fields; an inner merge retains only matches. Duplicate keys can produce multiple rows per key in either join.

---

### ✏️ Task: Survival by Group

```python
# Using titanic.csv:
# 1. Find the survival rate by Pclass, then by Pclass AND Sex together.
# 2. Use .agg() to show, per Embarked port: passengers, average Fare, survival rate.
# 3. .reset_index() the result and sort it by survival rate, highest first.
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# Survival by Group
print('Survival by class:')
print(titanic.groupby('Pclass')['Survived'].mean().to_string())
print('Survival by class and sex:')
print(titanic.groupby(['Pclass', 'Sex'])['Survived'].mean().to_string())
# Keep passengers with missing Embarked as an explicit NaN group.
port_summary = (titanic.groupby('Embarked', dropna=False)
    .agg(passengers=('PassengerId', 'size'), average_Fare=('Fare', 'mean'),
         survival_rate=('Survived', 'mean'))
    .reset_index().sort_values('survival_rate', ascending=False))
print(port_summary.to_string(index=False))
assert port_summary['passengers'].sum() == len(titanic)
port_summary.to_csv(OUT / 'survival_by_port.csv', index=False)
```


### ✏️ Task: Join Two Tables

```python
# Build a table of 5 students (student_id, name) and a table of 4 grades
# (student_id, grade), where one student has no grade.
# Merge them with how='left' and with how='inner'. How many rows does each give, and why?
```

Runnable solution (execute the support notebook in order; setup loads the CSV files):

```python
# Join Two Tables: invented students and grades, not personal course grades.
student_table = pd.DataFrame([
    {'student_id': 1, 'name': 'Sample Alex'},
    {'student_id': 2, 'name': 'Sample Blair'},
    {'student_id': 3, 'name': 'Sample Casey'},
    {'student_id': 4, 'name': 'Sample Drew'},
    {'student_id': 5, 'name': 'Sample Emery'},
])
grade_table = pd.DataFrame({'student_id': [1, 2, 3, 4], 'grade': [85, 92, 78, 88]})
left_result = student_table.merge(grade_table, on='student_id', how='left', validate='one_to_one')
inner_result = student_table.merge(grade_table, on='student_id', how='inner', validate='one_to_one')
print('LEFT:', len(left_result), 'rows; preserves all five students.')
print(left_result.to_string(index=False))
print('INNER:', len(inner_result), 'rows; only four students have matching grades.')
print(inner_result.to_string(index=False))
assert len(left_result) == 5 and len(inner_result) == 4
left_result.to_csv(OUT / 'sample_students_left_join.csv', index=False)
inner_result.to_csv(OUT / 'sample_students_inner_join.csv', index=False)
```


### 🤖 Explain It

In your own words: when you merge UFO sightings (state codes like `'tx'`) with populations (codes like `'TX'`), every state fails to match at first. Why, and what does that teach you about checking keys *before* you join?

**Inuka’s supplied response:** 'tx' and 'TX' look like the same state to me, but pandas treats them as different strings. Before merging, I’d trim extra spaces and convert both state columns to uppercase. Afterward, I’d check which states still didn’t match.

---

## 🧾 Submit Checklist

- [ ] I created a `Series` and a `DataFrame` from Python containers (a dictionary or a list of dictionaries).
- [ ] I loaded a local CSV into a DataFrame and inspected it with `.info()` and `.describe()`.
- [ ] I used both `.loc[]` and `.iloc[]` at least once each.
- [ ] I filtered a DataFrame using a compound condition (`&` or `|`).
- [ ] I cleaned at least one column with `.fillna()`, `.dropna()`, or `pd.to_numeric()`.
- [ ] I created a new column and sorted by it.
- [ ] I removed duplicate rows or replaced a placeholder value with `NaN`.
- [ ] I filtered with `.isin()`, `.between()`, or `.str.contains()`.
- [ ] I used a whole-column (vectorized) calculation instead of a row-by-row loop.
- [ ] I summarized groups with `groupby()` (and `.agg()`), and combined tables with `pd.concat()` or `.merge()`.
- [ ] I completed the "Explain It" prompts in my own words.

## Execution evidence and personal review

Prepared for **Inuka Hulathduwage**. See [executed support notebook](Worksheet-Support/worksheet_support.ipynb) for setup, full results, assertions, and `%timeit` output. Run the notebook from its own folder; it reads the CSV files one folder above and writes its tables to `../Worksheet-OutputFiles`.

- Pokémon: 800 rows and 13 columns; `Type 2` has the most missing values (386).
- UFO: `country` has the most missing values (9,670). The explicit `Unknown` fill preserves sightings without inferring a country.
- Top total scores: Christopher 197, Danielle 195, Bridget 192.
- The sample left merge returns five rows; the inner merge returns four rows.
- The loop and vectorized totals match exactly. Timing results are recorded in the notebook and depend on the computer and run.
- The four course/grade pairs and all six Explain It responses were supplied by Inuka. The grade mean is 85.25.
- The original submission checklist is left unchecked for the student's personal review and attestation.
