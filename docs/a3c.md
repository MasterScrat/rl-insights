# Asynchronous Methods for Deep Reinforcement Learning

!!! warning
    Under construction! This page is still incomplete.

!!! tldr
    - Introduces a parallel training method that uses multiple CPU cores to speed up training on a single machine.
    - The main result is A3C, a parallel actor-critic method which uses an LSTM layer, n-step returns and entropy regularization.
    - Also investigates parallel training of DQN, but with less convincing results.
    - A non-asynchronous version called A2C, geared towards GPU, is generally preferred today.[^a2c]
     
    **Published February 2016 - [arXiv](https://arxiv.org/abs/1602.01783)**

Learning faster
---

Let's start with some context. When this paper comes out in February 2016, DQN had already shown the promise of "deep" reinforcement learning, with extensions such as [Double DQN](double-dqn.md) and  [Prioritized Experience Replay](per.md) already published - but the Rainbow agent that would combine them all was still a year away. On the policy gradient front, [TPRO](trpo.md) was out, but not yet [PPO](ppo.md).

~ The concerns of learning in a stable and efficient way were even more at the forefront than right now.



The replay buffer is an efficient solution against observation non-stationarity. 
But:
- uses memory (yes)
- can't be used for off-po methods! (YES) 

To address these concerns, instead of using a replay buffer, this method executes multiple agents in parallel:
- no need   

There are multiple ways to consider efficiency of RL training:
- sample efficiency
- time efficiency

This method, as presented, has very low sample efficiency (each observation is used only once, or a few times due to n-step learning) but can be scaled up easily. Note that for off-policy method, it could very well be combined with a replay buffer!

This approach relies exclusively on CPU. 

### Summary
This paper investigates a new parallel training method which uses multiple CPU cores on the same machine, rather than relying on GPUs. Both value-based and policy-based methods are considered. 

The major result is the performance of this training scheme using an [actor-critic method](actor-critic.md).

This training scheme also shows promising results for value-based methods. However, these methods being off-policy, they can be significantly improved with the use of a replay buffer. 

The core idea is to use multiple asynchronous "actor-learners" running in different threads. Each actor-learner performs a number of learning steps, then perform an asynchronous update of the global parameters using accumulated gradients. 

Since this method is designed to train networks using a CPU, asynchronous updates made a lot of sense as it enabled [Hogwild syle](hogwild.md) updates. However, it appeared later on that this was not optimal when using a GPU. For this reason, this method is commonly used today in a synchronous way in which the updates from all the actor-learners are batched to make better use of the GPU. This non-asynchronous version is simply called **A2C** (Advantage Actor Critic) [^openai-acktr-a2c].

In hindsight
---

- ✅ Using multiple environments in parallel is a good way to decorrelate the agent's data
- ❌ Asynchronous updates are not a good match for GPU training
- ❌ Using exclusively on-policy data is very bad for sample efficiency


Key concepts
---

"Building blocks" involved in this work:

- Builds on [DQN](dqn.md) and [Actor-Critic](actor-critic.md) 
- Introduces a single-machine [parallel training](parallel-training.md) method
- Uses [entropy regularization](entropy-regularization.md)
- Uses an LSTM [Recurrent Neural Network](rnn.md)
- Uses [multi-step return](n-step-return.md) with the forward view
- Uses [shared layers](shared-layers.md) between policy and value functions
- Benchmarked on [Atari games](atari.md)

Related Links
---

- [Actor-Critic Methods: A3C and A2C](https://danieltakeshi.github.io/2018/06/28/a2c-a3c/) from Daniel Seita

[^a2c]: [OpenAI Baselines: ACKTR & A2C](https://openai.com/blog/baselines-acktr-a2c/)