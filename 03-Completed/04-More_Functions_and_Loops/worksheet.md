# 📝 Worksheet: 04 - More Functions & Loops

Do this worksheet **on paper, without a computer**. Each section ends with an **🤖 Explain It** prompt: write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: Defaults and Keywords

```python
def price(amount, tax=0.0825, discount=0):
    return round(amount * (1 + tax) - discount, 2)
```

What does each call return?

1. `price(100)` → `108.25`
2. `price(100, discount=10)` → `98.25`
3. `price(100, 0)` → `100`
4. `price(discount=5, amount=20)` → `16.65`

> 🤖 **Explain It:** Why are keyword arguments easier to read than positional ones in a call like `price(100, 0, 10)`?

**Explanation:** Keywords name the purpose of each value, making tax=0 and discount=10 clearer than two unexplained numbers.

---

## 🧠 Section 2: Scope

What prints? Explain why.

```python
count = 0

def add_one(count):
    count = count + 1
    return count

result = add_one(count)
print(count, result)
```

`Answer:` `0 1`. The parameter is local; returning the incremented value does not reassign global count.

> 🤖 **Explain It:** Describe the "room with two doors" model of a function in your own words.

**Explanation:** Parameters bring data into the function; return sends the result out. Local names stay inside that scope.

---

## 🧠 Section 3: Trace a While Loop

```python
balance = 100
years = 0
while balance < 150:
    balance = balance + 20
    years += 1
```

| pass | `balance` at the start | `balance < 150`? | `balance` after | `years` after |
|------|------------------------|------------------|-----------------|---------------|
| 1 | 100 | True | 120 | 1 |
| 2 | 120 | True | 140 | 2 |
| 3 | 140 | True | 160 | 3 |
| 4 (condition only) | 160 | False | 160 (unchanged) | 3 (unchanged) |

Final `years`: **3**. Final `balance`: **160**.

What single change would make this an **infinite** loop?  
`Answer:` Remove the balance update (or replace +20 with +0), so balance stays below 150.

---

## 🧠 Section 4: `for` or `while`?

| Task | `for` or `while`? | Why? |
|------|-------------------|------|
| Print each line of a file | for | The file is directly iterable. |
| Keep asking for a password until it's correct | while | The number of attempts is unknown. |
| Find the average of a list of prices | for | Visit each price once. |
| Double a number until it's over one million | while | Stop when the numerical condition changes. |

---

## 🧠 Section 5: Files

Given the file `pets.txt`:

```text
name,species
Rex,dog

# rescued in May
Tom,cat
```

1. How many times does `for line in f:` run? **5**, including the blank and comment lines.
2. Which lines should your code skip, and how would you detect each one?  
   `Answer:` Strip each line, then skip empty text, text beginning with #, and the header name,species.
3. Write the list of dictionaries a `read_pets` function should return:  
   `Answer:` `[{'name': 'Rex', 'species': 'dog'}, {'name': 'Tom', 'species': 'cat'}]`.

> 🤖 **Explain It:** When is `try` / `except` a good idea, and when does it just hide bugs?

**Explanation:** Catch expected, recoverable cases such as FileNotFoundError. Catching every exception around a large block can conceal unrelated programming errors.

**Practice note:** These are typed worked answers. The requested independent paper exercise has not been performed here.
