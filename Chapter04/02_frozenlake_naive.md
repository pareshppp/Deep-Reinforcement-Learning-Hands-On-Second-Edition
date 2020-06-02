### `DiscreteOneHotWrapper`

- Our environment has 16 discrete states
    SFFF       (S: starting point, safe)
    FHFH       (F: frozen surface, safe)
    FFFH       (H: hole, fall to your doom)
    HFFG       (G: goal, where the frisbee is located)
- At any point, the current observation space can be a value in the range 0-15 inclusive. This number denotes our agent's position in the grid.
- The action space is also a vale between 0-3 (up, down, left, right).
- But our Neural Net model expects a vector of observations as input and will produce a vector of actions as output.
- So, we use `DiscreteOneHotWrapper` to convert our discrete state/action value to a one-hot vector.
- `observation` function creates a `observation_shape` sized array of zeroes and puts `1` at the index of our agent's location in grid. Basically, creating a one-hot vector of observation space.

### `__main__`

- We wrap `gym.make("FrozenLake-v0")` in `DiscreteOneHotWrapper` to get one-hot vector as observation instead of discrete number.
- Everything else remains same as CartPole problem.