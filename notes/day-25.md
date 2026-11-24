# Day 25 — Union-Find / Disjoint Set Union (DSU)

**Date:** November 25, 2026  
**Language:** Python  
**Topic:** Connected Components, Cycle Detection and Disjoint Sets  
**Status:** Study notes prepared — online-judge submissions not yet confirmed.

## 1. Concepts Learned

- Union-Find is also called Disjoint Set Union (DSU).
- It maintains a collection of non-overlapping groups.
- `find(x)` returns the representative (root) of the group containing `x`.
- `union(a, b)` joins the groups containing `a` and `b).
- Path compression makes future `find()` operations faster.
- Union by size attaches the smaller group to the larger group.
- A connected component is a set of vertices connected directly or indirectly.
- If both endpoints of an edge already have the same root, adding that edge creates a cycle.

## 2. Important Logic

### Basic DSU template

```python
parent = list(range(n))
size = [1] * n

def find(x):
    if parent[x] != x:
        parent[x] = find(parent[x])
    return parent[x]

def union(a, b):
    root_a = find(a)
    root_b = find(b)

    if root_a == root_b:
        return False

    if size[root_a] < size[root_b]:
        root_a, root_b = root_b, root_a

    parent[root_b] = root_a
    size[root_a] += size[root_b]
    return True
```

### Q1 — LeetCode: Redundant Connection

[Problem link](https://leetcode.com/problems/redundant-connection/)

For each edge, find the roots of both endpoints. If both roots are already equal, the edge connects vertices that are already connected, so it is redundant.

```python
class Solution:
    def findRedundantConnection(self, edges):
        n = len(edges)
        parent = list(range(n + 1))
        size = [1] * (n + 1)

        def find(x):
            if parent[x] != x:
                parent[x] = find(parent[x])
            return parent[x]

        def union(a, b):
            ra, rb = find(a), find(b)

            if ra == rb:
                return False

            if size[ra] < size[rb]:
                ra, rb = rb, ra

            parent[rb] = ra
            size[ra] += size[rb]
            return True

        for u, v in edges:
            if not union(u, v):
                return [u, v]
```

### Q2 — LeetCode: Number of Provinces

[Problem link](https://leetcode.com/problems/number-of-provinces/)

Initially, every city is its own group. Union directly connected cities. The number of distinct roots after all connections is the number of provinces.

```python
class Solution:
    def findCircleNum(self, isConnected):
        n = len(isConnected)
        parent = list(range(n))
        size = [1] * n

        def find(x):
            if parent[x] != x:
                parent[x] = find(parent[x])
            return parent[x]

        def union(a, b):
            ra, rb = find(a), find(b)

            if ra == rb:
                return

            if size[ra] < size[rb]:
                ra, rb = rb, ra

            parent[rb] = ra
            size[ra] += size[rb]

        for i in range(n):
            for j in range(i + 1, n):
                if isConnected[i][j] == 1:
                    union(i, j)

        return sum(1 for i in range(n) if find(i) == i)
```

### Q3 — HackerRank: Components in a Graph

[Problem link](https://www.hackerrank.com/challenges/components-in-graph/problem)

The required HackerRank function name is `componentsInGraph(gb)`. Join every supplied pair, then collect the sizes of components containing at least two vertices. Isolated vertices are excluded.

```python
def componentsInGraph(gb):
    max_node = 2 * len(gb)
    parent = list(range(max_node + 1))
    size = [1] * (max_node + 1)

    def find(x):
        if parent[x] != x:
            parent[x] = find(parent[x])
        return parent[x]

    def union(a, b):
        ra, rb = find(a), find(b)

        if ra == rb:
            return

        if size[ra] < size[rb]:
            ra, rb = rb, ra

        parent[rb] = ra
        size[ra] += size[rb]

    for u, v in gb:
        union(u, v)

    seen = set()
    component_sizes = []

    for node in range(1, max_node + 1):
        root = find(node)

        if size[root] > 1 and root not in seen:
            seen.add(root)
            component_sizes.append(size[root])

    return [min(component_sizes), max(component_sizes)]
```

### Q4 — HackerRank: Journey to the Moon

[Problem link](https://www.hackerrank.com/challenges/journey-to-the-moon/problem)

Astronauts in the same connected component belong to the same country. After building the components, count pairs selected from different countries.

```python
def journeyToMoon(n, astronaut):
    parent = list(range(n))
    size = [1] * n

    def find(x):
        if parent[x] != x:
            parent[x] = find(parent[x])
        return parent[x]

    def union(a, b):
        ra, rb = find(a), find(b)

        if ra == rb:
            return

        if size[ra] < size[rb]:
            ra, rb = rb, ra

        parent[rb] = ra
        size[ra] += size[rb]

    for a, b in astronaut:
        union(a, b)

    answer = 0
    previous = 0

    for i in range(n):
        if find(i) == i:
            answer += previous * size[i]
            previous += size[i]

    return answer
```

The running total counts every cross-country pair once. For example, component sizes 3, 2 and 4 produce:
`3 × 2 + 5 × 4 = 26` valid pairs.

## 3. Mistakes to Avoid

- Compare root representatives, not just the original node values.
- Do not add a cycle-forming edge in Redundant Connection.
- Update the root's size only after a successful union.
- Number of Provinces uses zero-based city indexes.
- Components in a Graph uses node labels up to twice the number of input pairs; isolated single-node components must not be included in the answer.
- Keep the HackerRank function name exactly as `componentsInGraph(gb)`.
- Journey to the Moon includes astronauts with no connections as single-person country groups.
- Count pairs from different components once, not twice.

## 4. Coding Problems Assigned

### LeetCode
- [ ] Q1 — [Redundant Connection](https://leetcode.com/problems/redundant-connection/)
- [ ] Q2 — [Number of Provinces](https://leetcode.com/problems/number-of-provinces/)

### HackerRank
- [ ] Q1 — [Components in a Graph](https://www.hackerrank.com/challenges/components-in-graph/problem)
- [ ] Q2 — [Journey to the Moon](https://www.hackerrank.com/challenges/journey-to-the-moon/problem)

**Submission status:** The four problems have been assigned and solutions reviewed. Mark a problem Accepted only after its online judge confirms acceptance.

## 5. Time & Space Complexity

Let V be the number of vertices, E the number of edges, and α(V) the inverse Ackermann function (practically constant for ordinary input sizes).

| Problem | Time | Auxiliary Space |
|---|---|---|
| Redundant Connection | O(E × α(V)) | O(V) |
| Number of Provinces | O(V² × α(V)) | O(V) |
| Components in a Graph | O(E × α(V) + V) | O(V) |
| Journey to the Moon | O((V + E) × α(V)) | O(V) |

## 6. Mock Interview Questions & Answers

1. **What is Union-Find?**  
   A data structure that maintains disjoint groups and supports finding and merging their representatives.

2. **What does `find(x)` do?**  
   It returns the root representative of the group containing `x`.

3. **What does `union(a, b)` do?**  
   It joins the two groups if they are different.

4. **What is path compression?**  
   During a find operation, it makes visited nodes point directly to the root to speed up later lookups.

5. **What is union by size?**  
   It attaches the smaller component tree below the larger one and updates the larger root's size.

6. **How can DSU detect a cycle in an undirected graph?**  
   If an edge's endpoints already have the same root, adding that edge closes a cycle.

7. **Where is DSU used?**  
   In connected-component problems, cycle detection and Kruskal's Minimum Spanning Tree algorithm.

## 7. Key Learning

Union-Find efficiently maintains connected groups. The same `find()` and `union()` operations can detect a redundant edge, count provinces, measure component sizes and count pairs from different components. Path compression and union by size keep the operations efficient.
