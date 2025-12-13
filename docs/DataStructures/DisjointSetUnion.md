# Disjoint Set Union (Union-Find)

## Creating a Union-Find

```python
# Basic Union-Find
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

# Union-Find with size tracking
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.size = [1] * n
        self.count = n  # number of components

# Union-Find for arbitrary keys (not just 0 to n-1)
class UnionFind:
    def __init__(self):
        self.parent = {}
        self.rank = {}

    def add(self, x):
        if x not in self.parent:
            self.parent[x] = x
            self.rank[x] = 0
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Find | O(α(n)) ≈ O(1) |
| Union | O(α(n)) ≈ O(1) |
| Connected | O(α(n)) ≈ O(1) |
| Space | O(n) |

*α(n) = inverse Ackermann function, effectively constant*

### Python Implementations

#### Basic Union-Find Class

```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # path compression
        return self.parent[x]

    def union(self, x, y):
        px, py = self.find(x), self.find(y)
        if px == py:
            return False
        # union by rank
        if self.rank[px] < self.rank[py]:
            px, py = py, px
        self.parent[py] = px
        if self.rank[px] == self.rank[py]:
            self.rank[px] += 1
        return True

    def connected(self, x, y):
        return self.find(x) == self.find(y)
```

#### Find with Path Compression - O(α(n))

```python
def find(self, x):
    if self.parent[x] != x:
        self.parent[x] = self.find(self.parent[x])
    return self.parent[x]

# Iterative version
def find_iterative(self, x):
    root = x
    while self.parent[root] != root:
        root = self.parent[root]
    # path compression
    while self.parent[x] != root:
        next_x = self.parent[x]
        self.parent[x] = root
        x = next_x
    return root
```

#### Union by Rank - O(α(n))

```python
def union(self, x, y):
    px, py = self.find(x), self.find(y)
    if px == py:
        return False

    if self.rank[px] < self.rank[py]:
        px, py = py, px
    self.parent[py] = px
    if self.rank[px] == self.rank[py]:
        self.rank[px] += 1
    return True
```

#### Union by Size - O(α(n))

```python
def union(self, x, y):
    px, py = self.find(x), self.find(y)
    if px == py:
        return False

    if self.size[px] < self.size[py]:
        px, py = py, px
    self.parent[py] = px
    self.size[px] += self.size[py]
    self.count -= 1
    return True

def get_size(self, x):
    return self.size[self.find(x)]
```

#### Union-Find with Component Count

```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n
        self.count = n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        px, py = self.find(x), self.find(y)
        if px == py:
            return False
        if self.rank[px] < self.rank[py]:
            px, py = py, px
        self.parent[py] = px
        if self.rank[px] == self.rank[py]:
            self.rank[px] += 1
        self.count -= 1
        return True

    def get_count(self):
        return self.count
```

#### Connected Components - O(n * α(n))

```python
def count_components(n, edges):
    uf = UnionFind(n)
    for u, v in edges:
        uf.union(u, v)
    return uf.count

# Get all components
def get_components(n, edges):
    uf = UnionFind(n)
    for u, v in edges:
        uf.union(u, v)

    components = {}
    for i in range(n):
        root = uf.find(i)
        if root not in components:
            components[root] = []
        components[root].append(i)
    return list(components.values())
```

#### Cycle Detection (Undirected Graph) - O(E * α(n))

```python
def has_cycle(n, edges):
    uf = UnionFind(n)
    for u, v in edges:
        if uf.find(u) == uf.find(v):
            return True
        uf.union(u, v)
    return False
```

#### Redundant Connection - O(n * α(n))

```python
def find_redundant_connection(edges):
    n = len(edges)
    uf = UnionFind(n + 1)
    for u, v in edges:
        if not uf.union(u, v):
            return [u, v]
    return []
```

#### Kruskal's MST - O(E log E)

```python
def kruskal_mst(n, edges):
    # edges: [(weight, u, v), ...]
    edges.sort()
    uf = UnionFind(n)
    mst = []
    total_weight = 0

    for weight, u, v in edges:
        if uf.union(u, v):
            mst.append((u, v, weight))
            total_weight += weight
            if len(mst) == n - 1:
                break

    return mst, total_weight
```

#### Number of Islands (Union-Find approach) - O(m * n * α(m * n))

```python
def num_islands(grid):
    if not grid:
        return 0

    rows, cols = len(grid), len(grid[0])
    uf = UnionFind(rows * cols)
    count = sum(grid[r][c] == '1' for r in range(rows) for c in range(cols))

    def index(r, c):
        return r * cols + c

    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == '1':
                for dr, dc in [(0, 1), (1, 0)]:
                    nr, nc = r + dr, c + dc
                    if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] == '1':
                        if uf.union(index(r, c), index(nr, nc)):
                            count -= 1

    return count
```

#### Accounts Merge - O(n * k * α(n * k))

```python
def accounts_merge(accounts):
    uf = UnionFind(len(accounts))
    email_to_id = {}

    # Map emails to account index
    for i, account in enumerate(accounts):
        for email in account[1:]:
            if email in email_to_id:
                uf.union(i, email_to_id[email])
            email_to_id[email] = i

    # Group emails by root account
    from collections import defaultdict
    groups = defaultdict(set)
    for email, idx in email_to_id.items():
        groups[uf.find(idx)].add(email)

    # Build result
    return [[accounts[idx][0]] + sorted(emails)
            for idx, emails in groups.items()]
```

#### Largest Component by Common Factor - O(n * sqrt(max_val))

```python
def largest_component_size(nums):
    uf = UnionFind(max(nums) + 1)

    def get_factors(n):
        factors = []
        d = 2
        while d * d <= n:
            if n % d == 0:
                factors.append(d)
                while n % d == 0:
                    n //= d
            d += 1
        if n > 1:
            factors.append(n)
        return factors

    for num in nums:
        factors = get_factors(num)
        for f in factors:
            uf.union(num, f)

    from collections import Counter
    count = Counter(uf.find(num) for num in nums)
    return max(count.values())
```

#### Satisfiability of Equality Equations - O(n * α(26))

```python
def equations_possible(equations):
    uf = UnionFind(26)

    def char_to_idx(c):
        return ord(c) - ord('a')

    # Process equalities first
    for eq in equations:
        if eq[1] == '=':
            uf.union(char_to_idx(eq[0]), char_to_idx(eq[3]))

    # Check inequalities
    for eq in equations:
        if eq[1] == '!':
            if uf.find(char_to_idx(eq[0])) == uf.find(char_to_idx(eq[3])):
                return False

    return True
```

#### Union-Find for Strings/Arbitrary Keys

```python
class UnionFindMap:
    def __init__(self):
        self.parent = {}
        self.rank = {}

    def find(self, x):
        if x not in self.parent:
            self.parent[x] = x
            self.rank[x] = 0
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        px, py = self.find(x), self.find(y)
        if px == py:
            return False
        if self.rank[px] < self.rank[py]:
            px, py = py, px
        self.parent[py] = px
        if self.rank[px] == self.rank[py]:
            self.rank[px] += 1
        return True
```

---

## What It Provides

- Group membership tracking
- Connectivity checking
- Cycle detection

## What It Requires

- Disjoint set operations only
- Initial set of elements

## Good For

- Connected components
- Kruskal's MST algorithm
- Cycle detection in undirected graphs
- Dynamic connectivity

## Use When You Need

- "Are these in the same group?"
- "Merge these groups"
- Network connectivity
- Avoid cycles when adding edges
