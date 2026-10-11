# 📝 Quiz: 03b - Containers → Functions

24 questions covering container choice, the loop patterns, nested expressions, function basics, `print` vs. `return`, mutation, and pipelines. Mix of multiple choice, true/false, code-tracing, and short answer.

Try every question on your own first. The Answer Key is at the bottom, so don't peek. If you're using an AI tutor, paste in *your answer* and ask it to check your reasoning, rather than asking it to solve the question for you.

---

## Section A — Containers

**1.** (Short Answer) Why is `scores = [87, 91, 74]` better than `score1 = 87`, `score2 = 91`, `score3 = 74`? Give two reasons.

**Answer:** One variable groups all scores, and a loop can process any number of scores without adding separate variables or copied statements.

**2.** (Code Tracing) What prints?
```python
scores = [87, 91, 74, 88, 95]
scores.append(60)
scores.remove(91)
print(scores[1], scores[-1], len(scores))
```

**Answer:** `74 60 5`.

**3.** (Multiple Choice) Which container fits "Student ID → GPA" best?
A) list  B) tuple  C) dictionary  D) set

**Answer:** C: dictionary.

**4.** (Multiple Choice) Which container fits "an RGB color" best?
A) list  B) tuple  C) dictionary  D) set

**Answer:** B: tuple.

**5.** (Short Answer) Give a better description of a tuple than "an immutable list."

**Answer:** A fixed record with positions that have specific meanings, such as red, green and blue channels.

**6.** (Code Tracing) What prints?
```python
a = {"OOP", "Database", "Algorithms"}
b = {"Database", "Networks"}
print(a & b)
```

**Answer:** `{'Database'}`.

**7.** (Code Tracing) Evaluate one step at a time. What is the value?
```python
students = [
    {"name": "Alice", "grade": 91},
    {"name": "Bob",   "grade": 84}
]
students[-1]["name"][0]
```

**Answer:** students[-1] is Bob's dictionary; its name is 'Bob'; index 0 of that string is 'B'.


---

## Section B — Patterns

**8.** (Short Answer) Accumulate and Count both start at `0`. What's the difference in how they update?

**Answer:** Accumulate adds each value; Count adds one for each matching item.

**9.** (Code Tracing) What prints?
```python
nums = [4, -2, 7, -5, 3]
x = []
for n in nums:
    if n < 0:
        x.append(n)
print(x)
```

**Answer:** `[-2, -5]`.

**10.** (Multiple Choice) Which pattern is question 9?
A) Accumulate  B) Count  C) Filter  D) Best So Far

**Answer:** C: Filter.

**11.** (Short Answer) When finding the maximum with the Best So Far pattern, why should `best` start at the first item instead of `0`?

**Answer:** Zero is wrong for all-negative inputs and may not be in the data; the first item is a valid initial candidate.


---

## Section C — Function Basics

**12.** (Code Tracing) What prints when this cell runs?
```python
def square(x):
    return x * x
```

**Answer:** Nothing: the function is defined but not called.

**13.** (Short Answer) In `def area(width, height):` and `area(3, 5)`, which are the parameters and which are the arguments?

**Answer:** Parameters: width and height. Arguments: 3 and 5.

**14.** (Code Tracing) What prints?
```python
def square(x):
    return x * x

print(square(3) + square(square(2)))
```

**Answer:** `25`.

**15.** (Code Tracing) What prints? (Careful!)
```python
def double(x):
    print(x * 2)

result = double(5)
print(result)
```

**Answer:** `10`, then `None`, on separate lines.

**16.** (True/False) `print()` gives a value back to the program so it can be used in later calculations.

**Answer:** False: print displays text and normally returns None; use return to send the computed result back.

**17.** (Code Tracing) What prints?
```python
def check(x):
    return "big"
    return "small"

print(check(1))
```

**Answer:** `big`.

**18.** (Short Answer) Give three reasons functions are useful *besides* avoiding copy/paste.

**Answer:** Readable names, independent tests, and fixes in one place.


---

## Section D — Functions + Containers

**19.** (Short Answer) Find the bug:
```python
def total(numbers):
    result = 0
    for n in numbers:
        result += n
        return result
```

**Answer:** return is inside the loop, so only the first element is processed. Move return after the loop.

**20.** (Code Tracing) What prints?
```python
def add_one(values):
    values.append(1)
    return values

a = [5]
b = add_one(a)
print(a)
```

**Answer:** `[5, 1]`.

**21.** (Code Tracing) What prints?
```python
nums = [3, 1, 2]
x = nums.sort()
print(x, nums)
```

**Answer:** `None [1, 2, 3]`.

**22.** (Multiple Choice) `frequency(["a", "b", "a"])` from Notebook 05 turns a list into a...
A) number  B) bool  C) list  D) dictionary

**Answer:** D: dictionary.

**23.** (Short Answer) Write the contract (IN / OUT / DOES) for a function `count_above(numbers, threshold)`.

**Answer:** IN: a list of numbers and a numeric threshold. OUT: integer count. DOES: count values strictly greater than the threshold; empty input returns 0.

**24.** (Code Tracing) Given the functions from Notebook 06, what prints?
```python
numbers = [10, -3, 20, 30]
clean = remove_negatives(numbers)
print(above(clean, average(clean)))
```

**Answer:** `[30]`; clean is [10, 20, 30] and the mean is 20.

