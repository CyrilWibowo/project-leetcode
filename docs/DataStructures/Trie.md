# Trie (Prefix Tree)

## Creating a Trie

```python
# TrieNode class
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

# Trie class
class Trie:
    def __init__(self):
        self.root = TrieNode()

# Alternative: using defaultdict
from collections import defaultdict

class TrieNode:
    def __init__(self):
        self.children = defaultdict(TrieNode)
        self.is_end = False

# Alternative: using array for lowercase letters only
class TrieNode:
    def __init__(self):
        self.children = [None] * 26
        self.is_end = False

    def _char_to_index(self, char):
        return ord(char) - ord('a')
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Insert word | O(m) |
| Search word | O(m) |
| Search prefix | O(m) |
| Delete word | O(m) |
| Space | O(total characters) |

*where m = length of word*

### Python Implementations

#### Basic Trie Class

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True

    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end

    def starts_with(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
```

#### Insert - O(m)

```python
def insert(self, word):
    node = self.root
    for char in word:
        if char not in node.children:
            node.children[char] = TrieNode()
        node = node.children[char]
    node.is_end = True
```

#### Search - O(m)

```python
def search(self, word):
    node = self.root
    for char in word:
        if char not in node.children:
            return False
        node = node.children[char]
    return node.is_end
```

#### Starts With (Prefix Search) - O(m)

```python
def starts_with(self, prefix):
    node = self.root
    for char in prefix:
        if char not in node.children:
            return False
        node = node.children[char]
    return True
```

#### Delete Word - O(m)

```python
def delete(self, word):
    def _delete(node, word, depth):
        if not node:
            return False

        if depth == len(word):
            if not node.is_end:
                return False
            node.is_end = False
            return len(node.children) == 0

        char = word[depth]
        if char not in node.children:
            return False

        should_delete = _delete(node.children[char], word, depth + 1)

        if should_delete:
            del node.children[char]
            return len(node.children) == 0 and not node.is_end

        return False

    _delete(self.root, word, 0)
```

#### Get All Words - O(n) where n = total characters

```python
def get_all_words(self):
    words = []

    def dfs(node, path):
        if node.is_end:
            words.append(''.join(path))
        for char, child in node.children.items():
            path.append(char)
            dfs(child, path)
            path.pop()

    dfs(self.root, [])
    return words
```

#### Autocomplete (Words with Prefix) - O(m + n)

```python
def autocomplete(self, prefix):
    node = self.root
    for char in prefix:
        if char not in node.children:
            return []
        node = node.children[char]

    words = []

    def dfs(curr_node, path):
        if curr_node.is_end:
            words.append(prefix + ''.join(path))
        for char, child in curr_node.children.items():
            path.append(char)
            dfs(child, path)
            path.pop()

    dfs(node, [])
    return words
```

#### Count Words with Prefix - O(m + n)

```python
def count_words_with_prefix(self, prefix):
    node = self.root
    for char in prefix:
        if char not in node.children:
            return 0
        node = node.children[char]

    count = [0]

    def dfs(curr_node):
        if curr_node.is_end:
            count[0] += 1
        for child in curr_node.children.values():
            dfs(child)

    dfs(node)
    return count[0]
```

#### Trie with Count (for duplicates)

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.count = 0  # number of words ending here
        self.prefix_count = 0  # number of words with this prefix

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
            node.prefix_count += 1
        node.count += 1

    def count_word(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return 0
            node = node.children[char]
        return node.count

    def count_prefix(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return 0
            node = node.children[char]
        return node.prefix_count
```

#### Word Search in Board (Boggle) - O(m * n * 4^L)

```python
def find_words(board, words):
    # Build trie from words
    trie = Trie()
    for word in words:
        trie.insert(word)

    rows, cols = len(board), len(board[0])
    result = set()

    def dfs(r, c, node, path):
        if node.is_end:
            result.add(''.join(path))

        if r < 0 or r >= rows or c < 0 or c >= cols:
            return
        char = board[r][c]
        if char not in node.children:
            return

        board[r][c] = '#'  # mark visited
        next_node = node.children[char]
        path.append(char)

        for dr, dc in [(0, 1), (0, -1), (1, 0), (-1, 0)]:
            dfs(r + dr, c + dc, next_node, path)

        path.pop()
        board[r][c] = char  # restore

    for r in range(rows):
        for c in range(cols):
            dfs(r, c, trie.root, [])

    return list(result)
```

#### Longest Common Prefix - O(n * m)

```python
def longest_common_prefix(words):
    if not words:
        return ""

    trie = Trie()
    for word in words:
        trie.insert(word)

    prefix = []
    node = trie.root

    while len(node.children) == 1 and not node.is_end:
        char = list(node.children.keys())[0]
        prefix.append(char)
        node = node.children[char]

    return ''.join(prefix)
```

#### Search with Wildcards (.) - O(m * 26^k)

```python
class WordDictionary:
    def __init__(self):
        self.root = TrieNode()

    def add_word(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True

    def search(self, word):
        def dfs(node, i):
            if i == len(word):
                return node.is_end

            char = word[i]
            if char == '.':
                for child in node.children.values():
                    if dfs(child, i + 1):
                        return True
                return False
            else:
                if char not in node.children:
                    return False
                return dfs(node.children[char], i + 1)

        return dfs(self.root, 0)
```

#### Replace Words (Dictionary) - O(n * m)

```python
def replace_words(dictionary, sentence):
    trie = Trie()
    for root in dictionary:
        trie.insert(root)

    def get_root(word):
        node = trie.root
        for i, char in enumerate(word):
            if char not in node.children:
                return word
            node = node.children[char]
            if node.is_end:
                return word[:i + 1]
        return word

    words = sentence.split()
    return ' '.join(get_root(word) for word in words)
```

---

## What It Provides

- Prefix-based search
- Autocomplete
- Dictionary operations

## What It Requires

- String/prefix operations
- Extra space for tree structure

## Good For

- Autocomplete systems
- Spell checker
- IP routing
- Word games (Boggle, Scrabble)
- Prefix matching

## Use When You Need

- "Does this prefix exist?"
- "Find all words with prefix X"
- String pattern matching
- Dictionary of words
