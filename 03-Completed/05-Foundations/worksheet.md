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

The explanations below are **assistant drafts**, not Inuka-authored reflections. Inuka must review and rewrite each in their own words:

1. **Package environment:** Shell pip may install into a different Python than the active kernel. `%pip` uses the kernel's interpreter so installation and import target the same environment.
2. **Recipe and kitchen:** Saved cells are the recipe; kernel memory is the kitchen. A kitchen can contain leftovers from earlier steps, so a recipe that appears to work there may fail in a clean kitchen. Restarting and running in order tests the saved recipe.
3. **Help workflow:** Start with `?` for a signature/docstring, use `??` when Python source would help, `help()` in scripts, and `dir()` to discover available attributes. Consult official docs for detailed examples, behavior, or version-specific questions.
4. **Narrative:** Code comments explain implementation, while Markdown gives readers rendered headings, equations, tables, and interpretation. Generate Markdown when values should update with calculations so narrative stays consistent with results.
5. **CSV:** CSV encodes text, so csv.reader returns numeric-looking fields as strings. Its quote-aware parser preserves a comma inside a quoted name, while split(',') incorrectly splits that name.
6. **Conversion losses:** Excel-to-CSV loses workbook formatting and multiple-sheet structure. CSV type inference can remove leading zeros from identifiers; explicit string dtypes preserve them.
7. **Chart choice:** A line joins ordered positions, appropriate for continuous x or time. School subjects are separate categories without a meaningful connecting sequence, so bars fit them better.
8. **Timing:** Repetition estimates typical runtime and variability rather than trusting one noisy run. Measuring first identifies the actual bottleneck and avoids spending effort rewriting code that is already fast enough.
