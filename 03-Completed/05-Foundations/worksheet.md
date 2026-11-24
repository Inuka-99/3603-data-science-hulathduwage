# 📝 Worksheet: 06 - Foundations

Use this worksheet to reinforce the Jupyter/IPython tooling skills from this module. There's one section per notebook, in order. Each section ends with an **🤖 Explain It** prompt. Write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧙 Section 1: Magic Commands (01)

1. What magic command lists every variable currently in memory, along with its type?<br>
   `Answer:` `%whos`.

2. What's the difference between a line magic (`%pwd`), a cell magic (`%%writefile`), and a shell command (`!ls`)?<br>
   `Answer:` A line magic handles one line, a cell magic handles a whole cell, and `!` invokes the operating-system shell.

3. Why does `%cd ..  # go up` fail, and how do you fix it?<br>
   `Answer:` The inline comment is interpreted as part of the folder name. Put the comment on its own line above `%cd ..`.

---

### ✏️ Task: Write, Run, and Reload

```python
# Use %%writefile to create tools.py containing a function shout(text)
# that returns text in uppercase with "!" on the end.
# Turn on %load_ext autoreload and %autoreload 2, then import tools and call shout().
# Rewrite tools.py so shout() adds "!!!" instead, and call it again WITHOUT restarting.
```

### 🤖 Explain It

In your own words: why can `!pip install` "succeed" while `import` still fails with `ModuleNotFoundError`? Why does `%pip` avoid the problem?

---

## ⚡ Section 2: Jupyter Workflow (02)

4. What are the two Jupyter cell modes, and what key switches to each?<br>
   `Answer:` Command mode: Escape. Edit mode: Enter.

5. What do the numbers in `[3]`, `[4]`, `[12]` next to code cells tell you, and what *don't* they tell you?<br>
   `Answer:` They show execution order within a kernel session, not physical cell order or whether the notebook works from a fresh kernel.

6. A cell's code ends with three expressions on three lines. How many of their values are displayed?<br>
   `Answer:` Only the final expression is displayed automatically; use print/display to show the others.

---

### ✏️ Task: Shortcut Drill

```
Using only the keyboard (no mouse):
- Insert 2 new cells below this one.
- Turn one into a Markdown cell and the other into a Code cell.
- Move the Code cell above the Markdown cell.
- Delete the Markdown cell, then undo the deletion.
- Run the Code cell.
```

### ✏️ Task: Break It, Then Fix It

```python
# In three separate cells, IN THIS ORDER, type:
#   print(area)
#   width, height = 4, 5
#   area = width * height
# Get it to work by running cells out of order. Then Restart & Run All,
# watch it fail, and fix the ORDER so it runs top to bottom.
```

### 🤖 Explain It

In your own words, using the "recipe and kitchen" idea: why can a notebook look correct on your screen and still fail for your grader?

---

## 📚 Section 3: Getting Help (03)

7. What's the difference between `help(len)` and `len?`? Which one also works in a plain `.py` script?<br>
   `Answer:` `help(len)` prints Python help and works in scripts; `len?` is an IPython inspection command, often displayed in a pager.

8. In the signature `round(number, ndigits=None)`, which argument is required and which is optional? What's the optional one's default?<br>
   `Answer:` `number` is required; `ndigits` is optional with default None.

9. Name the error type for each: `'5' + 5`, `int('hello')`, `[1, 2][5]`, `{'a': 1}['b']`.<br>
   `Answer:` `TypeError`, `ValueError`, `IndexError`, and `KeyError`, respectively.

---

### ✏️ Task: Investigate Without Searching

```python
# Using only ?, Tab/IntelliSense, dir(), and help() (no web searching):
# 1. Find a string method that checks whether a string contains only digits.
# 2. Use a wildcard search (np.*sum*?) to list NumPy functions with "sum" in the name.
# 3. Find out whether np.random.randint's upper limit is included. Prove it with code.
```

### 🤖 Explain It

In your own words: when would you reach for `?` versus `??` versus `help()` versus `dir()` versus the official docs? Is there a natural order you'd try them in?

---

## 📝 Section 4: Markdown (04)

10. What's the difference between `*italic*` and `**bold**` in Markdown?<br>
    `Answer:` Single asterisks render emphasis (italic); double asterisks render strong emphasis (bold).

11. Write the Markdown for a 2-item bulleted list where the second item has its own sub-bullet.<br>
    `Answer:` See the rendered mini-report cell in Worksheet_Practice.ipynb for a two-item list with a nested second item.

12. How do you show a literal price like `$5` in Markdown without it turning into math?<br>
    `Answer:` Escape the dollar sign: `\$5`.

---

### ✏️ Task: Mini Report

```markdown
# Write a Markdown cell with:
# - a level-2 heading
# - a short paragraph with a line break in the middle
# - a 3-item list
# - one inline LaTeX expression (try the mean, \bar{x})
# - a small table with a right-aligned number column
```

### 🤖 Explain It

In your own words: what's lost if you write an entire notebook as code + comments only, with no Markdown cells at all? When would *generating* Markdown from code (`display(Markdown(...))`) be better than typing it?

---

## 📂 Section 5: Files and Paths (05)

13. What does the `with` keyword do when you open a file, and why is it preferred over a plain `open()`/`.close()` pair?<br>
    `Answer:` `with` closes the file on leaving the block, including when an exception occurs, making cleanup reliable.

14. What's the difference between modes `'w'`, `'a'`, and `'x'`?<br>
    `Answer:` `w` creates/truncates, `a` creates/appends, and `x` exclusively creates and raises FileExistsError if the path exists.

15. For `Path('reports') / 'final.pdf'`, what are the `.name`, `.stem`, `.suffix`, and `.parent`?<br>
    `Answer:` `final.pdf`, `final`, `.pdf`, and `reports`.

---

### ✏️ Task: Build, Save, Reload

```python
# Create a dictionary describing yourself (name, major, hobbies as a list).
# Save it to a JSON file with indent=2 (use pathlib to build the path).
# Read it back into a NEW variable and confirm it matches the original with ==.
# Then add a tuple to the dictionary and repeat. Does it still match? Why not?
```

### ✏️ Task: Find Files

```python
# Write three small .txt files into a folder using a loop.
# Use glob('*.txt') to find them WITHOUT typing their names, and print each
# file's name and size in bytes.
```

### 🤖 Explain It

In your own words: why does `csv.reader` give you `'90'` instead of `90`, and why does splitting a CSV line on `','` break on a value like `"Smith, John"`?

---

## 📊 Section 6: Data Input and Output (06)

16. Name three things `.info()` tells you about a DataFrame that `.head()` doesn't.<br>
    `Answer:` Column dtypes, full-column non-null counts, and memory usage.

17. What does `index=False` do in `df.to_csv(...)`, and what happens if you forget it?<br>
    `Answer:` It omits the row index. Otherwise a default index is typically reloaded as an Unnamed: 0 data column.

18. When would you use `pd.json_normalize()` instead of `pd.read_json()`?<br>
    `Answer:` Use json_normalize to flatten nested records into columns, rather than leaving dictionaries inside cells.

---

### ✏️ Task: CSV Round Trip

```python
# Create a small DataFrame from a dictionary of lists (use pd.DataFrame(your_dict)).
# Save it to a CSV, then read that CSV back into a new DataFrame.
# Use .equals() to confirm the reloaded DataFrame matches the original.
```

### ✏️ Task: Convert Between Formats

```python
# Take the same DataFrame and save it as JSON (orient='records') and as Excel.
# Read the Excel file back and convert it to a CSV.
# Print the raw text of the JSON and CSV files and compare them.
```

### 🤖 Explain It

In your own words: what information can get lost or changed when converting Excel → CSV, or CSV → DataFrame? Give two examples.

---

## 📈 Section 7: Plotting with NumPy (07)

19. What's the difference between `[1, 2, 3] * 2` and `np.array([1, 2, 3]) * 2`?<br>
    `Answer:` The list repeats to [1, 2, 3, 1, 2, 3]; the array doubles elementwise to [2, 4, 6].

20. What does `plt.legend()` require in order to show meaningful labels (hint: think about the `plot()` calls before it)?<br>
    `Answer:` Give each plotted series a meaningful label, such as plot(x, y, label="Observed"), then call legend().

21. Which chart would you use for: comparing categories, change over time, a relationship between two numbers, and the distribution of one number?<br>
    `Answer:` Categories: bar; time: line; numeric relationship: scatter; numeric distribution: histogram.

---

### ✏️ Task: Compare Three Categories

```python
# Given: subjects = ["Math", "Science", "History"]
#        hours_studied = [5, 8, 3]
# Build a bar plot with a title and axis labels (with units).
# Save it to a PNG file, then display it.
```

### ✏️ Task: Distribution

```python
# Generate 200 test scores with np.random.normal(75, 10, size=200).
# Plot a histogram and mark the mean with a vertical dashed line and a legend.
# Then show the same data as a box plot side by side, using subplots.
```

### 🤖 Explain It

In your own words: why does a line plot make sense for `sin(x)` or monthly revenue but not for the categories `"Math"`, `"Science"`, `"History"`? What's different about the two kinds of data?

---

## ⏱️ Section 8: Timing and Performance (08)

22. What's the difference between `%time`, `%timeit`, `%%time`, and `%%timeit`?<br>
    `Answer:` `%time` times one line once; `%timeit` repeats one line. `%%time` times an entire cell once; `%%timeit` repeats the cell.

23. Name two things that make a timing comparison **unfair**.<br>
    `Answer:` Different input sizes/results, or including setup/conversion for only one version.

24. What does `%prun` tell you that `%timeit` doesn't?<br>
    `Answer:` `%prun` attributes runtime to called functions, revealing bottlenecks; `%timeit` measures the whole statement repeatedly.

---

### ✏️ Task: Timing Comparison

```python
# Build a list of the first 500,000 integers, and a NumPy array of the same.
# Use %timeit -o to compare squaring the list with a comprehension
# vs. squaring the array (numbers ** 2).
# Confirm both give the same values, then print how many times faster NumPy is.
```

### ✏️ Task: Find the Repeated Work

```python
# This function is slow. Time it, find the repeated work, fix it, and time it again:
def above_average(values):
    return [v for v in values if v > sum(values) / len(values)]
```

### 🤖 Explain It

In your own words: why does `%timeit` run your code many times instead of just once like `%time`? And why should you "measure first" instead of rewriting code that just *looks* slow?

---

## 🧾 Submit Checklist

- [ ] I used at least 3 different magic commands, including one cell magic and one `!` shell command.
- [ ] I fixed a notebook that only worked when run out of order, and I can explain why it failed.
- [ ] I ran **Restart & Run All** on my notebooks before submitting.
- [ ] I used `?`, `help()`, or `dir()` to look something up instead of guessing.
- [ ] I wrote a Markdown cell with a heading, a list, a table, and LaTeX math.
- [ ] I wrote and read back a text file, a JSON file, and a CSV file using `pathlib` paths.
- [ ] I loaded data with Pandas and converted it between at least two formats.
- [ ] I built at least one plot with a title, axis labels, and (if applicable) a legend, and saved it to a file.
- [ ] I timed two approaches fairly with `%timeit`.
- [ ] I uploaded each notebook's `NN-OutputFiles` folder along with the notebook.
- [ ] I completed the "Explain It" prompts in my own words.

## Worked task support and participation status

The companion [Worksheet_Practice.ipynb](Worksheet-Support/Worksheet_Practice.ipynb) executes the independent tasks in a fresh project `.venv` kernel. Its generated files are in `Worksheet-OutputFiles/`. The break/fix exercise is demonstrated programmatically; no keyboard-only activity or personal learning attestation is claimed. Original submit-checklist boxes remain unchecked for Inuka to confirm.

Pending hands-on task: perform Section 2's keyboard-only Shortcut Drill: insert two cells, change their types, move the Code cell, delete/undo the Markdown cell, and run the Code cell. For Section 3, perform the requested literal Tab/IntelliSense interaction; the companion uses help, wildcard inspection, and dir programmatically.

The following are **generated explanations completing the eight written prompts**. They are not claims of learner authorship or hands-on participation. The original personal attestations above remain unchecked.

1. **Package environment:** `!pip install` asks the operating-system shell to run whichever `pip` its PATH finds. That executable can belong to a different Python environment from the notebook kernel, so installation can succeed while the kernel still cannot import the package. `%pip` runs pip through the active kernel's interpreter, aligning the installation environment with that kernel. It addresses this environment mismatch; an incorrect import name, failed installation, or a required kernel restart can still cause an import problem.

2. **Recipe and kitchen:** The saved notebook cells are the recipe; the running kernel and its variables are the kitchen. A kitchen can contain leftovers from cells run earlier, edited, deleted, or run out of order. An output may also remain on screen after its code changes. The notebook can therefore look correct while depending on state that is absent from the grader's fresh kernel. Restarting clears that state, and running every cell from top to bottom checks whether the saved recipe creates its own dependencies in the right order.

3. **Help workflow:** Use `?` for a quick signature and docstring when deciding how to call an object. Use `??` when the Python implementation might explain its behavior; source is not always available for compiled functions. Use ordinary `help()` in a Python terminal or script, and `dir()` when the problem is discovering an object's attribute or method names. Official documentation is the next step for fuller examples, edge cases, or behavior specific to the installed version. A useful order is discover with completion or `dir()`, inspect with `?` or `help()`, and then consult source or official docs when the question needs more detail; there is no mandatory order for every problem.

4. **Narrative:** Code comments help explain implementation, but code cells alone lose the notebook's rendered report structure: headings, readable tables, equations, links, and prose explaining the purpose and limitations of results. Markdown lets a reader understand the analysis without deciphering every statement. Generated Markdown with `display(Markdown(...))` is useful for a sentence or table that includes computed values, because rerunning the calculation updates the narrative too. Stable background explanations and section headings are usually clearer as ordinary Markdown cells.

5. **CSV:** CSV stores fields as text and does not declare Python numeric types, so `csv.reader` normally returns a field such as `'90'` as a string. Convert it explicitly with `int()` or `float()` when its meaning is numeric; keep identifiers as text when their formatting matters. A proper CSV reader understands delimiters inside quoted fields: `"Smith, John",90` contains a name and a score. Plain `split(',')` ignores those quotes and incorrectly splits the name into two fields.

6. **Conversion losses:** First, Excel-to-CSV preserves one table of plain cell values, not the workbook's multiple sheets, formulas as formulas, formatting, charts, or other spreadsheet structure. A formula may survive only as an available cached result. Second, CSV-to-DataFrame inference can change meaning: an identifier such as `00123` may become integer `123`, losing its leading zeros, or a text placeholder such as `NA` may become a missing value. Use explicit dtypes and missing-value rules when loading, and compare the converted data with the original rather than assuming a round trip preserves everything.

7. **Chart choice:** Connecting points implies an order and a meaningful path between neighboring x-values. That is appropriate for `sin(x)` over an ordered numerical axis or monthly revenue over time, where sequence and change matter. `Math`, `Science`, and `History` are separate nominal categories with no intrinsic numerical distance or necessary sequence. A line would imply a trend that depends on an arbitrary category order; bars compare their values directly without making that connection.

8. **Timing:** A single `%time` result can be affected by operating-system activity, timer resolution, caching, or startup overhead. `%timeit` repeats the operation and reports timing information across repeated runs, giving a more stable comparison and exposing variability; it does not guarantee identical results on every machine or run. Measuring first identifies which code actually costs time, so optimization effort targets a demonstrated bottleneck. Compare the same inputs and outputs, keep setup treatment consistent, and recheck correctness after a change: faster code is not an improvement if it computes a different result.
