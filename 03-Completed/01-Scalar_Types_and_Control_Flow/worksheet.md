# 📝 Worksheet: 02 - Scalar Types and Control Flow

Use this worksheet to reinforce your understanding of variables, arithmetic, comparisons, and decision logic. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: Scalar Types and Casting

1. What is the output of the following code?

```python
x = 10
print(type(x))
```

   `Answer:` `<class 'int'>`.

2. What scalar type would best represent:
   - A person's name: `str`
   - Their age: `int`
   - Whether they passed a test: `bool`

3. Why does `int('21')` work, but `int('twenty-one')` raise an error?  
   `Answer:` '21' is valid decimal integer text; 'twenty-one' is not, so it raises ValueError.

---

### ✏️ Task: Type Practice

```python
age = 21
price = 3.5
name = 'Sample Student'
passed = True
for value in [age, price, name, passed]:
    print(value, type(value))
```

### ✏️ Task: Arithmetic

```python
hours_worked = 37
hourly_rate = 15.50
pay = hours_worked * hourly_rate
print(pay)
print(round(pay, 2))
```

### ✏️ Task: Casting Round Trip

```python
user_input = '3.14159'
print(round(float(user_input), 2))
```

### 🤖 Explain It

In your own words: why does `input()` always return a string, and why does that matter when you want to do math with what the user typed?

**Explanation:** input reads text without guessing its meaning. Convert numeric text to int or float before arithmetic; otherwise + may concatenate strings.

---

## 🔁 Section 2: Comparison Operators

4. What does the `!=` operator mean?

   `Answer:` Not equal to.

5. What will the following code print?

```python
a = 5
b = 3
print(a < b or b < 10)
```

   `Answer:` `True`.

6. What does `0 <= score <= 100` check, and how would you write the same thing *without* chaining?  
   `Answer:` `score` is inclusively between 0 and 100; `score >= 0 and score <= 100`.

---

### ✏️ Task: Comparison Practice

```python
temperature = 98.6
print(97.0 <= temperature <= 99.0)
print(temperature >= 97.0 and temperature <= 99.0)
```

### 🤖 Explain It

In your own words: what's the difference between `=` and `==` in Python? Why does mixing them up cause errors (or worse, silently wrong code)?

**If you've written C++:** explain why `0 <= score <= 100` is safe to write in Python but dangerous to write in C++. What does the C++ version actually evaluate to, and how would you fix it?

**Explanation:** = assigns a value; == compares values. Ordinary assignment cannot replace equality in a Python if condition. Python chains comparisons with a shared middle operand; C++ compares the first boolean result, converted to 0 or 1, against 100. Use && in C++.

---

## 🔀 Section 3: Control Flow

7. Write a conditional that prints "Pass" if a grade is >= 70, and "Fail" otherwise.

```python
grade = 75
if grade >= 70:
    print('Pass')
else:
    print('Fail')
```

8. What does `elif` allow you to do that separate `if` statements don't?  
   `Answer:` elif checks another condition only if prior branches failed; separate if statements can run several bodies.

9. What will this print?

```python
age = 16
has_ticket = False
print(age >= 13 and has_ticket)
```

   `Answer:` `False`.

---

### ✏️ Task: Multi-Branch Logic

```python
bmi = 22.5
if bmi < 18.5:
    print('Underweight')
elif bmi < 25:
    print('Normal')
elif bmi < 30:
    print('Overweight')
else:
    print('Obese')
```

### ✏️ Task: Multi-Line Branches

```python
cart_items = 3
member_since_days = 400
item_price = 20.00
subtotal = cart_items * item_price
if member_since_days >= 365:
    discount = subtotal * 0.15
    print(f'Discount: ${discount:.2f}')
    print(f'Final price: ${subtotal - discount:.2f}')
else:
    discount = 0
    print('No discount yet')
    print(f'Full price: ${subtotal:.2f}')
```

### ✏️ Task: Your Turn

Write a program that asks for the weather and prints:
- "Bring sunscreen" if it's sunny
- "Take an umbrella" if it's raining
- "Check the forecast" otherwise

```python
weather = input("Weather: ").strip().lower()
if weather == "sunny":
    print("Bring sunscreen")
elif weather in ("raining", "rainy"):
    print("Take an umbrella")
else:
    print("Check the forecast")
```

### 🤖 Explain It

In your own words: what's the difference between using `and` versus writing nested `if` statements to check two conditions? Do they always produce the same result?

**Explanation:** For a simple combined test, nested if statements and and both require both conditions and short-circuit the second test. Their behavior can differ when nested branches include other actions or separate else clauses.

---

## 🚀 Section 4: Going Further (Optional)

These pair with the "🔥 Challenge" sections in the notebooks — skip if you haven't gotten there yet.

### ✏️ Task: Conditional Expression

```python
temperature = 95
comfort = 'too hot' if temperature > 90 else 'fine'
print(comfort)
```

### ✏️ Task: Float Precision

```python
# Prediction: False because of binary floating-point rounding.
print(0.1 + 0.1 + 0.1 == 0.3)
print(abs((0.1 + 0.1 + 0.1) - 0.3) < 0.0001)
```

### ✏️ Task: Match Statement

```python
grade_letter = 'B'
match grade_letter:
    case 'A':
        print('Excellent')
    case 'B' | 'C':
        print('Good')
    case _:
        print('Needs improvement')
```

### 🤖 Explain It

**If you've written C++:** how is Python's `match`/`case` similar to a C++ `switch`? What can `match` do (strings, multiple values per case with `|`) that a plain C++ `switch` can't?

**Explanation:** Both select a branch by a value. match also accepts strings and structural patterns, and | combines alternatives. A plain C++ switch uses integral or enum cases and does not directly switch on strings.

---

## 🧾 Submit Checklist

- [ ] I practiced creating and casting each scalar type.
- [ ] I used arithmetic operators, including `//` and `%`.
- [ ] I wrote conditionals using comparison and logical operators.
- [ ] I used a chained comparison at least once.
- [ ] I wrote at least one branch with multiple lines inside it.
- [ ] I completed the "Explain It" prompts in my own words.
