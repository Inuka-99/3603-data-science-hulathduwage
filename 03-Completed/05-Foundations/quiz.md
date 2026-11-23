# 📝 Quiz: 05 - Foundations

45 questions covering all 8 Foundations notebooks, in order: magic commands, Jupyter workflow, getting help, Markdown, files and paths, data I/O, plotting with NumPy, and timing. Mix of multiple choice, true/false, code-tracing, and short answer.

This is a conceptual self-check. For hands-on practice writing and running real code, see `Foundations_Quiz.ipynb` in this folder.

Try every question on your own first. The Answer Key is at the bottom, no peeking. If you're using an AI tutor, paste in *your answer* and ask it to check your reasoning rather than asking it to solve the question first.

---

## Section A — Magic Commands (01)

**1.** (Multiple Choice) Which magic command shows your current working directory?
A) `%pwd`  B) `%cd`  C) `%ls`  D) `%dir`

**Answer:** A) `%pwd`.

**2.** (Short Answer) What's the difference between a line magic (`%pwd`), a cell magic (`%%writefile`), and a shell command (`!ls`)?

**Answer:** A line magic applies an IPython command to one line; a cell magic controls the entire cell and starts on its first line; `!` runs an operating-system shell command.

**3.** (Code Tracing) A folder contains only `a.csv` and `b.txt`. What kind of value is stored in `files`, and what does it contain?
```python
files = !ls
```

**Answer:** An IPython SList (list-like captured shell output), with the lines `a.csv` and `b.txt`.

**4.** (True/False) `%cd ..  # go up one folder` moves you to the parent folder.

**Answer:** False. IPython treats the inline comment as part of the directory argument. Put the comment on a separate line, then use `%cd ..`.

**5.** (Short Answer) Inside a notebook, why should you install packages with `%pip install` instead of `!pip install`?

**Answer:** `%pip` targets the active kernel environment; shell `pip` can target another Python installation.

**6.** (True/False) `%who` only shows variable *names*, while `%whos` also shows their types and a value summary.

**Answer:** True.


---

## Section B — Jupyter Workflow (02)

**7.** (Multiple Choice) In Command mode, which keyboard shortcut inserts a new cell *below* the current one?
A) `A`  B) `B`  C) `D D`  D) `M`

**Answer:** B) `B`.

**8.** (Short Answer) What's the practical difference between Command mode and Edit mode? You press `B` and the letter "b" appears in your code. What happened, and what should you press?

**Answer:** Command mode operates on cells; Edit mode edits text. The letter appeared because the cell was in Edit mode. Press Escape, then B.

**9.** (Code Tracing) What does this cell display when it runs?
```python
x = 5
x * 2
x * 3
```

**Answer:** `15`, because only the final expression is automatically displayed.

**10.** (Short Answer) A cell near the bottom of a notebook shows `[7]`, and the cell above it shows `[9]`. What does that tell you?

**Answer:** The bottom cell ran as execution 7, before the cell above was run as execution 9; page order and execution order differ.

**11.** (True/False) If you delete the cell that created the variable `message`, `message` is removed from memory immediately.

**Answer:** False. Deleting source does not delete existing kernel variables.

**12.** (Short Answer) Why should you **Restart & Run All** before submitting a notebook?

**Answer:** To check all saved cells work in order from an empty kernel without hidden state.


---

## Section C — Getting Help (03)

**13.** (Short Answer) `?` shows a docstring. What does `??` sometimes show that `?` doesn't, and why doesn't it always work?

**Answer:** `??` may show Python source code; compiled built-ins or unavailable source cannot always be displayed.

**14.** (Multiple Choice) The signature is `sorted(iterable, /, *, key=None, reverse=False)`. Which call is valid?
A) `sorted(iterable=nums)`  B) `sorted(nums, None, True)`  C) `sorted(nums, reverse=True)`  D) `sorted()`

**Answer:** C) `sorted(nums, reverse=True)`; the iterable is positional-only and reverse is keyword-only.

**15.** (Code Tracing) What error does this raise, and what does it mean?
```python
numbers = [1, 2, 3]
numbers.mean()
```

**Answer:** `AttributeError`: a Python list has no `mean` method. Use `sum(numbers)/len(numbers)` for a nonempty numeric list or a NumPy array.

**16.** (Short Answer) A long traceback fills the screen. Which line should you read first, and why?

**Answer:** Read the final exception line first: it names the error and message. Then inspect the relevant source frame above it.

**17.** (Short Answer) What does `dir(obj)` give you that Tab completion doesn't?

**Answer:** An inspectable list of attribute/method names, including special methods; it works in scripts and can be filtered programmatically without an editor popup.


---

## Section D — Markdown (04)

**18.** (Short Answer) What's the Markdown syntax for a level-2 heading (like `## Section 2`)?

**Answer:** Begin a line with `## `, for example `## Section 2`.

**19.** (Short Answer) How do you write **inline** LaTeX math in a Markdown cell, versus a **block** equation on its own line(s)?

**Answer:** Inline: `$x^2$`. Block: put `$$`, the equation, and `$$` on separate lines.

**20.** (Short Answer) The Markdown text `The item costs $5 and the tax is $2.` renders strangely. Why, and how do you fix it?

**Answer:** Dollar signs start math delimiters. Escape each price dollar sign: `The item costs \$5 and the tax is \$2.`

**21.** (Short Answer) You typed two lines directly under each other in a Markdown cell, but they render as **one** line. Name two ways to fix it.

**Answer:** Use `<br>` or two trailing spaces before the newline. A blank line also creates a separate paragraph.

**22.** (Short Answer) Why might you add narrative Markdown cells between code cells instead of just writing code comments?

**Answer:** Markdown provides rendered headings, rich text, links, tables, and equations to explain purpose and results to readers.


---

## Section E — Files and Paths (05)

**23.** (Code Tracing) What does this print?
```python
with open('x.txt', 'w', encoding='utf-8') as f:
    f.write('hi')

with open('x.txt', 'r', encoding='utf-8') as f:
    print(f.read())
```

**Answer:** `hi`.

**24.** (Multiple Choice) Which file mode adds to the end of an existing file **without** erasing it?
A) `'r'`  B) `'w'`  C) `'a'`  D) `'x'`

**Answer:** C) `'a'`.

**25.** (Code Tracing) What does this print?
```python
from pathlib import Path
p = Path('data') / 'sales_2026.csv'
print(p.name, p.stem, p.suffix)
```

**Answer:** `sales_2026.csv sales_2026 .csv`.

**26.** (Short Answer) Why is it good practice to use a relative path (like `'data/file.csv'`) instead of an absolute path (like `'C:/Users/yourname/...'`) in a notebook you'll share or submit?

**Answer:** Relative paths keep the project portable when its folder moves to a different computer, provided the same relative layout is kept.

**27.** (Code Tracing) `scores.csv` contains the two lines `Name,Score` and `Alice,90`. What does this print, and why might that cause a problem?
```python
import csv
with open('scores.csv', newline='', encoding='utf-8') as f:
    rows = list(csv.reader(f))
print(rows[1])
```

**Answer:** `['Alice', '90']`. CSV fields are text; convert the score to int or float before numeric calculations.

**28.** (True/False) After saving `{'point': (3, 4)}` with `json.dump` and reading it back with `json.load`, you get back exactly the same dictionary.

**Answer:** False. The tuple becomes a list: `{'point': [3, 4]}`.


---

## Section F — Data Input and Output (06)

**29.** (Short Answer) What does `pd.read_csv('file.csv')` return?

**Answer:** A pandas DataFrame.

**30.** (Multiple Choice) Which DataFrame method shows summary statistics (mean, standard deviation, min/max, etc.)?
A) `.head()`  B) `.info()`  C) `.describe()`  D) `.columns()`

**Answer:** C) `.describe()`.

**31.** (Short Answer) You save a DataFrame with `df.to_csv('out.csv')`, read it back, and find an extra `Unnamed: 0` column. What caused it, and how do you prevent it?

**Answer:** The saved index becomes an extra column. Write with `df.to_csv(path, index=False)` when the index is not part of the data.

**32.** (Short Answer) What does JSON written with `orient='records'` look like, and why is it usually the layout you want?

**Answer:** A JSON array containing one object per row, with column names as keys. This row-oriented layout is easy for APIs and other programs to consume.

**33.** (Short Answer) After `pd.read_csv`, the ZIP code `02108` shows up as `2108`. Why, and how do you fix it?

**Answer:** Numeric inference drops leading zeros. Read with `dtype={'Zip': str}` to preserve the code as text.

**34.** (Short Answer) What does `pd.read_excel('file.xlsx', sheet_name=None)` return?

**Answer:** A dictionary mapping sheet names to DataFrames, one per worksheet.


---

## Section G — Plotting with NumPy and Matplotlib (07)

**35.** (Code Tracing) What do these two lines print?
```python
print([1, 2] * 2)
print(np.array([1, 2]) * 2)
```

**Answer:** `[1, 2, 1, 2]` followed by `[2 4]`: lists repeat, while NumPy arrays multiply elementwise.

**36.** (Matching) Choose the best chart (line, bar, scatter, or histogram) for each question:
a) Which department sold the most?
b) How did daily website visits change over a month?
c) Is there a relationship between price and units sold?
d) What is the distribution of customer order values?

**Answer:** a) Bar. b) Line. c) Scatter. d) Histogram.

**37.** (Short Answer) A histogram and a bar chart both draw rectangles. What's the difference in what they show?

**Answer:** Histograms group numeric observations into ordered intervals to show a distribution; bars compare separate categories.

**38.** (Short Answer) You call `plt.show()` and then `plt.savefig('chart.png')`, and the saved image is blank. Why?

**Answer:** With the notebook backend, showing can finish/close the current figure, so the later pyplot save targets an empty figure. Save before show, or retain and save the intended Figure explicitly.

**39.** (Short Answer) On a box plot, what does the line **inside** the box represent, and what do the dots **beyond** the whiskers represent?

**Answer:** The line is the median; dots beyond the whiskers are potential outliers, typically beyond the 1.5-IQR fences, not automatically bad data.


---

## Section H — Timing and Performance (08)

**40.** (Short Answer) What's the difference between `%time` and `%timeit`, and why is `%timeit` more trustworthy for comparisons?

**Answer:** `%time` runs once; `%timeit` repeats over multiple runs and reports typical per-loop time and variability, reducing reliance on one noisy observation.

**41.** (Short Answer) Why is a NumPy vectorized operation like `arr ** 2` usually much faster than a Python `for` loop doing the same calculation element by element?

**Answer:** NumPy performs bulk work in compiled loops, avoiding Python-level dispatch for every element; fixed overhead can matter for tiny inputs.

**42.** (True/False) A variable created inside a `%%timeit` cell is available in the cells after it.

**Answer:** False. `%%timeit` uses a temporary timing scope.

**43.** (Short Answer) What's unfair about comparing `%timeit np.array(my_list) ** 2` against `%timeit arr ** 2` to decide whether squaring is fast?

**Answer:** The first includes list-to-array conversion and squaring; the second only squares. Create inputs outside timing to compare just the operation.

**44.** (Short Answer) Why is `[s / max(scores) for s in scores]` slow for large lists? How would you fix it, and roughly what happens to its runtime when the list doubles in size?

**Answer:** `max(scores)` rescans the list for every element, giving quadratic work; compute the maximum once before the comprehension. Doubling n roughly quadruples the slow version and doubles the corrected linear version.

**45.** (Multiple Choice) What does `%prun` show you?
A) Only the total time of the cell  B) How much time was spent in each function called  C) How much memory each variable uses  D) The source code of a function

**Answer:** B) How much time was spent in each function called.
