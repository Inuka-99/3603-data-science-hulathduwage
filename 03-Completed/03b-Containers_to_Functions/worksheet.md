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

Which **two** patterns are mixed together in this loop?  
`Answer:` Accumulate and Count.

> 🤖 **Explain It:** Explain the difference between Accumulate, Count, and Filter as if you were talking to someone who has never programmed.

**Explanation:** Accumulate adds the values, Count records how many match a condition, and Filter keeps the matching values in a new collection.

---

## 🧠 Section 2: Pick Your Weapon

| Scenario | Container | Why? |
|----------|-----------|------|
| Daily step counts for a month | list | Preserve daily order and repeated counts. |
| A playing card (rank, suit) | tuple | Two fixed fields describe one card. |
| Username → password hash | dictionary | Retrieve a hash by username. |
| Every distinct IP address in a log file | set | Keep unique addresses. |
| Your class schedule, in order | list | Preserve class order. |

> 🤖 **Explain It:** Pick the scenario you were *least* sure about and argue for a different container than the one you chose.

**Alternative:** A class schedule could be a dictionary keyed by day and time if fast lookup matters more than a simple ordered list. This compares designs without claiming a personal learning experience.

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

Write the expression that gets Ana's second score:  
`Answer:` `course["students"][0]["scores"][1]` gives 92.

---

## 🧠 Section 4: Functions

1. What prints?

```python
def f(x):
    return x + 1

print(f(f(f(0))))
```

   `Answer:` `3`: the nested calls return 1, then 2, then 3.

2. What prints? Explain why.

```python
def shout(word):
    print(word.upper())

x = shout("hi")
print(x)
```

   `Answer:` `HI`, then `None`: shout prints text but has no return statement.

3. Circle the **parameters** and underline the **arguments**:

```python
def greet(name, greeting):
    return greeting + ", " + name

greet("Ada", "Hello")
```

Parameters: `name`, `greeting`. Arguments: `"Ada"`, `"Hello"`.

> 🤖 **Explain It:** In your own words, explain `print()` vs. `return`. Then explain why getting it wrong breaks a pipeline.

**Explanation:** print displays a value for a person; return passes a value to the calling code. A print-only function gives the next pipeline step None rather than the data it expects.

---

## 🧠 Section 5: Contracts and Tests

Write a contract for a function `longest_word(words)`:

```text
IN: a list of strings
OUT: a string, or None for an empty list
DOES: return the longest word; first encountered wins a tie
```

Write one test of each kind:

- Normal: `longest_word(["cat", "elephant", "dog"]) == "elephant"`
- Boundary: `longest_word(["cat"]) == "cat"`
- Weird: `longest_word([]) is None`

---

## 🧠 Section 6: Draw the Pipeline

> "Given a list of prices, drop any that are `0` or less, add 8.25% tax to each, then find the total."

1. Name each function you'd need.
2. For each one, write what goes **in** and what comes **out** (shape, not just "data").
3. Draw the pipeline with arrows, labeling each arrow with the data's shape.

> 🤖 **Explain It:** Why is a pipeline of small functions easier to fix than one big block of code?

**Pipeline answer:**

| Function | Input | Output |
|---|---|---|
| positive_prices | list of numbers | list of numbers greater than 0 |
| add_tax | list of prices | list of prices multiplied by 1.0825 |
| total_prices | list of taxed prices | one numeric total |

```mermaid
flowchart TD
  A["Prices: list"] --> B[positive_prices]
  B -->|list of positive prices| C[add_tax]
  C -->|list of taxed prices| D[total_prices]
  D --> E["Total: number"]
```

**Explanation:** Each function has one job and can be checked separately. A wrong intermediate value shows which step needs fixing.

**Practice note:** These are typed worked answers. The requested independent paper exercise has not been performed here.
