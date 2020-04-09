# Asynchronous Methods for Deep Reinforcement Learning (A3C)


!!! tldr
    Introduces **A3C - Asynchronous Advantage Actor Critic**, a  parallel training method that uses multiple CPU cores to speed up actor-critic training on a single machine. A non-asynchronous version called A2C, geared towards GPU, is generally preferred today.
     
    **Published February 2016 - Very Influential - [arXiv](https://arxiv.org/abs/1602.01783)**

### Summary
This paper investigates a new parallel training method which uses multiple CPU cores on the same machine, rather than relying on GPUs. Both value-based and policy-based methods are considered. 

The major result is the performance of this training scheme using an [actor-critic method](actor-critic.md).

This training scheme also shows promising results for value-based methods. However, these methods being off-policy, they can be significantly improved with the use of a replay buffer. 

The core idea is to use multiple asynchronous "actor-learners" running in different threads. Each actor-learner performs a number of learning steps, then perform an asynchronous update of the global parameters using accumulated gradients. 

Since this method is designed to train networks using a CPU, asynchronous updates made a lot of sense as it enabled [Hogwild syle](hogwild.md) updates. However, it appeared later on that this was not optimal when using a GPU. For this reason, this method is commonly used today in a synchronous way in which the updates from all the actor-learners are batched to make better use of the GPU. This non-asynchronous version is simply called **A2C** (Advantage Actor Critic) [^openai-acktr-a2c].

### In hindsight
- ✅ Using multiple environments in parallel is a good way to decorrelate the agent's data
- ❌ Asynchronous updates are not a good match for GPU training
- ❌ Using exclusively on-policy data is very bad for sample efficiency

### Key Concepts
- Builds on [DQN](dqn.md) and [Actor-Critic](actor-critic.md) 
- Introduces a new single-machine [Parallel Training](parallel-training.md) method
- Uses [Entropy Regularization](entropy-regularization.md)
- Uses an LSTM [Recurrent Neural Network](rnn.md)
- Uses [multi-step return](n-step-return.md) with the forward view
- Uses [shared layers](shared-layers.md) between policy and value functions

### Context
At this point, DQN had proven that value-based methods could be used to reach good performance on the [Atari domain](atari-benchmark). Multiple improvements had been proposed such as Dueling Networks, Double DQN etc, but the [Rainbow paper](rainbow) which would combine them all wasn't out yet.

On the policy gradient front, the [generalized advantage estimation](gae.md) was out.

### Related Links
- [Actor-Critic Methods: A3C and A2C](https://danieltakeshi.github.io/2018/06/28/a2c-a3c/) from Daniel Seita

[^openai-acktr-a2c]: [OpenAI Baselines: ACKTR & A2C](https://openai.com/blog/baselines-acktr-a2c/)