# pypsoa

A simple, zero-dependency Particle Swarm Optimization (PSO) library for Python.

`pypsoa` is a lightweight implementation of the Particle Swarm Optimization algorithm, designed for educational purposes and simple optimization tasks. It provides a clean, object-oriented interface with no external dependencies beyond Python's standard library.

## Features

- **Zero Dependencies**: Only requires Python standard library
- **Simple API**: Easy-to-use classes for Vector, Particle, and Swarm
- **Educational**: Clear implementation perfect for learning PSO concepts
- **Flexible**: Customizable parameters for different optimization scenarios
- **2D Optimization**: Optimized for 2-dimensional search spaces

## Installation

```bash
pip install pypsoa
```

Or install from source:

```bash
git clone https://github.com/atasoglu/pypsoa.git
cd pypsoa
pip install .
```

## Quick Start

```python
import math
from pypsoa import Vector, Swarm

# Define a fitness function (minimize distance to target)
target = Vector(50, 50)
def fitness_function(pos):
    return math.sqrt((pos.x - target.x)**2 + (pos.y - target.y)**2)

# Create a swarm with 50 particles
swarm = Swarm.from_bounds(
    num_particles=50,
    x_bounds=(0, 100),
    y_bounds=(0, 100),
    w=0.5,  # inertia weight
    c1=1.0, # cognitive coefficient
    c2=2.0  # social coefficient
)

# Run optimization for 20 iterations
for _ in range(20):
    swarm.step()      # Update particle positions
    swarm.eval(fitness_function)  # Evaluate fitness

# Get best solution
best_position, best_fitness = swarm.g_best
print(f"Best position: {best_position}")
print(f"Best fitness: {best_fitness}")
```

See [API Reference](API_REFERENCE.md) for more details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - see LICENSE file for details.