# 📝 Worksheet: 03 - Strings and Text

Use this worksheet to reinforce your understanding of strings — creating them, slicing them, cleaning them up, and formatting them. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: String Basics

1. Why doesn't Python care whether you use `'...'` or `"..."`?  
   `Answer:` Both delimit the same str type; choose the delimiter that needs fewer escapes.

2. What's the output of this code?

```python
word = 'science'
print(word[0:3])
```

   `Answer:` `sci`.

3. Rewrite this string so it could be written with single quotes on the outside instead of double:

```python
message = "She said \"don't stop\""
```

   `Answer:` `message = 'She said "don\'t stop"'`.

---

### ✏️ Task: Slicing Practice

```python
course = 'Programming for Data Science'
print(course[16:20])
print(course[::-1])
```

### ✏️ Task: Multi-Line String

```python
"""Sample bio for demonstrating multiline strings."""
bio = """My name is Sample Student.
I study programming.
I enjoy solving problems."""
print(bio)
```

### 🤖 Explain It

In your own words: why are strings immutable, and what do you actually have to do if you want a "modified" version of a string?

**Explanation:** A string cannot be edited in place. Slicing and concatenation or a string method create a new string, which can be assigned back to the variable.

---

## 🔁 Section 2: String Methods

4. What's the difference between `.strip()` and `.replace(' ', '')`?  
   `Answer:` strip removes whitespace from the ends; replace(" ", "") removes ordinary spaces everywhere, including inside.

5. What will this print?

```python
name = "  ADA lovelace  "
print(name.strip().title())
```

   `Answer:` `Ada Lovelace`.

6. If `words = "red,green,blue".split(',')`, what is `words`, and what type is it?  
   `Answer:` `['red', 'green', 'blue']`, a list.

---

### ✏️ Task: Clean and Validate

```python
raw_input = '  YES  '
print(raw_input.strip().lower() == 'yes')
```

### ✏️ Task: Build a Sentence

```python
words = ['data', 'science', 'is', 'fun']
sentence = ' '.join(words)
print(sentence)
print(sentence.replace('fun', 'powerful'))
```

### 🤖 Explain It

In your own words: what's the difference between a method like `.upper()` that returns a new string, versus a list method like `.append()` that changes the list in place? Why do strings only work the first way?

**Explanation:** upper returns a new string and leaves the original unchanged. append mutates a list and returns None. String immutability rules out an append-style in-place operation.

---

## 🎯 Section 3: Formatted Strings

7. What does the format spec `:.2f` do?  
   `Answer:` Fixed-point formatting with two decimal places.

8. What will this print?

```python
item = "eraser"
qty = 5
print(f"You bought {qty} {item}(s)")
```

   `Answer:` `You bought 5 eraser(s)`.

9. Why might you use an f-string instead of `+` to build a string out of variables?  
   `Answer:` They insert values and expressions directly, avoiding explicit conversions and awkward concatenation.

---

### ✏️ Task: Formatted Receipt

```python
item = 'Backpack'
price = 45.999
qty = 2
print(f'{qty}x {item} @ ${price:.2f} = ${price * qty:.2f}')
```

### ✏️ Task: Aligned Table

```python
names = ['Ana', 'Bartholomew', 'Cy']
for name in names:
    print(f'{name:>15}')
```

### 🤖 Explain It

In your own words: what's the practical difference between `f'{price}'` and `f'{price:.2f}'` when `price = 19.999999`? When would the difference actually matter in real code?

**Explanation:** The first displays 19.999999; the second displays 20.00. Fixed decimal places make receipts readable, but formatting does not change the stored numeric value.

---

## 🚀 Section 4: Going Further (Optional)

These pair with the "🔥 Challenge" sections in the notebooks — skip if you haven't gotten there yet.

### ✏️ Task: Raw String

```python
path = r'C:\Users\you\Desktop\notes.txt'
print(path)
# Ordinary literals interpret backslashes as escapes, including newline or Unicode escapes.
```

### ✏️ Task: Debug Format Spec

```python
width = 10
height = 4
print(f'{width=}, {width * height=}')
```

---

## 🧾 Submit Checklist

- [ ] I created strings with single quotes, double quotes, and triple quotes.
- [ ] I indexed and sliced a string.
- [ ] I used at least three different string methods (`.strip()`, `.split()`, `.join()`, `.replace()`, etc.).
- [ ] I built an f-string with more than one embedded expression.
- [ ] I used a format spec to control decimal places or alignment.
- [ ] I completed the "Explain It" prompts in my own words.
