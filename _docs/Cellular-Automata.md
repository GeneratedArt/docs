---
title: Cellular Automata (CA)
subtitle: Cellular Automata (CA) is a computational model consisting of a grid of cells.
tags: [algorithm]
author:
---

Cellular Automata is a computational model consisting of a grid of cells, where each cell's state is updated based on a set of predefined rules and the states of its neighboring cells. The state of each cell evolves over discrete time steps, making it a dynamic and iterative system. Cellular Automata can exhibit complex patterns and behavior emerging from simple local interactions.

Examples of math formulas used in Cellular Automata include:

1. Conway's Game of Life: One of the most well-known cellular automata, where each cell follows the following rules:
   - Any live cell with fewer than two live neighbors dies (underpopulation).
   - Any live cell with two or three live neighbors survives.
   - Any live cell with more than three live neighbors dies (overpopulation).
   - Any dead cell with exactly three live neighbors becomes alive (reproduction).

2. Elementary Cellular Automaton: A one-dimensional cellular automaton with a binary state (0 or 1), where the next state of each cell is determined by a lookup table specifying the rules based on its current state and the states of its two neighbors.

Algorithms that derive from Cellular Automata include:

1. Rule-based Systems: Cellular Automata can be used as a basis for creating rule-based systems, where the behavior or evolution of a system is defined by a set of rules applied to individual components or cells.

2. Generative Systems: Cellular Automata can be used as generative algorithms to create patterns, structures, or textures in generative art. By defining rules that govern the state transitions of cells and mapping them to visual elements, artists can generate complex and visually appealing compositions.

3. Complex Systems Modeling: Cellular Automata provide a way to model and simulate complex systems in various domains such as physics, biology, social sciences, and more. By defining rules that mimic the behavior of real-world phenomena, cellular automata can be used to study and understand emergent behavior in these systems.

In Generative Art, Cellular Automata can be used to create visually captivating and intricate patterns. Artists can design rules that govern the cell states, and the resulting patterns can be visualized and interpreted in various ways. Cellular Automata can be used to generate artwork, digital images, animations, or interactive installations by mapping cell states to colors, shapes, textures, or movements. Artists can experiment with different rules, initial configurations, or parameter values to explore the vast creative possibilities and produce unique generative art pieces.

Processing:

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
Python:

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
JavaScript:

```javascript
const numCells = 100;
const cellSize = 5;
const numGenerations = 100;
const rule = 30;

let cells = new Array(numCells).fill(0);
let next = new Array(numCells).fill(0);

cells[Math.floor(numCells / 2)] = 1;

for (let generation = 0; generation < numGenerations; generation++) {
  for (let i = 0; i < numCells; i++) {
    // Visualize the cells here using your preferred graphics library or HTML canvas
    // For example, you can create HTML elements or manipulate pixels on a canvas
  }

  generateNextGeneration();
}

function generateNextGeneration() {
  for (let i = 1; i < numCells - 1; i++) {
    const left = cells[i - 1];
    const middle = cells[i];
    const right = cells[i + 1];
    next[i] = applyRule(left, middle, right);
  }

  [cells, next] = [next, cells];
}

function applyRule(a, b, c) {
  const index = 7 - (a << 2 | b << 1 | c);
  return (rule >> index) & 1;
}
```
C++:

```cpp
#include <iostream>
#include <vector>

const int numCells = 100;
const int numGenerations = 100;
const int rule = 30;

std::vector<int> cells(numCells);
std::vector<int> next(numCells);

void generateNextGeneration() {
  for (int i = 1; i < numCells - 1; i++) {
    int left = cells[i - 1];
    int middle = cells[i];
    int right = cells[i + 1];
    next[i] = applyRule(left, middle, right);
  }

  cells = next;
}

int applyRule(int a, int b, int c) {
  int index = 7 - (a << 2 | b << 1 | c);
  return (rule >> index) & 1;
}

int main() {
  cells[numCells / 2] = 1;

  for (int generation = 0; generation < numGenerations; generation++) {
    for (int i = 0; i < numCells; i++) {
      // Visualize the cells here using your preferred graphics library or ASCII art
      // For example, you can print '*' for alive cells and ' ' for dead cells
      std::cout << (cells[i] ? '*' : ' ');
    }
    std::cout << std::endl;

    generateNextGeneration();
  }

  return 0;
}
```
Java:

```java
import java.util.Arrays;

public class CellularAutomata {
    public static void main(String[] args) {
        int numCells = 100;
        int numGenerations = 100;
        int rule = 30;

        int[] cells = new int[numCells];
        int[] next = new int[numCells];

        cells[numCells / 2] = 1;

        for (int generation = 0; generation < numGenerations; generation++) {
            for (int i = 0; i < numCells; i++) {
                // Visualize the cells here using your preferred graphics library or ASCII art
                // For example, you can print '*' for alive cells and ' ' for dead cells
                System.out.print(cells[i] == 1 ? '*' : ' ');
            }
            System.out.println();

            generateNextGeneration(cells, next, rule);

            int[] temp = cells;
            cells = next;
            next = temp;
        }
    }

    private static void generateNextGeneration(int[] cells, int[] next, int rule) {
        for (int i = 1; i < cells.length - 1; i++) {
            int left = cells[i - 1];
            int middle = cells[i];
            int right = cells[i + 1];
            next[i] = applyRule(left, middle, right, rule);
        }
    }

    private static int applyRule(int left, int middle, int right, int rule) {
        int index = 7 - (left << 2 | middle << 1 | right);
        return (rule >> index) & 1;
    }
}
```
Unity/C#:

```csharp
using UnityEngine;

public class CellularAutomata : MonoBehaviour
{
    public int numCells = 100;
    public int numGenerations = 100;
    public int rule = 30;
    public GameObject cellPrefab;
    public float cellSize = 0.5f;

    private int[] cells;
    private int[] next;

    private void Start()
    {
        cells = new int[numCells];
        next = new int[numCells];

        cells[numCells / 2] = 1;

        for (int generation = 0; generation < numGenerations; generation++)
        {
            for (int i = 0; i < numCells; i++)
            {
                // Instantiate or update GameObjects representing the cells at their positions
                if (cells[i] == 1)
                {
                    Vector3 position = new Vector3(i * cellSize, generation * cellSize, 0f);
                    Instantiate(cellPrefab, position, Quaternion.identity);
                }
            }

            generateNextGeneration();
        }
    }

    private void generateNextGeneration()
    {
        for (int i = 1; i < numCells - 1; i++)
        {
            int left = cells[i - 1];
            int middle = cells[i];
            int right = cells[i + 1];
            next[i] = applyRule(left, middle, right);
        }

        int[] temp = cells;
        cells = next;
        next = temp;
    }

    private int applyRule(int left, int middle, int right)
    {
        int index = 7 - (left << 2 | middle << 1 | right);
        return (rule >> index) & 1;
    }
}
```
