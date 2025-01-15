

### 1. **Fractional Knapsack (Greedy Algorithm)**

```python
def fractional_knapsack(capacity, items):
    # Sort items by value-to-weight ratio in descending order
    items.sort(key=lambda x: x[1] / x[0], reverse=True)
    
    total_value = 0
    
    for weight, value in items:
        if capacity <= 0:
            break
            
        if weight <= capacity:
            total_value += value
            capacity -= weight
        else:
            total_value += value * (capacity / weight)
            capacity = 0
    
    return total_value
```

---

### 2. **0/1 Knapsack (Dynamic Programming)**

```python
def knapsack_01(capacity, items):
    n = len(items)
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]
    
    for i in range(1, n + 1):
        for w in range(capacity + 1):
            weight, value = items[i - 1]
            if weight <= w:
                dp[i][w] = max(dp[i - 1][w], dp[i - 1][w - weight] + value)
            else:
                dp[i][w] = dp[i - 1][w]
    
    return dp[n][capacity]
```

---

### 3. **Prim’s Algorithm (Minimum Spanning Tree)**

```python
import heapq

def prim(graph, start):
    n = len(graph)
    visited = [False] * n
    min_heap = [(0, start)]  # (weight, node)
    total_cost = 0
    
    while min_heap:
        weight, u = heapq.heappop(min_heap)
        
        if visited[u]:
            continue
        
        visited[u] = True
        total_cost += weight
        
        for v, w in graph[u]:
            if not visited[v]:
                heapq.heappush(min_heap, (w, v))
    
    return total_cost
```

---

### 4. **Kruskal’s Algorithm (Minimum Spanning Tree)**

```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n
    
    def find(self, u):
        if self.parent[u] != u:
            self.parent[u] = self.find(self.parent[u])
        return self.parent[u]
    
    def union(self, u, v):
        root_u, root_v = self.find(u), self.find(v)
        if root_u != root_v:
            if self.rank[root_u] > self.rank[root_v]:
                self.parent[root_v] = root_u
            elif self.rank[root_u] < self.rank[root_v]:
                self.parent[root_u] = root_v
            else:
                self.parent[root_v] = root_u
                self.rank[root_u] += 1

def kruskal(graph, n):
    edges = []
    for u in range(n):
        for v, weight in graph[u]:
            edges.append((weight, u, v))
    edges.sort()
    
    uf = UnionFind(n)
    mst_cost = 0
    
    for weight, u, v in edges:
        if uf.find(u) != uf.find(v):
            uf.union(u, v)
            mst_cost += weight
    
    return mst_cost
```

---

### 5. **Dijkstra’s Algorithm (Shortest Path)**

```python
import heapq

def dijkstra(graph, start):
    n = len(graph)
    dist = [float('inf')] * n
    dist[start] = 0
    min_heap = [(0, start)]
    
    while min_heap:
        d, u = heapq.heappop(min_heap)
        
        if d > dist[u]:
            continue
        
        for v, weight in graph[u]:
            if dist[u] + weight < dist[v]:
                dist[v] = dist[u] + weight
                heapq.heappush(min_heap, (dist[v], v))
    
    return dist
```

---

### 6. **Bellman-Ford Algorithm (Shortest Path)**

```python
def bellman_ford(graph, start):
    n = len(graph)
    dist = [float('inf')] * n
    dist[start] = 0
    
    for _ in range(n - 1):
        for u in range(n):
            for v, weight in graph[u]:
                if dist[u] + weight < dist[v]:
                    dist[v] = dist[u] + weight
    
    # Check for negative weight cycles
    for u in range(n):
        for v, weight in graph[u]:
            if dist[u] + weight < dist[v]:
                print("Graph contains negative weight cycle")
                return None
    
    return dist
```

---

### 7. **Floyd-Warshall Algorithm (All-Pairs Shortest Path)**

```python
def floyd_warshall(graph):
    n = len(graph)
    dist = [[float('inf')] * n for _ in range(n)]
    
    for u in range(n):
        dist[u][u] = 0
        for v, weight in graph[u]:
            dist[u][v] = weight
    
    for k in range(n):
        for i in range(n):
            for j in range(n):
                if dist[i][j] > dist[i][k] + dist[k][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
    
    return dist
```

---

### 8. **Warshall’s Algorithm (Reachability Matrix)**

```python
def warshall(graph):
    n = len(graph)
    reach = [[False] * n for _ in range(n)]
    
    for u in range(n):
        reach[u][u] = True
        for v in graph[u]:
            reach[u][v] = True
    
    for k in range(n):
        for i in range(n):
            for j in range(n):
                reach[i][j] = reach[i][j] or (reach[i][k] and reach[k][j])
    
    return reach
```

---

Each algorithm is designed for specific problems:
- **Knapsack**: Solves optimization problems for selecting items under weight constraints.
- **Prim’s and Kruskal’s**: Find Minimum Spanning Tree for graph optimization.
- **Dijkstra’s and Bellman-Ford**: Solve shortest path problems (Dijkstra for positive weights, Bellman-Ford for negative weights).
- **Floyd-Warshall and Warshall’s**: Find shortest paths between all pairs and determine reachability between all nodes.

