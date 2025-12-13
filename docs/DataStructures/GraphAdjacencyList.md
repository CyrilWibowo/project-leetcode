# Graph (Adjacency List)

## Creating a Graph

```python
from collections import defaultdict

# Undirected graph using dict
graph = defaultdict(list)

def add_edge_undirected(graph, u, v):
    graph[u].append(v)
    graph[v].append(u)

# Directed graph
graph = defaultdict(list)

def add_edge_directed(graph, u, v):
    graph[u].append(v)

# Weighted graph (list of tuples)
graph = defaultdict(list)

def add_edge_weighted(graph, u, v, weight):
    graph[u].append((v, weight))
    graph[v].append((u, weight))  # remove for directed

# Graph from edge list
def build_graph(edges, directed=False):
    graph = defaultdict(list)
    for u, v in edges:
        graph[u].append(v)
        if not directed:
            graph[v].append(u)
    return graph

edges = [[0, 1], [0, 2], [1, 2], [2, 3]]
graph = build_graph(edges)

# Graph from adjacency list input
def build_from_adj_list(adj_list):
    graph = defaultdict(list)
    for i, neighbors in enumerate(adj_list):
        graph[i] = neighbors
    return graph
```

---

## Operations

| Operation | Time Complexity |
|-----------|-----------------|
| Add vertex | O(1) |
| Add edge | O(1) |
| Remove edge | O(E) |
| Check if edge exists | O(degree) |
| Get all neighbors | O(1) |
| Space | O(V + E) |

### Python Implementations

#### Add/Remove Vertex - O(1)

```python
def add_vertex(graph, v):
    if v not in graph:
        graph[v] = []

def remove_vertex(graph, v):
    if v in graph:
        del graph[v]
    for u in graph:
        graph[u] = [x for x in graph[u] if x != v]
```

#### Add/Remove Edge - O(1) / O(E)

```python
def add_edge(graph, u, v):
    graph[u].append(v)
    graph[v].append(u)

def remove_edge(graph, u, v):
    graph[u] = [x for x in graph[u] if x != v]
    graph[v] = [x for x in graph[v] if x != u]
```

#### Check Edge Exists - O(degree)

```python
def has_edge(graph, u, v):
    return v in graph[u]
```

#### BFS (Breadth-First Search) - O(V + E)

```python
from collections import deque

def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    result = []
    while queue:
        node = queue.popleft()
        result.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return result
```

#### DFS (Depth-First Search) - O(V + E)

```python
def dfs(graph, start):
    visited = set()
    result = []

    def explore(node):
        visited.add(node)
        result.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                explore(neighbor)

    explore(start)
    return result

# Iterative DFS
def dfs_iterative(graph, start):
    visited = set()
    stack = [start]
    result = []
    while stack:
        node = stack.pop()
        if node in visited:
            continue
        visited.add(node)
        result.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                stack.append(neighbor)
    return result
```

#### Shortest Path (Unweighted) - O(V + E)

```python
from collections import deque

def shortest_path(graph, start, end):
    if start == end:
        return [start]
    visited = set([start])
    queue = deque([(start, [start])])
    while queue:
        node, path = queue.popleft()
        for neighbor in graph[node]:
            if neighbor == end:
                return path + [neighbor]
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, path + [neighbor]))
    return []  # no path found

# Return distance only
def shortest_distance(graph, start, end):
    if start == end:
        return 0
    visited = set([start])
    queue = deque([(start, 0)])
    while queue:
        node, dist = queue.popleft()
        for neighbor in graph[node]:
            if neighbor == end:
                return dist + 1
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, dist + 1))
    return -1
```

#### Dijkstra's Algorithm (Weighted) - O((V + E) log V)

```python
import heapq

def dijkstra(graph, start):
    distances = {start: 0}
    heap = [(0, start)]

    while heap:
        dist, node = heapq.heappop(heap)
        if dist > distances.get(node, float('inf')):
            continue
        for neighbor, weight in graph[node]:
            new_dist = dist + weight
            if new_dist < distances.get(neighbor, float('inf')):
                distances[neighbor] = new_dist
                heapq.heappush(heap, (new_dist, neighbor))

    return distances

# With path reconstruction
def dijkstra_with_path(graph, start, end):
    distances = {start: 0}
    parent = {start: None}
    heap = [(0, start)]

    while heap:
        dist, node = heapq.heappop(heap)
        if node == end:
            break
        if dist > distances.get(node, float('inf')):
            continue
        for neighbor, weight in graph[node]:
            new_dist = dist + weight
            if new_dist < distances.get(neighbor, float('inf')):
                distances[neighbor] = new_dist
                parent[neighbor] = node
                heapq.heappush(heap, (new_dist, neighbor))

    # Reconstruct path
    path = []
    node = end
    while node is not None:
        path.append(node)
        node = parent.get(node)
    return path[::-1], distances.get(end, float('inf'))
```

#### Detect Cycle (Undirected) - O(V + E)

```python
def has_cycle_undirected(graph, n):
    visited = set()

    def dfs(node, parent):
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                if dfs(neighbor, node):
                    return True
            elif neighbor != parent:
                return True
        return False

    for i in range(n):
        if i not in visited:
            if dfs(i, -1):
                return True
    return False
```

#### Detect Cycle (Directed) - O(V + E)

```python
def has_cycle_directed(graph, n):
    WHITE, GRAY, BLACK = 0, 1, 2
    color = {i: WHITE for i in range(n)}

    def dfs(node):
        color[node] = GRAY
        for neighbor in graph[node]:
            if color[neighbor] == GRAY:
                return True
            if color[neighbor] == WHITE and dfs(neighbor):
                return True
        color[node] = BLACK
        return False

    for i in range(n):
        if color[i] == WHITE:
            if dfs(i):
                return True
    return False
```

#### Topological Sort (Kahn's Algorithm) - O(V + E)

```python
from collections import deque

def topological_sort(graph, n):
    in_degree = [0] * n
    for u in graph:
        for v in graph[u]:
            in_degree[v] += 1

    queue = deque([i for i in range(n) if in_degree[i] == 0])
    result = []

    while queue:
        node = queue.popleft()
        result.append(node)
        for neighbor in graph[node]:
            in_degree[neighbor] -= 1
            if in_degree[neighbor] == 0:
                queue.append(neighbor)

    return result if len(result) == n else []  # empty if cycle
```

#### Topological Sort (DFS) - O(V + E)

```python
def topological_sort_dfs(graph, n):
    visited = set()
    stack = []

    def dfs(node):
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                dfs(neighbor)
        stack.append(node)

    for i in range(n):
        if i not in visited:
            dfs(i)

    return stack[::-1]
```

#### Connected Components (Undirected) - O(V + E)

```python
def count_components(graph, n):
    visited = set()
    count = 0

    def dfs(node):
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                dfs(neighbor)

    for i in range(n):
        if i not in visited:
            dfs(i)
            count += 1

    return count

# Get all components
def get_components(graph, n):
    visited = set()
    components = []

    def dfs(node, component):
        visited.add(node)
        component.append(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                dfs(neighbor, component)

    for i in range(n):
        if i not in visited:
            component = []
            dfs(i, component)
            components.append(component)

    return components
```

#### Bipartite Check - O(V + E)

```python
from collections import deque

def is_bipartite(graph, n):
    color = [-1] * n

    for start in range(n):
        if color[start] != -1:
            continue
        queue = deque([start])
        color[start] = 0
        while queue:
            node = queue.popleft()
            for neighbor in graph[node]:
                if color[neighbor] == -1:
                    color[neighbor] = 1 - color[node]
                    queue.append(neighbor)
                elif color[neighbor] == color[node]:
                    return False
    return True
```

#### Find All Paths - O(V! in worst case)

```python
def find_all_paths(graph, start, end):
    paths = []

    def dfs(node, path):
        if node == end:
            paths.append(path[:])
            return
        for neighbor in graph[node]:
            if neighbor not in path:
                path.append(neighbor)
                dfs(neighbor, path)
                path.pop()

    dfs(start, [start])
    return paths
```

#### Clone Graph - O(V + E)

```python
def clone_graph(node):
    if not node:
        return None

    cloned = {}

    def dfs(n):
        if n in cloned:
            return cloned[n]
        copy = Node(n.val)
        cloned[n] = copy
        for neighbor in n.neighbors:
            copy.neighbors.append(dfs(neighbor))
        return copy

    return dfs(node)
```

---

## What It Provides

- Relationships between entities
- Network representation
- Path finding

## What It Requires

- Connections between nodes
- More space than adjacency matrix for sparse graphs

## Good For

- Social networks
- Dependencies
- State transitions
- Path finding
- Sparse graphs

## Use When You Need

- Model connections
- Find paths
- Explore relationships
- Graph is sparse (few edges)
