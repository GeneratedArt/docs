---
title: Particle systems (PS)
subtitle: Particle systems are computational models used to simulate the behavior and movement of individual particles in a dynamic system.
tags: [algorithm]
author:
---

Particle systems are computational models used to simulate the behavior and movement of individual particles in a dynamic system. Each particle in the system is typically governed by a set of rules and parameters, which determine its motion, appearance, and interaction with other particles or forces in the environment. Particle systems are often used to simulate natural phenomena like fire, smoke, water, or flocking behavior.

Examples of math formulas used in Particle Systems include:

1. Newton's Laws of Motion: Particle systems often use Newton's laws to calculate the acceleration, velocity, and position of each particle based on the applied forces and initial conditions.

2. Verlet Integration: Verlet integration is a numerical integration method used to update the positions and velocities of particles based on their acceleration and previous state. It provides stable and accurate particle motion simulation.

3. Force Fields: Particle systems can incorporate various force fields, such as gravity, wind, or magnetic fields, using mathematical formulas that define the strength, direction, and distance-dependent effects of these forces on particles.

4. Collision Detection and Response: Particle systems employ collision detection algorithms to detect intersections between particles or particles and obstacles. The response to collisions can involve calculations based on conservation of momentum or energy.

Algorithms that derive from Particle Systems include:

1. Boids Algorithm: The Boids algorithm simulates the flocking behavior of birds, where each particle (boid) follows simple rules of alignment, separation, and cohesion to create realistic flocking patterns.

2. Fluid Simulation Algorithms: Various algorithms simulate fluid dynamics, such as smoothed-particle hydrodynamics (SPH) or lattice Boltzmann methods, to model the behavior of liquids or gases in a particle system.

Particle systems can be used in Generative Art in various ways:

1. Visual Effects: Particle systems can create visually stunning effects like fire, smoke, explosions, or flowing water. By manipulating parameters such as particle size, color, lifespan, and behavior, artists can generate dynamic and visually appealing animations or still images.

2. Natural Phenomena: Particle systems can simulate natural phenomena such as clouds, rain, snow, or swarms of insects. Artists can adjust the rules and parameters to create realistic or stylized representations of these phenomena.

3. Interactive Art: Particle systems can be used in interactive installations or games where user input or other external factors influence the behavior of particles. Artists can design interactive experiences where users can manipulate particles or affect their motion through gestures, sounds, or other interactive elements.

4. Data Visualization: Particle systems can be used to visualize complex datasets by mapping data attributes to particle properties. This can help represent information in a visually intuitive and engaging manner, revealing patterns, relationships, or dynamics within the data.

Particle systems provide artists with a versatile toolset for creating dynamic and interactive visual experiences. They allow for the generation of lifelike and fluid animations, as well as the representation of complex phenomena or datasets in a visually appealing way.

Certainly! Here are code examples of implementing particle systems using Processing (Java-based language for visual arts) and Python:

Processing (Java):

```java
import processing.core.PApplet;

class Particle {
  float x, y;
  float speedX, speedY;
  float radius;
  float colorR, colorG, colorB;
  
  Particle(float x, float y, float speedX, float speedY, float radius, float colorR, float colorG, float colorB) {
    this.x = x;
    this.y = y;
    this.speedX = speedX;
    this.speedY = speedY;
    this.radius = radius;
    this.colorR = colorR;
    this.colorG = colorG;
    this.colorB = colorB;
  }
  
  void update() {
    x += speedX;
    y += speedY;
    
    if (x < 0 || x > width) {
      speedX *= -1;
    }
    if (y < 0 || y > height) {
      speedY *= -1;
    }
  }
  
  void display() {
    fill(colorR, colorG, colorB);
    ellipse(x, y, radius * 2, radius * 2);
  }
}

public class ParticleSystem extends PApplet {
  int numParticles = 100;
  Particle[] particles = new Particle[numParticles];
  
  public void settings() {
    size(800, 800);
  }
  
  public void setup() {
    for (int i = 0; i < numParticles; i++) {
      float x = random(width);
      float y = random(height);
      float speedX = random(-1, 1);
      float speedY = random(-1, 1);
      float radius = random(5, 20);
      float colorR = random(255);
      float colorG = random(255);
      float colorB = random(255);
      
      particles[i] = new Particle(x, y, speedX, speedY, radius, colorR, colorG, colorB);
    }
  }
  
  public void draw() {
    background(255);
    
    for (int i = 0; i < numParticles; i++) {
      particles[i].update();
      particles[i].display();
    }
  }
  
  public static void main(String[] args) {
    PApplet.main("ParticleSystem");
  }
}
```

Python

```python
import random
import pygame

class Particle:
    def __init__(self, x, y, speed_x, speed_y, radius, color):
        self.x = x
        self.y = y
        self.speed_x = speed_x
        self.speed_y = speed_y
        self.radius = radius
        self.color = color
    
    def update(self):
        self.x += self.speed_x
        self.y += self.speed_y
        
        if self.x < 0 or self.x > width:
            self.speed_x *= -1
        if self.y < 0 or self.y > height:
            self.speed_y *= -1
    
    def display(self):
        pygame.draw.circle(screen, self.color, (int(self.x), int(self.y)), self.radius)

pygame.init()
width, height = 800, 800
screen = pygame.display.set_mode((width, height))
clock = pygame.time.Clock()

num_particles = 100
particles = []

for _ in range(num_particles):
    x = random.uniform(0, width)
    y = random.uniform(0, height)
    speed_x = random.uniform(-1, 1)
    speed_y = random.uniform(-1, 1)
    radius = random.uniform(5, 20)
    color = (random.randint(0, 255), random.randint(0, 255), random.randint(0, 255))
    
    particles.append(Particle(x, y, speed_x, speed_y, radius, color))

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            exit()
    
    screen.fill((255, 255, 255))
    
    for particle in particles:
        particle.update()
        particle.display()
    
    pygame.display.flip()
    clock.tick(60)
```
JavaScript:

```javascript
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
const width = canvas.width;
const height = canvas.height;

class Particle {
  constructor(x, y, speedX, speedY, radius, color) {
    this.x = x;
    this.y = y;
    this.speedX = speedX;
    this.speedY = speedY;
    this.radius = radius;
    this.color = color;
  }

  update() {
    this.x += this.speedX;
    this.y += this.speedY;

    if (this.x < 0 || this.x > width) {
      this.speedX *= -1;
    }
    if (this.y < 0 || this.y > height) {
      this.speedY *= -1;
    }
  }

  display() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, 2 * Math.PI);
    ctx.fillStyle = this.color;
    ctx.fill();
    ctx.closePath();
  }
}

const numParticles = 100;
const particles = [];

for (let i = 0; i < numParticles; i++) {
  const x = Math.random() * width;
  const y = Math.random() * height;
  const speedX = Math.random() * 2 - 1;
  const speedY = Math.random() * 2 - 1;
  const radius = Math.random() * 5 + 1;
  const color = `rgba(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255}, 1)`;

  particles.push(new Particle(x, y, speedX, speedY, radius, color));
}

function updateParticles() {
  for (let i = 0; i < particles.length; i++) {
    particles[i].update();
  }
}

function drawParticles() {
  ctx.clearRect(0, 0, width, height);

  for (let i = 0; i < particles.length; i++) {
    particles[i].display();
  }
}

function animate() {
  updateParticles();
  drawParticles();
  requestAnimationFrame(animate);
}

animate();
```
C++ using the SFML library:

```cpp
#include <SFML/Graphics.hpp>
#include <random>

struct Particle {
    sf::Vector2f position;
    sf::Vector2f velocity;
    float radius;
    sf::Color color;
};

int main()
{
    const int width = 800;
    const int height = 800;

    sf::RenderWindow window(sf::VideoMode(width, height), "Particle System");
    window.setFramerateLimit(60);

    std::vector<Particle> particles;
    std::random_device rd;
    std::mt19937 gen(rd());
    std::uniform_real_distribution<float> dist(-1.0f, 1.0f);
    std::uniform_real_distribution<float> colorDist(0.0f, 1.0f);

    const int numParticles = 100;
    for (int i = 0; i < numParticles; ++i) {
        Particle particle;
        particle.position = sf::Vector2f(width / 2.0f, height / 2.0f);
        particle.velocity = sf::Vector2f(dist(gen), dist(gen));
        particle.radius = 5.0f;
        particle.color = sf::Color(colorDist(gen) * 255, colorDist(gen) * 255, colorDist(gen) * 255);
        particles.push_back(particle);
    }

    while (window.isOpen()) {
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed) {
                window.close();
            }
        }

        window.clear();

        for (auto& particle : particles) {
            particle.position += particle.velocity;

            if (particle.position.x < 0 || particle.position.x > width) {
                particle.velocity.x *= -1;
            }
            if (particle.position.y < 0 || particle.position.y > height) {
                particle.velocity.y *= -1;
            }

            sf::CircleShape circle(particle.radius);
            circle.setPosition(particle.position);
            circle.setFillColor(particle.color);
            window.draw(circle);
        }

        window.display();
    }

    return 0;
}
```

In this example, the code uses the SFML library to create a window for rendering the particle system. Each particle is represented by the `Particle` struct, which contains the position, velocity, radius, and color. The particles are randomly initialized and updated within the main loop, bouncing off the walls of the window. The particle system is rendered by creating and drawing `sf::CircleShape` objects for each particle.

Make sure to link the SFML library when compiling the code. For example, using g++:

```
g++ -o particles main.cpp -lsfml-graphics -lsfml-window -lsfml-system
```

Note: The SFML library is not included in the standard C++ library, so you will need to install and configure it separately to compile and run the code successfully.

Sure! Here are code examples of implementing a particle system in Java and Unity/C#:

Java:

```java
import java.awt.Color;
import java.awt.Graphics;
import java.util.ArrayList;
import java.util.List;
import javax.swing.JFrame;
import javax.swing.JPanel;

class Particle {
    private float x;
    private float y;
    private float velocityX;
    private float velocityY;
    private float radius;
    private Color color;

    public Particle(float x, float y, float velocityX, float velocityY, float radius, Color color) {
        this.x = x;
        this.y = y;
        this.velocityX = velocityX;
        this.velocityY = velocityY;
        this.radius = radius;
        this.color = color;
    }

    public void update() {
        x += velocityX;
        y += velocityY;

        if (x < 0 || x > width) {
            velocityX *= -1;
        }
        if (y < 0 || y > height) {
            velocityY *= -1;
        }
    }

    public void display(Graphics g) {
        g.setColor(color);
        g.fillOval((int) (x - radius), (int) (y - radius), (int) (radius * 2), (int) (radius * 2));
    }
}

public class ParticleSystem extends JPanel {
    private static final int WIDTH = 800;
    private static final int HEIGHT = 800;
    private static final int NUM_PARTICLES = 100;
    private static final int MAX_RADIUS = 10;

    private List<Particle> particles;

    public ParticleSystem() {
        particles = new ArrayList<>();
        for (int i = 0; i < NUM_PARTICLES; i++) {
            float x = (float) (Math.random() * WIDTH);
            float y = (float) (Math.random() * HEIGHT);
            float velocityX = (float) (Math.random() * 2 - 1);
            float velocityY = (float) (Math.random() * 2 - 1);
            float radius = (float) (Math.random() * MAX_RADIUS);
            Color color = new Color((int) (Math.random() * 256), (int) (Math.random() * 256), (int) (Math.random() * 256));

            particles.add(new Particle(x, y, velocityX, velocityY, radius, color));
        }
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        for (Particle particle : particles) {
            particle.update();
            particle.display(g);
        }
        repaint();
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Particle System");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(WIDTH, HEIGHT);
        frame.setResizable(false);
        frame.add(new ParticleSystem());
        frame.setVisible(true);
    }
}
```

Unity/C#:

```csharp
using UnityEngine;

public class ParticleSystem : MonoBehaviour
{
    public int numParticles = 100;
    public float maxRadius = 10f;
    public float maxSpeed = 1f;
    public Color[] colors;

    private Particle[] particles;

    private void Start()
    {
        particles = new Particle[numParticles];
        for (int i = 0; i < numParticles; i++)
        {
            Vector3 position = new Vector3(Random.Range(0f, 1f), Random.Range(0f, 1f), 0f);
            Vector3 velocity = new Vector3(Random.Range(-maxSpeed, maxSpeed), Random.Range(-maxSpeed, maxSpeed), 0f);
            float radius = Random.Range(1f, maxRadius);
            Color color = colors[Random.Range(0, colors.Length)];

            particles[i] = new Particle(position, velocity, radius, color);
        }
    }

    private void Update()
    {
        for (int i = 0; i < numParticles; i++)
        {
            particles[i].Update();
        }
    }

    private void OnDrawGizmos()
    {
        for (int i = 0; i < numParticles; i++)
        {
            particles[i].Display();
        }
    }
}

public class Particle
{
    private Vector3 position;
    private Vector3 velocity;
    private float radius;
    private Color color;

    public Particle(Vector3 position, Vector3 velocity, float radius, Color color)
    {
        this.position = position;
        this.velocity = velocity;
        this.radius = radius;
        this.color = color;
    }

    public void Update()
    {
        position += velocity;

        if (position.x < 0f || position.x > 1f)
        {
            velocity.x *= -1f;
        }
        if (position.y < 0f || position.y > 1f)
        {
            velocity.y *= -1f;
        }
    }

    public void Display()
    {
        Gizmos.color = color;
        Gizmos.DrawSphere(position, radius);
    }
}
```
