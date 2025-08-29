# Dyno Tuning & ECU Remapping Using Graphs

## Overview

This project applies **graph data structures and algorithms** (notably Dijkstra's algorithm) to optimize automotive dyno tuning and ECU remapping. By modeling engine states and tuning transitions as nodes and weighted edges, it helps identify optimal tuning paths and visualizes engine performance improvements using horsepower data before and after tuning.[1]

## Features

- Graph representation of tuning state transitions
- Reads initial and tuned engine parameters from CSV files
- Calculates horsepowers for each state and visualizes with ASCII plots
- Implements Dijkstra's algorithm to find optimal (minimum-cost) tuning path[1]

## Project Structure

| File/Folder              | Purpose                                                |
|--------------------------|-------------------------------------------------------|
| dyno_tuning.c            | Main C program with all logic and ASCII plotting      |
| Intialvalues.csv         | Initial (stock) engine readings (power, rpm per state)|
| FinalValues.csv          | Tuned/optimized engine readings (power, rpm per state)|
| README.md                | Project documentation                                 |
| /docs                    | Detailed algorithm and data structure explanations    |

## Prerequisites

- GCC compiler or compatible C compiler
- Two CSV files: `Intialvalues.csv` and `FinalValues.csv` in the project directory
- Each CSV: 6 lines, each with `<power>,<rpm>` (comma separated, one per node/state)

## Build and Run

```bash
gcc -o dyno_tuning dyno_tuning.c
./dyno_tuning
```

## Example CSV

`Intialvalues.csv`
```
100,3000
110,3200
120,3400
130,3600
140,3800
150,4000
```
`FinalValues.csv`
```
120,3000
130,3200
140,3400
150,3600
160,3800
170,4000
```

## Key Algorithm Extract (C)

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <limits.h>
#define V 6 // Number of states

// ... [rest of code as in question] ...
```
- Computes node weights as horsepower difference between tuned and initial state
- Runs Dijkstra’s algorithm to find shortest path from base state
- Visualizes initial and tuned HP values as ASCII plot[1]

## How It Works

1. Each **node**: A unique combination of power and rpm (engine state)
2. **Edges**: Weighted by the difference in horsepower between tuned and initial measurements
3. **Dijkstra's Algorithm**: Finds the shortest (minimum “cost”) path across tuning states
4. **ASCII Visualization**: See HP changes graphically for instant validation

## Applications

- Automates dyno tuning across complex parameter spaces
- Assists in motorsport, custom builds, and performance research
- Educational tool for combining data structures & real engineering

## References

See the final report and academic papers cited in `/docs` for theory and industrial context.[1]

## License

MIT License

***

