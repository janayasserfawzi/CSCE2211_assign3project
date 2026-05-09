# CSCE2211 Assignment 3 — Dijkstra & Floyd–Warshall

**Name:** Jana Fawzi  
**Student ID:** 900241258
**Section:** 01 

## Project Description

This project implements shortest path algorithms in C++ for a weighted directed graph:

- **Dijkstra's Algorithm** — Single-source shortest path using a min-heap priority queue
- **Repeated Dijkstra** — All-pairs shortest path by running Dijkstra from every node
- **Floyd–Warshall Algorithm** — All-pairs shortest path using dynamic programming

The graph is loaded from a text file (`Code_library/graph.txt`) with 100 nodes and 9900 edges. All implementations are validated using Google Test.

---

## Project Structure

```
CSCE2211_assign3project/
├── Code_library/
│   ├── dijkstra_floyd.cpp   # Implementation of all three algorithms
│   ├── graph.cpp            # Graph loading (adjacency list + matrix)
│   ├── graph.h
│   ├── dijkstra.h
│   ├── floyd.h
│   └── graph.txt            # Input graph data
├── Google_tests/
│   ├── Testcases.cpp        # Google Test test cases
│   ├── CMakeLists.txt
│   └── lib/                 # Google Test & Google Mock libraries
├── main.cpp
├── CMakeLists.txt
└── README.md
```

---

## How to Build

### Prerequisites
- [CMake](https://cmake.org/download/) (version 3.24+)
- [MinGW (g++ 15+)](https://github.com/niXman/mingw-builds-binaries/releases) with `C:\mingw64\bin` added to PATH

### Build Steps

Open a terminal in the project root folder and run:

```powershell
mkdir build
cd build
cmake .. -G "MinGW Makefiles"
cmake --build .
```

---

## How to Run Tests

After building, from inside the `build` folder run:

```powershell
.\Google_tests\Google_Tests_run.exe
```

### Expected Output

```
[==========] Running 3 tests from 3 test suites.
[ RUN      ] GraphLoadTest.LoadsCorrectNodeEdgeCount
[       OK ] GraphLoadTest.LoadsCorrectNodeEdgeCount
[ RUN      ] DijkstraTest.SingleSource
[       OK ] DijkstraTest.SingleSource
[ RUN      ] CompareAlgorithms.DijkstraVsFloyd
[       OK ] CompareAlgorithms.DijkstraVsFloyd
[  PASSED  ] 3 tests.
```

---

## Algorithm Details

### Dijkstra's Algorithm
Uses a min-heap priority queue to greedily relax edges. Time complexity: **O((V + E) log V)**.

### Repeated Dijkstra
Runs Dijkstra from every node 0 to n-1 to produce a full all-pairs shortest path matrix. Time complexity: **O(V · (V + E) log V)**.

### Floyd–Warshall
Triple nested loop over intermediate nodes k, source i, and destination j. Time complexity: **O(V³)**. Uses the adjacency matrix as input.

---

## Notes
- The graph is directed and weighted.
- Infinity is represented as `1e9` (one billion).
- An overflow guard is used in Floyd–Warshall to avoid integer overflow when summing two infinity values.
- All three test cases pass successfully with the provided graph.
