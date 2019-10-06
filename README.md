# leetcode
leetnode note
## Python modules
1. list.sort(__key = lambda x: x[1]__)

2. graph = __collections.defaultdict(list)__

3. __heapify__(list)     
a = __heapq.pop(queue)__  
__heapq.push(b)__

4. dq = __collections.deque(list)__      
append, appendleft, clear, copy(shallow copy), count(dp.count(23)means counting the num of 23 in dq), extend, extendleft, 
index, insert, pop, popleft, remove, reverse, rotate





## Interview expressions

### Part 1:

__project__ the 2D image/vector/matrix __into__ a 1D array/vector and use the binary search to find the __boundaries__

__suppose__ we have a 10x11 image __as shown__ in figure 1

if we project ... into ... __with the following rules__

__similarly__, we can do the same for rows

now, we __claim__ the following __lemma__

__proof by contradiction__, __assume to the contrary__ that there are .... __Thus, there exists__ .... Therefore, ... __which contradicting the condition of__ "...". __Therefore, we conclude__ ....

__on the fly__: during the running of a computer program without interrupting the run

however, the __projection step cost O(mn) time__ which __dominate__ the entire algorithm. If so, we __gain nothing comparing with the previous approaches__. The __trick__ is that we do not need to do the projection step __as a preprocess__. We can do it __on the fly__, i.e. "don't project the column/row unless needed".

similarly it __costs O(nlogm) to find__ "top" and "bottom". __The entire algorithm has a time complexity of__ O(nlogm + mlogn)





## Solutions:
### 1. binary search
```
left = 0
right = n
while left < right:
    middle = (left + right) // 2
    if f(middle) < target:
        left = middle + 1
    else:
        right = middle
result = right
```

### 2. union find
```
parent = [i for i in range(N)]:
def find(x):
    if parent[x] == x:
        return x
    while parent[parent[x]] != parent[x]:
        parent[x] = parnet[parent[x]]
    return parent[x]
def union(x, y):
    parent[x] = y
    return 
if find(x) != find(y):
    union(find(x), find(y))
```

### 3. kruskal's algorithm: to find the minimum spanning tree
```
KRUSKAL(G):
    A = ∅
    foreach v ∈ G.V:
    MAKE-SET(v)
        foreach (u, v) in G.E ordered by weight(u, v), increasing:
            if FIND-SET(u) ≠ FIND-SET(v):
            A = A ∪ {(u, v)}
            UNION(FIND-SET(u), FIND-SET(v))
    return A
```

### 4. prim's algorithm: to find the MST
```
    G = collections.defaultdict(list)
        for city1, city2, cost in connections:
            G[city1].append((cost, city2))
            G[city2].append((cost, city1))
        
        queue = [(0, N)]  # [1] Arbitrary starting point N costs 0.
        visited = set()
        total = 0
        while queue and len(visited) < N: # [3] Exit if all cities are visited.
            # cost is always least cost connection in queue.
            cost, city = heapq.heappop(queue)
            if city not in visited:
                visited.add(city)
                total += cost # [2] Grow tree by one edge.
                for edge_cost, next_city in G[city]:
                    heapq.heappush(queue, (edge_cost, next_city))
        return total if len(visited) == N else -1
```

























