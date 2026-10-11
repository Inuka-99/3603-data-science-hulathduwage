# 📝 Worksheet: 01 - Working with Data

Use this worksheet to review and reinforce your understanding of Python's core data containers. Each section ends with an **🤖 Explain It** prompt — write your explanation in your own words, then (optionally) paste it into an AI tutor and ask it to point out anything you got wrong or left out.

---

## 🧠 Section 1: Lists

1. What method adds an item to the end of a list?  
   `Answer:` `.append(item)`.

2. How can you remove an item from a list by value? By position?  
   `Answer:` By value: `.remove(value)`. By position: `.pop(index)` or `del items[index]`.

3. What's the result of this code?

```python
nums = [2, 4, 6]
nums.append(8)
print(nums)
```

   `Answer:` `[2, 4, 6, 8]`.

4. What does `my_list[1:4]` return, given `my_list = [10, 20, 30, 40, 50]`?  
   `Answer:` `[20, 30, 40]`.

4a. Given `a = [1, 2]` and `b = [3, 4]`, what is the result of `a + b`? Of `a.append(b)`? Of `a.extend(b)`?  
   `Answer:` Starting fresh each time: + returns [1, 2, 3, 4] without mutation; append changes a to [1, 2, [3, 4]] and returns None; extend changes a to [1, 2, 3, 4] and returns None.

4b. Given `grid = [[1, 2], [3, 4]]`, how do you access the value `3`?  
   `Answer:` `grid[1][0]`.

4c. List three different ways to remove an item from a list.  
   `Answer:` `remove(value)`, `pop(index)`, and `del items[index]`.

---

### ✏️ Task: List Practice

```python
# Sample foods rather than claimed personal favorites.
foods = ['rice', 'pasta', 'apples']
foods.append('soup')
foods.remove('pasta')
print(foods)
```

### ✏️ Task: Slicing and Sorting

```python
numbers = [42, 17, 8, 99, 23, 4]
print(numbers[:3])
print(sorted(numbers))
print(sorted(numbers, reverse=True))
```

### ✏️ Task: Filtering

```python
temps = [55, 72, 90, 43, 88, 67, 101]
hot = []
for temp in temps:
    if temp > 85:
        hot.append(temp)
print(hot)
```

### ✏️ Task: Combine Lists Three Ways

```python
morning = ['eggs', 'toast']
extras = ['jam', 'coffee']
breakfast = morning + extras
print(breakfast, morning)
a = morning.copy()
a.append(extras)
print(a)  # Three items: the extras list is one nested item.
b = morning.copy()
b.extend(extras)
print(b)
```

### ✏️ Task: 2D List (grid)

```python
board = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(board[2][0])
board[1][1] = 0
for row in board:
    print(row)
```

### ✏️ Task: Deleting Items

```python
queue = ['Ana', 'Ben', 'Cy', 'Dana', 'Eve']
queue.remove('Cy')
served = queue.pop()
del queue[0]
print(queue, served)
```

### ✏️ Task: Iterate by Index

```python
prices = [10, 20, 30, 40]
for i in range(len(prices)):
    print(f'{i}: {prices[i]}')
for i in range(len(prices)):
    prices[i] += 5
print(prices)
for i, price in enumerate(prices):
    print(f'{i}: {price}')
```

### 🤖 Explain It

In your own words: what's the difference between a list and a slice of a list? Is slicing a list the same as modifying it? And when you write `a.append(b)` versus `a.extend(b)`, what ends up in `a` each way?

**Explanation:** A slice is a new shallow list containing selected element references. Slicing alone does not modify the original. append adds b as one element; extend adds each element from b.

---

## 🔒 Section 2: Tuples

5. What is a key difference between a list and a tuple?  
   `Answer:` Lists are mutable; tuple element positions cannot be reassigned.

6. Can you change the contents of a tuple once it is created? Why or why not?  
   `Answer:` Tuple element references cannot change, although a mutable object inside a tuple can still change internally.

7. What does `first, *rest = (10, 20, 30, 40)` assign to `first` and `rest`?  
   `Answer:` `first = 10`, `rest = [20, 30, 40]`.

---

### ✏️ Task: Tuple Practice

```python
# Sample number choices.
numbers = (3, 7, 12)
a, b, c = numbers
print(a)
print(b)
print(c)
```

### ✏️ Task: Unpacking with *rest

```python
race_times = (9.58, 9.63, 9.69, 9.71, 9.74)
winner, *others = race_times
print(winner)
print(others)
```

### ✏️ Task: Tuples as Dictionary Keys

```python
# Invented cities and distances for a dictionary-key example.
distances = {('City A', 'City B'): 120, ('City B', 'City C'): 75}
print(distances[('City A', 'City B')])
```

### 🤖 Explain It

In your own words: why does Python allow a tuple to be a dictionary key, but not a list? What property makes that possible?

**Explanation:** Dictionary keys must be hashable. A tuple of hashable elements has a stable hash; a mutable list is unhashable. A tuple containing a list is also unhashable.

---

## 🔑 Section 3: Dictionaries

8. What does the `.get()` method do differently from accessing a key directly with `[]`?  
   `Answer:` get returns a default (None if omitted) for a missing key; [] raises KeyError.

9. How do you loop through both keys and values in a dictionary?  
   `Answer:` `for key, value in data.items():`.

10. How would you remove a key from a dictionary and also capture the value it held?  
    `Answer:` `value = data.pop(key)`.

11. In a list of dictionaries like `people = [{'name': 'Ana'}, {'name': 'Ben'}]`, how do you get Ben's name?  
    `Answer:` `people[1]['name']`.

12. If the same dictionary object is stored in both a list and another dictionary, and you change it through one, does the other see the change? Why?  
    `Answer:` Yes. Both containers refer to the same dictionary object rather than independent copies.

---

### ✏️ Task: Dictionary Practice

```python
person = {'name': 'Sample Student', 'age': 21, 'hobby': 'reading'}
for key, value in person.items():
    print(f'{key}: {value}')
```

### ✏️ Task: Build from Two Lists

```python
products = ['pen', 'notebook', 'eraser']
prices = [1.50, 3.25, 0.75]
costs = dict(zip(products, prices))
print(sum(costs.values()))
```

### ✏️ Task: Nested Dictionaries

```python
inventory = {'apples': {'count': 50, 'price': 0.50}, 'bananas': {'count': 30, 'price': 0.25}}
for fruit, info in inventory.items():
    print(f"{fruit}: {info['count']} units at ${info['price']:.2f}")
```

### ✏️ Task: List of Dictionaries (table rows)

```python
roster = [{'name': 'Alex', 'major': 'CS'}, {'name': 'Ana', 'major': 'Math'}, {'name': 'Ben', 'major': 'History'}]
for student in roster:
    print(f"{student['name']} - {student['major']}")
roster.append({'name': 'Cy', 'major': 'CS'})
print([student['name'] for student in roster if student['major'] == 'CS'])
```

### ✏️ Task: Update a Record by Row Number

```python
by_row = {i: row for i, row in enumerate(roster)}
by_row[2]['major'] = 'CS'
print(roster[2])
# by_row[2] and roster[2] point to the same dictionary.
```

### 🤖 Explain It

In your own words: what's the difference between `student['gpa']` and `student.get('gpa')` when `'gpa'` isn't in the dictionary? Which would you use, and when? Also: why does changing `by_row[2]` also change `roster[2]`?

**Explanation:** [] raises KeyError when gpa is missing; get returns None or a supplied default. Use [] when the field must exist, get for an optional field. by_row[2] and roster[2] share the same dictionary object.

---

## 🚀 Section 4: Going Further (Optional)

These pair with the "🔥 Challenge" sections in the notebooks — skip if you haven't gotten there yet.

### ✏️ Task: List Comprehension

```python
cubes = [n ** 3 for n in range(6)]
print(cubes)
```

### ✏️ Task: namedtuple

```python
from collections import namedtuple
Book = namedtuple('Book', ['title', 'author'])
book = Book('Pride and Prejudice', 'Jane Austen')
print(book.title, book.author)
```

### ✏️ Task: Word Counter

```python
text = 'to be or not to be that is the question'
counts = {}
for word in text.split():
    counts[word] = counts.get(word, 0) + 1
print(counts)
from collections import Counter
assert counts == dict(Counter(text.split()))
```

### ✏️ Task: Parse Some JSON

```python
import json
raw = '{"course": "Programming for Data Science", "online": true, "instructor": null, "students": [{"name": "Alex", "grade": 91}, {"name": "Ana", "grade": 88}]}'
data = json.loads(raw)
print(data['course'], data['students'][1]['grade'])
print(type(data['online']), type(data['instructor']))
```

### ✏️ Task: Walk a GeoJSON FeatureCollection

```python
geo = {
    'type': 'FeatureCollection',
    'features': [
        {'type': 'Feature', 'geometry': {'type': 'Point', 'coordinates': [-98.529, 33.878]}, 'properties': {'name': 'Bolin Hall'}},
        {'type': 'Feature', 'geometry': {'type': 'Point', 'coordinates': [-98.531, 33.876]}, 'properties': {'name': 'Moffett Library'}},
    ],
}
for feature in geo['features']:
    lon, lat = feature['geometry']['coordinates']
    print(feature['properties']['name'], 'latitude:', lat, 'longitude:', lon)
```

---

## 🧾 Submit Checklist

- [ ] I practiced creating, slicing, sorting, and filtering lists.
- [ ] I can explain the difference between `+`, `append()`, and `extend()`.
- [ ] I built and traversed a nested (2D) list.
- [ ] I removed list items with `remove()`, `pop()`, and `del`.
- [ ] I looped by index with `range(len(...))` and with `enumerate()`.
- [ ] I understand how tuples are different from lists, and why that makes them hashable.
- [ ] I accessed, looped through, updated, and removed items from a dictionary.
- [ ] I built a dictionary from two separate lists.
- [ ] I worked with at least one nested dictionary.
- [ ] I processed a list of dictionaries as table rows and updated a record by row number.
- [ ] I parsed JSON with `json.loads()` and walked a GeoJSON FeatureCollection.
- [ ] I completed the "Explain It" prompts in my own words.
