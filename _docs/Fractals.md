---
title: Fractals
subtitle: Fractals are intricate mathematical patterns that exhibit self-similarity at different scales.
tags: [algorithm]
author:
---

Fractals are complex mathematical patterns that exhibit self-similarity at different scales. They are created by repeating a simple geometric or mathematical operation recursively or iteratively, resulting in intricate and detailed structures. Fractals often exhibit fine and intricate patterns, with similar shapes and structures recurring at different levels of magnification.

Examples of math formulas used in Fractals include:

1. Mandelbrot Set: The Mandelbrot set is defined by the iterative formula: Z(n+1) = Z(n)^2 + C, where Z(n) is a complex number, and C represents a point in the complex plane.

2. Julia Set: The Julia set is similar to the Mandelbrot set but uses a fixed complex constant C and iteratively applies the formula: Z(n+1) = Z(n)^2 + C, starting with different initial complex values.

3. Sierpinski Triangle: The Sierpinski triangle is formed by recursively dividing an equilateral triangle into smaller triangles and removing the inner triangle.

4. Koch Snowflake: The Koch snowflake is created by replacing the middle third of each line segment with an equilateral triangle and repeating this process infinitely.

Algorithms that derive from Fractals include:

1. Iterated Function Systems (IFS): IFS is a method to generate fractals by applying a set of affine transformations iteratively to a point or set of points. The transformations can be scaled, rotated, and translated to create complex and self-similar patterns.

2. Lindenmayer Systems (L-Systems): L-Systems are string rewriting systems used to generate fractal-like patterns. Starting with an initial string (axiom), production rules are applied iteratively to replace each character with a set of characters, forming more complex patterns.

Fractals can be used in Generative Art in various ways:

1. Visual Art: Fractals can be rendered and visualized to create stunning and intricate visual artworks. Artists can use color, shading, and other visual effects to enhance the aesthetic appeal of the fractal patterns.

2. Digital Landscapes: Fractals can be used to generate realistic and visually captivating landscapes, such as mountains, coastlines, and forests. The self-similar and recursive nature of fractals lends itself well to creating intricate natural scenes.

3. Textures and Patterns: Fractals can serve as a source of inspiration for generating textures and patterns used in various digital design applications. The repetitive and detailed structures of fractals can be applied to surfaces, backgrounds, or 3D models to add visual interest.

4. Generative Music: Fractal algorithms can be employed to create generative music compositions. By associating musical parameters, such as pitch, rhythm, or dynamics, with the geometric properties of fractals, artists can generate unique and evolving musical patterns.

5. Data Visualization: Fractals can be used to represent and visualize complex datasets or mathematical functions. By mapping data values to geometric properties of fractals, artists can create visually engaging representations of abstract concepts or scientific data.

Fractals provide generative artists with a rich source of inspiration and a means to create intricate, self-repeating patterns that exhibit beauty and complexity. They offer endless possibilities for artistic exploration and expression.



Processing (Java):

```java
import processing.core.PApplet;

public class FractalExample extends PApplet {

    float minR = -2.5f;
    float maxR = 1.5f;
    float minI, maxI;
    int maxIterations = 100;

    public void settings() {
        size(800, 800);
    }

    public void setup() {
        colorMode(HSB, maxIterations, 1, 1);
        noLoop();
        minI = map(height, 0, height, -1.5f, 1.5f);
        maxI = minI + (maxR - minR) * height / width;
    }

    public void draw() {
        loadPixels();
        for (int x = 0; x < width; x++) {
            for (int y = 0; y < height; y++) {
                float a = map(x, 0, width, minR, maxR);
                float b = map(y, 0, height, minI, maxI);

                int n = 0;
                float ca = a;
                float cb = b;

                while (n < maxIterations) {
                    float aa = a * a - b * b;
                    float bb = 2 * a * b;

                    a = aa + ca;
                    b = bb + cb;

                    if (a * a + b * b > 16) {
                        break;
                    }

                    n++;
                }

                int hue = n % maxIterations;
                float brightness = map(n, 0, maxIterations, 0, 1);
                if (n == maxIterations) {
                    brightness = 0;
                }

                int color = color(hue, 1, brightness);
                pixels[x + y * width] = color;
            }
        }
        updatePixels();
    }

    public static void main(String[] args) {
        PApplet.main("FractalExample");
    }
}
```

Python:

```python
import numpy as np
import matplotlib.pyplot as plt

def mandelbrot(width, height, minR, maxR, minI, maxI, maxIterations):
    img = np.zeros((width, height))
    r_vals = np.linspace(minR, maxR, width)
    i_vals = np.linspace(minI, maxI, height)

    for x in range(width):
        for y in range(height):
            c = complex(r_vals[x], i_vals[y])
            z = complex(0, 0)

            for i in range(maxIterations):
                z = z * z + c

                if abs(z) > 2:
                    img[x, y] = i
                    break

    img = np.log(img + 1)
    img = np.flipud(img.T)
    return img

width = 800
height = 800
minR, maxR = -2.5, 1.5
minI, maxI = -1.5, 1.5
maxIterations = 100

fractal_img = mandelbrot(width, height, minR, maxR, minI, maxI, maxIterations)
plt.imshow(fractal_img, cmap='hot', extent=[minR, maxR, minI, maxI])
plt.show()
```

Certainly! Here are code examples of generating fractals using JavaScript and C++:

JavaScript:

```javascript
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
const width = canvas.width;
const height = canvas.height;

function drawFractal() {
  const maxIterations = 1000;
  const minR = -2.5;
  const maxR = 1.5;
  const minI = -1.5;
  const maxI = 1.5;

  for (let x = 0; x < width; x++) {
    for (let y = 0; y < height; y++) {
      const a = map(x, 0, width, minR, maxR);
      const b = map(y, 0, height, minI, maxI);

      let ca = a;
      let cb = b;
      let n = 0;

      while (n < maxIterations) {
        const aa = a * a - b * b;
        const bb = 2 * a * b;

        a = aa + ca;
        b = bb + cb;

        if (a * a + b * b > 16) {
          break;
        }

        n++;
      }

      const brightness = map(n, 0, maxIterations, 0, 255);
      const color = `rgb(${brightness}, ${brightness}, ${brightness})`;
      ctx.fillStyle = color;
      ctx.fillRect(x, y, 1, 1);
    }
  }
}

function map(value, start1, stop1, start2, stop2) {
  return ((value - start1) / (stop1 - start1)) * (stop2 - start2) + start2;
}

drawFractal();
```

C++:

```cpp
#include <iostream>
#include <fstream>
#include <cmath>

const int width = 800;
const int height = 800;

void writePixel(std::ofstream& file, int r, int g, int b) {
  file << r << " " << g << " " << b << " ";
}

void drawFractal() {
  std::ofstream image("fractal.ppm");
  image << "P3\n" << width << " " << height << "\n255\n";

  const int maxIterations = 1000;
  const double minR = -2.5;
  const double maxR = 1.5;
  const double minI = -1.5;
  const double maxI = 1.5;

  for (int y = 0; y < height; y++) {
    for (int x = 0; x < width; x++) {
      double a = minR + (maxR - minR) * x / width;
      double b = minI + (maxI - minI) * y / height;

      double ca = a;
      double cb = b;
      int n = 0;

      while (n < maxIterations) {
        double aa = a * a - b * b;
        double bb = 2 * a * b;

        a = aa + ca;
        b = bb + cb;

        if (a * a + b * b > 16) {
          break;
        }

        n++;
      }

      int brightness = static_cast<int>(map(n, 0, maxIterations, 0, 255));
      writePixel(image, brightness, brightness, brightness);
    }
  }

  image.close();
}

double map(double value, double start1, double stop1, double start2, double stop2) {
  return ((value - start1) / (stop1 - start1)) * (stop2 - start2) + start2;
}

int main() {
  drawFractal();
  return 0;
}
```

Java:

```java
import java.awt.Color;
import java.awt.Graphics;
import java.awt.image.BufferedImage;
import javax.swing.JFrame;
import javax.swing.JPanel;

public class FractalExample extends JPanel {
    private static final int WIDTH = 800;
    private static final int HEIGHT = 800;
    private static final int MAX_ITERATIONS = 1000;
    private static final double MIN_R = -2.5;
    private static final double MAX_R = 1.5;
    private static final double MIN_I = -1.5;
    private static final double MAX_I = 1.5;

    private BufferedImage image;

    public FractalExample() {
        image = new BufferedImage(WIDTH, HEIGHT, BufferedImage.TYPE_INT_RGB);
        generateFractal();
    }

    private void generateFractal() {
        for (int x = 0; x < WIDTH; x++) {
            for (int y = 0; y < HEIGHT; y++) {
                double a = map(x, 0, WIDTH, MIN_R, MAX_R);
                double b = map(y, 0, HEIGHT, MIN_I, MAX_I);

                double ca = a;
                double cb = b;
                int n = 0;

                while (n < MAX_ITERATIONS) {
                    double aa = a * a - b * b;
                    double bb = 2 * a * b;

                    a = aa + ca;
                    b = bb + cb;

                    if (a * a + b * b > 16) {
                        break;
                    }

                    n++;
                }

                int brightness = (int) map(n, 0, MAX_ITERATIONS, 0, 255);
                Color color = new Color(brightness, brightness, brightness);
                image.setRGB(x, y, color.getRGB());
            }
        }
    }

    private double map(double value, double start1, double stop1, double start2, double stop2) {
        return ((value - start1) / (stop1 - start1)) * (stop2 - start2) + start2;
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        g.drawImage(image, 0, 0, this);
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Fractal Example");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(WIDTH, HEIGHT);
        frame.setResizable(false);
        frame.add(new FractalExample());
        frame.setVisible(true);
    }
}
```

Unity/C#:

```csharp
using UnityEngine;

public class FractalExample : MonoBehaviour
{
    public int width = 800;
    public int height = 800;
    public int maxIterations = 1000;
    public double minR = -2.5;
    public double maxR = 1.5;
    public double minI = -1.5;
    public double maxI = 1.5;

    private Texture2D fractalTexture;

    private void Start()
    {
        fractalTexture = new Texture2D(width, height);
        GetComponent<Renderer>().material.mainTexture = fractalTexture;
        GenerateFractal();
    }

    private void GenerateFractal()
    {
        for (int x = 0; x < width; x++)
        {
            for (int y = 0; y < height; y++)
            {
                double a = Map(x, 0, width, minR, maxR);
                double b = Map(y, 0, height, minI, maxI);

                double ca = a;
                double cb = b;
                int n = 0;

                while (n < maxIterations)
                {
                    double aa = a * a - b * b;
                    double bb = 2 * a * b;

                    a = aa + ca;
                    b = bb + cb;

                    if (a * a + b * b > 16)
                    {
                        break;
                    }

                    n++;
                }

                int brightness = (int)Map(n, 0, maxIterations, 0, 255);
                Color color = new Color(brightness / 255f, brightness / 255f, brightness / 255f);
                fractalTexture.SetPixel(x, y, color);
            }
        }

        fractalTexture.Apply();
    }

    private double Map(double value, double start1, double stop1, double start2, double stop2)
    {
        return ((value - start1) / (stop1 - start1)) * (stop2 - start2) + start2;
    }
}
```
