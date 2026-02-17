# algorithm-pathfinder
## Overview

This project implements several uninformed search algorithms in a grid environment to find paths from a start node to a target node. The implemented algorithms include:

- Breadth-First Search (BFS)  
- Depth-First Search (DFS)  
- Uniform-Cost Search (UCS)  
- Depth-Limited Search (DLS)  
- Iterative Deepening DFS (IDDFS)  
- Bidirectional Search  

Each algorithm is visualized on a grid, showing the explored cells, frontier, and final path.
## Breadth-First Search (BFS)

1. **Initialization:**  
   - Frontier: `deque` containing the start node.  
   - Path Tracking: `came_from` dictionary initialized with the start node.  
   - Visualization: Starting cell marked as `FRONTIER`.  

2. **Search Step (`bfs_step`):**  
   - Node Selection: Oldest node removed using `popleft()`.  
   - Exploration Tracking: Node added to `explored` set and marked as `EXPLORED`.  
   - Target Check: If current node is target, reconstruct path.  
   - Neighbor Expansion: Adjacent cells added to frontier if unexplored.  

3. **Path Reconstruction:**  
   - Trace `came_from` from target to start.  
   - Reverse the path and mark it as `PATH` (purple).  

**Pros:**  
- Guaranteed shortest path.  
- Explores all directions layer by layer.  

**Cons:**  
- Memory intensive.  
- Less efficient than informed searches.  

**Test Cases:** Spiral maze, random maze.

---

## Depth-First Search (DFS)

**Explanation:**  
1. **Initialization:**  
   - Frontier: Stack initialized with start node.  
   - Path Tracking: `came_from` dictionary for parent nodes.  
   - Visualization: Start node marked as `FRONTIER`.  

2. **Iterative Step (`dfs_step`):**  
   - Node Selection: Most recent node popped from stack.  
   - Exploration: Node added to `explored`, state updated.  
   - Neighbor Processing: Neighbors added in reversed order to maintain clockwise exploration.  

3. **Path Reconstruction:**  
   - Trace `came_from` dictionary from target to start.  
   - Mark final path as `PATH`.  

**Pros:**  
- Memory efficient.  
- Can find deep paths quickly.  

**Cons:**  
- Does not guarantee shortest path.  
- Can explore inefficiently in large grids.  

**Test Cases:** Spiral maze, random maze.

---

## Uniform-Cost Search (UCS)

**Explanation:**  
1. **Initialization:**  
   - Frontier: Priority queue with `(cost, node)` tuples.  
   - Cost Tracking: `cost_so_far` dictionary.  
   - Path Tracking: `came_from` dictionary.  

2. **Iterative Step (`ucs_step`):**  
   - Node Selection: Node with lowest cost popped from priority queue.  
   - Neighbor Expansion: Calculate `new_cost` and update frontier if cost is lower.  

3. **Visualization:**  
   - Frontier nodes marked as `FRONTIER`, explored nodes as `EXPLORED`.  

**Pros:**  
- Considers actual move costs.  
- Finds optimal path.  

**Cons:**  
- More complex and computationally expensive.

---

## Depth-Limited Search (DLS)

**Explanation:**  
- Uses a stack containing `(node, depth)` tuples.  
- Explores neighbors only if current depth < depth_limit.  
- Marks path if target found, otherwise stops at limit.  

**Pros:**  
- Prevents infinite search.  
- Space efficient.  

**Cons:**  
- Incomplete if target is beyond depth limit.  
- Does not guarantee shortest path.  

**Test Cases:** Spiral maze, random maze.

---

## Iterative Deepening DFS (IDDFS)

**Explanation:**  
- Combines DLS and DFS iteratively increasing depth limit.  
- Each iteration searches with current depth limit, then increments.  
- Ensures shortest path while using less memory than BFS.  

**Pros:**  
- Finds shortest path like BFS.  
- Space efficient like DFS.  

**Cons:**  
- Redundant exploration at each depth increment.

---

## Bidirectional Search

**Explanation:**  
- Uses two frontiers: forward from start, backward from target.  
- Alternates steps between frontiers.  
- Reconstructs path when frontiers meet.  

**Pros:**  
- Faster search in large grids.  
- Finds shortest path.  

**Cons:**  
- Requires tracking two frontiers and dictionaries.  
- More complex implementation.  

**Test Cases:** Spiral maze, random maze.

---

## How to Run

1. Clone the repository:

```bash
git clone <your-github-repo-link>
cd algorithm-pathfinder
