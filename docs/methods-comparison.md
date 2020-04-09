# Which RL Method Should I Use?

### Policy-based vs value-based

"Advantages of Policy-Based RL" https://youtu.be/KHZVXao4qXs?t=625
- better convergence properties
- effective in high-dimensional or continuous action spaces (no need to compute the max, a problem when continuous)
- can learn stochastic properties
    - useful eg rock-paper-scicorss: less predictable
    - aliased states: may lead to situations where it is stuck!

problems (at least naive methods):
- convergence to local optimum
- high variance

[^silver-lecture-7](RL Course by David Silver - Lecture 7: Policy Gradient Methods)