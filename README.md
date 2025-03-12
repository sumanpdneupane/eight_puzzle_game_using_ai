# 🔥 Cracking the 8-Puzzle with BFS, DFS, Greedy & A* – My Journey 🚀

Solving the 8-Puzzle is more than just moving tiles—it’s about choosing the best strategy to reach the goal efficiently. I took on the challenge of implementing BFS, DFS, Greedy Best-First Search, and A* while carefully managing state representation and heuristic selection. Here’s how I approached it:

---

## 🔹 Step 1: Structuring the State Representation

Before diving into search algorithms, it was crucial to define a proper state representation for the 8-puzzle problem. The state representation determines how we store, manipulate, and track different puzzle configurations during the search process.

### 1️⃣ Properties of State Representation

✅ **State Space Definition:**
- A state in the 8-puzzle consists of a 3x3 grid, where each tile (1-8) is placed in one of the 9 positions.
- The blank tile (0) represents the empty space, which allows movement.

✅ **Initial & Goal State:**
- The initial state is the given arrangement of tiles from which the search begins.
- The goal state is a predefined arrangement where all tiles are in order:
  
```
1 2 3
4 5 6
7 8 0
```
- The solution is found when the current state matches the goal state.

✅ **State Transition:**
- The blank tile (0) moves **UP, DOWN, LEFT, or RIGHT** to swap places with an adjacent tile.
- Each move results in a new valid state.

✅ **Cost Function ( for BFS, DFS, GBFS and A*** **):**
- The cost to reach a state (**g(n)**) is typically the number of moves taken from the initial state.
- **BFS and DFS** considers equal cost for all moves, while **GBFS and A*** computes an estimated cost using heuristics.

✅ **State Uniqueness (Hashable Representation):**
- To avoid revisiting duplicate states, we store each state as a **tuple of tuples** (immutable data structure).

```python
((1, 2, 3),
 (4, 5, 6),
 (7, 8, 0))  # Hashable representation of the 3x3 grid
```

✅ **Efficient Code Implementation:**
- Stored the puzzle as a **2D list** for easy swapping of elements.
- Tracked the position of the blank tile (0) dynamically to optimize move generation.
- Used **Python’s Enum** for movement directions to ensure structured and readable code.
- Created **deep copies** of states for transitions to avoid modifying the original state.

This structured representation helped in efficiently implementing BFS, DFS, Greedy, and A* while keeping the state tracking efficient, hashable, and manageable! 🚀

---

## 🔹 Step 2: Implementing Search Strategies

### 🔹 BFS (Breadth-First Search)
- Ensures the shortest path but can be **slow due to high memory usage**.
- Explores all possibilities level-wise.

### 🔹 DFS (Depth-First Search)
- A depth-first approach that **sometimes finds the goal faster**, but without guaranteeing the optimal path.

### 🔹 Greedy Best-First Search (GBFS)
- Uses a **heuristic function** to prioritize the most promising state, making the search faster but not always optimal.
- It selects the next state based on:

```
f(n) = h(n)
```

where **h(n)** is the estimated cost to reach the goal.

### 🔹 A* – The Perfect Balance!
- Instead of only prioritizing estimated distance to the goal (**h(n)**), it also considers the actual cost from the start (**g(n)**):

```
f(n) = g(n) + h(n)
```

where:
- **g(n):** Cost to reach the current state.
- **h(n):** Estimated cost to reach the goal.

This allowed **A*** to find the **optimal path efficiently**.

---

## 🔹 Step 3: Choosing the Right Heuristic h(n)

To make the search smarter, I tested different heuristics:

📌 **Misplaced Tiles** – Counts tiles that are not in their correct position (simple but not very precise).

📌 **Manhattan Distance** – Computes the sum of the absolute row/column differences for each tile to reach its correct position:

```
h(n) = ∑(|x1 - x2| + |y1 - y2|)
```

📌 **Euclidean Distance** – Instead of just row/column differences, this calculates the direct straight-line distance for each tile to its goal position:

```
h(n) = sqrt((x1 - x2)^2 + (y1 - y2)^2)
```

📌 **Diagonal Distance** – Used when diagonal movements are allowed. It combines Manhattan Distance and diagonal steps:

```
dx = abs(current_x – goal_x)
dy = abs(current_y – goal_y)
h(n) = D * (dx + dy) + (D2 - 2 * D) * min(dx, dy)
```

where:
- **D = 1** (cost of moving horizontally/vertically)
- **D2 = sqrt(2)** (cost of moving diagonally)

📌 **Cost Function (g(n))** – The path cost from the start state, increasing by 1 per move in A*.

---

## 🔹 Step 4: Implementing A*
I designed A* with a **priority queue**, always expanding the state with the lowest **f(n) = g(n) + h(n)**. This ensures we reach the goal with **minimal steps and efficiency**.

---

## 🔹 Challenges & Learnings
✅ Avoiding redundant states and managing state space.
✅ Handling performance trade-offs between algorithms.
✅ Experimenting with different heuristics to optimize search efficiency.

This project reinforced how different search algorithms tackle the same problem with varying efficiency and optimality. 🚀

---

💡 **Which algorithm and heuristic do you think is the best for solving the 8-Puzzle? Let’s discuss in the comments!** 🔽

---

#AI #ArtificialIntelligence #SearchAlgorithms #8Puzzle #Python #AStar #BFS #DFS #GreedySearch #MachineLearning #Heuristics
