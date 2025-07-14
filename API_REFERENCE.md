## API Reference

### Vector

A 2D vector class for representing positions and velocities.

```python
# Create a vector
pos = Vector(10.0, 20.0)

# Create a random vector within bounds
random_pos = Vector.random((0, 100), (0, 100))

# Vector operations
v1 = Vector(1, 2)
v2 = Vector(3, 4)
sum_vec = v1 + v2      # Vector(4, 6)
diff_vec = v2 - v1     # Vector(2, 2)
scaled = v1 * 2.5      # Vector(2.5, 5.0)
```

### Particle

Represents a single particle in the swarm.

```python
# Create a particle at a specific position
particle = Particle(Vector(0, 0))

# Access particle properties
position = particle.pos
velocity = particle.vel
fitness = particle.fitness
personal_best = particle.p_best  # (position, fitness)
```

### Swarm

Manages a collection of particles and implements the PSO algorithm.

```python
# Create swarm with custom parameters
swarm = Swarm(
    particles=[...],           # List of Particle objects
    w=0.5,                    # Inertia weight
    c1=1.0,                   # Cognitive coefficient
    c2=2.0,                   # Social coefficient
    velocity_factor=0.1       # Velocity scaling factor
)

# Create swarm with random particles
swarm = Swarm.from_bounds(
    num_particles=100,
    x_bounds=(0, 100),
    y_bounds=(0, 100)
)

# Core methods
swarm.eval(fitness_function)  # Evaluate all particles
swarm.step()                  # Update velocities and positions
positions = swarm.get_positions()  # Get (x_coords, y_coords)

# Best solution
best_pos, best_fitness = swarm.g_best
```

## Algorithm Parameters

- **`w` (Inertia Weight)**: Controls momentum. Higher values (0.8-1.2) promote exploration, lower values (0.4-0.6) promote exploitation.
- **`c1` (Cognitive Coefficient)**: Influence of particle's personal best. Higher values increase exploration.
- **`c2` (Social Coefficient)**: Influence of swarm's global best. Higher values increase exploitation.
- **`velocity_factor`**: Scales velocity updates. Lower values (0.1-0.3) provide smoother convergence.

## Examples

See the `examples/` directory for a complete Jupyter notebook demonstrating:
- Basic PSO optimization
- Visualization of particle convergence
- Parameter tuning effects
- Real-world application scenarios

## Use Cases

- **Function Optimization**: Finding minima/maxima of mathematical functions
- **Parameter Tuning**: Optimizing hyperparameters for machine learning models
- **Engineering Design**: Optimizing design parameters
- **Educational**: Learning about swarm intelligence and optimization algorithms

## Requirements

- Python 3.6 or higher
- No external dependencies
