# 📝 Worksheet: 03b - Containers → Functions

Do this worksheet **on paper, without a computer**. The point is to practice being the computer. Each section ends with an **🤖 Explain It** prompt: write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: Trace a Loop

Fill in the table for this code:

```python
temps = [31, 45, 28, 52]
total = 0
count = 0
for t in temps:
    total += t
    if t <= 32:
        count += 1
```

| pass | `t` | `total` | `count` |
|------|-----|---------|---------|
| start | — | 0 | 0 |
| 1 | 31 | 31 | 1 |
| 2 | 45 | 76 | 1 |
| 3 | 28 | 104 | 2 |
| 4 | 52 | 156 | 2 |

**Learner-reported paper trace:** Inuka supplied the completed table above during the guided paper exercise.

Which **two** patterns are mixed together in this loop?<br>
`Answer:` The loop combines **accumulation** and **conditional counting**. `total` adds every temperature. `count` increases only when `t <= 32`, which is true for `31` and `28`.

> 🤖 **Explain It:** Explain the difference between Accumulate, Count, and Filter as if you were talking to someone who has never programmed.

**Inuka's paper explanation:** Think of checking four temperature readings by hand:

- **Accumulate** means “How much altogether?” Add all four readings to get `156`.
- **Count** means “How many fit the rule?” Two readings are 32 or below.
- **Filter** means “Which ones fit the rule?” Keep those two readings: `31` and `28`.

---

## 🧠 Section 2: Pick Your Weapon

| Scenario | Container | Why? |
|----------|-----------|------|
| Daily step counts for a month | List | It keeps the counts in day order, even when two days have the same count. |
| A playing card (rank, suit) | Tuple | A card is a fixed pair. The first value is its rank and the second is its suit. |
| Username → password hash | Dictionary | You can use a username as the key to look up its stored hash. |
| Every distinct IP address in a log file | Set | Each address appears only once, even if it shows up repeatedly in the log. |
| Your class schedule, in order | List | It keeps classes in the order you attend them and lets you update the schedule when it changes. |

**Learner-reported paper response:** Inuka supplied the container choices and explanations above during the guided paper exercise.

> 🤖 **Explain It:** Pick the scenario you were *least* sure about and argue for a different container than the one you chose.

**Inuka's reflection:** I felt equally sure about all five.

**Alternative design example supplied by Inuka:** “I chose a list because I wanted to read my step counts in order. A dictionary keyed by date would also make sense. If I forgot to record Tuesday, I could still look up Wednesday’s count by its date.” This is an alternative-container comparison, not a report of uncertainty about that scenario.

---

## 🧠 Section 3: Take It Apart

```python
course = {
    "title": "CMPS 3603",
    "students": [
        {"name": "Ana", "scores": [88, 92]},
        {"name": "Ben", "scores": [75, 81]}
    ]
}
```

Write the value after **each** step:

1. `course["students"]` → `[{'name': 'Ana', 'scores': [88, 92]}, {'name': 'Ben', 'scores': [75, 81]}]`
2. `course["students"][1]` → `{'name': 'Ben', 'scores': [75, 81]}`
3. `course["students"][1]["scores"]` → `[75, 81]`
4. `course["students"][1]["scores"][0]` → `75`

**Learner-reported paper trace:** Inuka supplied all four values above during the guided paper exercise.

Write the expression that gets Ana's second score:<br>
`Answer:` `course["students"][0]["scores"][1]` gives `92`. The `[0]` selects Ana, and the `[1]` selects her second score.

---

## 🧠 Section 4: Functions

1. What prints?

```python
def f(x):
    return x + 1

print(f(f(f(0))))
```

   `Answer:` Inuka supplied this paper trace:

   1. Innermost call: `f(0)` returns `1`.
   2. Middle call: `f(1)` returns `2`.
   3. Outermost call: `f(2)` returns `3`.

   `print()` displays `3`.

2. What prints? Explain why.

```python
def shout(word):
    print(word.upper())

x = shout("hi")
print(x)
```

   `Answer:` Inuka supplied this paper prediction and explanation:

   ```text
   HI
   None
   ```

   `shout("hi")` prints `HI`. Since the function has no `return` statement, it returns `None`. That value is assigned to `x`, so `print(x)` prints `None` on the next line.

3. Circle the **parameters** and underline the **arguments**:

```python
def greet(name, greeting):
    return greeting + ", " + name

greet("Ada", "Hello")
```

**Inuka's paper markings:** Circle `name` and `greeting`. They’re the parameters in the function definition.

Underline `"Ada"` and `"Hello"`. They’re the arguments in the call: `"Ada"` goes to `name`, and `"Hello"` goes to `greeting`.

> 🤖 **Explain It:** In your own words, explain `print()` vs. `return`. Then explain why getting it wrong breaks a pipeline.

**Inuka's paper explanation:** `print()` shows a value on the screen. `return` sends a value back to the code that called the function. In a pipeline, one step’s result becomes the next step’s input. If the first step only prints `"HI"`, I can see `HI` on the screen, but the next step receives `None`. If it expects a string, it can fail.

---

## 🧠 Section 5: Contracts and Tests

Write a contract for a function `longest_word(words)`:

**Learner-reported paper contract:**

```text
IN: A list of strings.
OUT: The first longest string, or None if the list is empty.
DOES: Compares words by character count. If two words tie for longest, it keeps the one that appears first.
```

Write one test of each kind:

**Inuka's paper tests:**

| Test | Input | Expected result |
|---|---|---|
| Normal | `["cat", "tiger", "ox"]` | `"tiger"` |
| Boundary | `[]` | `None` |
| Weird (tie with an empty string present) | `["", "pear", "plum"]` | `"pear"` |

---

## 🧠 Section 6: Draw the Pipeline

> "Given a list of prices, drop any that are `0` or less, add 8.25% tax to each, then find the total."

1. Name each function you'd need.
2. For each one, write what goes **in** and what comes **out** (shape, not just "data").
3. Draw the pipeline with arrows, labeling each arrow with the data's shape.

> 🤖 **Explain It:** Why is a pipeline of small functions easier to fix than one big block of code?

**Pipeline design supplied by Inuka:**

| Function | Input | Output |
|---|---|---|
| `keep_positive_prices` | List of prices | List containing only prices greater than `0` |
| `add_tax` | List of positive prices | List of the same length, with each price multiplied by `1.0825` |
| `sum_prices` | List of taxed prices | One number: the total, or `0` if the list is empty |

```text
Start → (list of prices) → keep_positive_prices → (list of positive prices) → add_tax → (list of taxed prices) → sum_prices → (one numeric total)
```

**Generated explanation:** Each small function has one job, a defined input and a defined output. I can test the filtering, tax calculation and summation separately, then inspect the value between steps to find where an incorrect result first appears. For example, if nonpositive prices are removed correctly but the taxed list is wrong, the problem is in `add_tax`. Fixing that function is easier than searching through one large block that mixes all three jobs. Matching each output shape to the next input shape also helps catch mistakes such as passing a single total to a function that expects a list.

**Practice status:** Inuka supplied guided paper responses for Sections 1–5 and the Section 6 pipeline design. The final technical explanation was generated at his request. The paper drawing is unconfirmed; the generated explanation awaits learner review for the own-word requirement.
