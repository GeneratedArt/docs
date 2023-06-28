---
title: Cellular Automata (CA)
subtitle: Cellular Automata (CA) is a computational model consisting of a grid of cells.
tags: [algorithm]
author:
---

Cellular Automata (CA) is a computational model consisting of a grid of cells, each having a state that evolves over discrete time steps based on a set of predefined rules. These rules determine how the states of the cells change in response to the states of their neighboring cells. CA can exhibit complex and emergent behavior, often resulting in visually interesting patterns and dynamic systems.

In a one-dimensional CA, each cell has two neighbors (one on each side), and the state of a cell at time t+1 depends on the state of the cell and its neighbors at time t. This relationship can be expressed using mathematical formulas, where the next state of a cell is determined based on the current states of its neighboring cells.

Here are a few examples of mathematical formulas used in Cellular Automata:

1. Rule 30: The next state of a cell is the XOR (exclusive OR) of its left neighbor, itself, and its right neighbor.

2. Rule 110: The next state of a cell is determined by a specific lookup table that considers the state of the cell and its neighbors.

3. Game of Life: This is a famous CA developed by John Conway. It has specific rules based on the number of neighboring live cells that determine whether a cell lives, dies, or is born in the next generation.

Generative artists can utilize Cellular Automata in various ways to create visual art. Some common approaches include:

1. Visual Patterns: Artists can explore different rule sets and initial configurations to generate intricate visual patterns, ranging from simple repetitive structures to complex and evolving forms.

2. Abstract Art: By mapping the state of each cell to visual attributes such as color, shape, or texture, artists can create abstract artworks that exhibit self-organization and emergent behavior.

3. Texture Generation: Cellular Automata can be used to generate textures that can be applied to surfaces or used as backgrounds in digital art or design.

4. Animation: By evolving the state of the cells over time, artists can create animations that showcase the dynamic behavior and evolution of the Cellular Automata patterns.

Generative artists often experiment with different rule sets, grid sizes, boundary conditions, and visualization techniques to create unique and visually captivating artworks using Cellular Automata. The iterative nature of CA lends itself well to generative art, allowing artists to explore and discover intriguing patterns and dynamics within the system.

Examples:

1. Processing (Java-based language for visual arts):

```java
int[] cells;
int[] next;

int rule = 30;
int cellSize = 5;
int numCells;

void setup() {
  size(800, 400);
  numCells = width / cellSize;

  cells = new int[numCells];
  next = new int[numCells];

  cells[numCells/2] = 1; // Set the middle cell as alive in the initial generation
}

void draw() {
  background(255);

  for (int i = 0; i < numCells; i++) {
    if (cells[i] == 1) {
      fill(0);
    } else {
      fill(255);
    }
    rect(i * cellSize, 0, cellSize, cellSize);
  }

  generateNextGeneration();
}

void generateNextGeneration() {
  for (int i = 1; i < numCells - 1; i++) {
    int left = cells[i-1];
    int middle = cells[i];
    int right = cells[i+1];
    next[i] = applyRule(left, middle, right);
  }

  int[] temp = cells;
  cells = next;
  next = temp;
}

int applyRule(int a, int b, int c) {
  int index = 7 - (a << 2 | b << 1 | c);
  return (rule >> index) & 1;
}
```

2. Python:

```python
import numpy as np
import matplotlib.pyplot as plt

num_cells = 100
num_generations = 100
rule = 110

cells = np.zeros(num_cells, dtype=int)
cells[num_cells // 2] = 1

for _ in range(num_generations):
    plt.imshow([cells], cmap='Greys')
    plt.show()

    next_gen = np.zeros_like(cells)
    for i in range(1, num_cells - 1):
        left = cells[i - 1]
        middle = cells[i]
        right = cells[i + 1]
        next_gen[i] = (rule >> (7 - (left << 2 | middle << 1 | right))) & 1

    cells = next_gen
```
