# Hash Map / Dictionary

## Creating a HashMap

```python
# Empty dictionary
d = {}
d = dict()

# Dictionary with initial values
d = {"a": 1, "b": 2, "c": 3}

# Dictionary from list of tuples
d = dict([("a", 1), ("b", 2)])

# Dictionary using comprehension
d = {x: x * 2 for x in range(5)}  # {0: 0, 1: 2, 2: 4, 3: 6, 4: 8}

# Default dictionary (auto-initializes missing keys)
from collections import defaultdict
d = defaultdict(int)   # defaults to 0
d = defaultdict(list)  # defaults to []

# Counter (for frequency counting)
from collections import Counter
d = Counter([1, 1, 2, 3, 3, 3])  # {3: 3, 1: 2, 2: 1}
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Insert | O(1) average |
| Delete | O(1) average |
| Lookup | O(1) average |
| Iteration | O(n) |

### Python Implementations

#### Insert - O(1) average

```python
def insert(d, key, value):
    d[key] = value
```

#### Delete - O(1) average

```python
def delete(d, key):
    if key in d:
        del d[key]

# Or with default return
def delete_with_return(d, key):
    return d.pop(key, None)
```

#### Lookup - O(1) average

```python
def lookup(d, key):
    return d.get(key)  # returns None if not found

def lookup_with_default(d, key, default):
    return d.get(key, default)
```

#### Check Existence - O(1) average

```python
def exists(d, key):
    return key in d
```

#### Iterate - O(n)

```python
def iterate_keys(d):
    for key in d:
        print(key)

def iterate_values(d):
    for value in d.values():
        print(value)

def iterate_items(d):
    for key, value in d.items():
        print(key, value)
```

#### Count Frequency - O(n)

```python
def count_frequency(arr):
    freq = {}
    for item in arr:
        freq[item] = freq.get(item, 0) + 1
    return freq

# Or using Counter
from collections import Counter
def count_frequency(arr):
    return Counter(arr)
```

#### Two Sum Pattern (Find Complement) - O(n)

```python
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []
```

---

## What It Provides

- Key-value storage
- Fast lookups by key
- Frequency counting
- Complement/pair finding

## What It Requires

- Hashable keys
- Extra O(n) space

## Good For

- Counting occurrences
- Finding complements (Two Sum pattern)
- Caching/memoization
- Grouping by property
- Quick existence checks

## Use When You Need

- "Have I seen this before?"
- "What's the count/frequency?"
- "Find the pair/complement"
- O(1) lookup instead of O(n) search
