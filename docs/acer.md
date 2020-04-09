# Sample Efficient Actor-Critic with Experience Replay (ACER)

!!! warning
    Under construction! This page is still vastly incomplete.

!!! tldr
    **ACER** - Actor-Critic with Experience Replay extends the parallel implementation of actor-critic methods described in A3C to the off-policy setting.

    **Published November 2016 - Influential (251 citations) - [arXiv](https://arxiv.org/abs/1611.01224)**

### Summary

> "ACER may be understood as the off-policy counterpart of the [A3C method](a3c.md)."

### Key concepts

- Uses ?? for variance reduction (GAE?)
- Uses [Generalized Advantage Estimation](generalized-advantage-estimation.md)
- Uses the the off-policy [Retrace](retrace.md) algorithm
- Uses parallel-training as in A3C
- Introduces Truncated Importance Sampling
- Introduces stochastic dueling network architectures
- Introduces efficient trust region policy optimization

### Legacy
- Used in [PPO](proximal-policy-optimization.md) (?)