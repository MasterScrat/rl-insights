# What is Reinforcement Learning?

Reinforcement learning is a sub-field of machine learning. In reinforcement learning, our goal is to learn a *behavior*.

Let's consider an example. How would you design a self-driving car? Assume you want to design a vehicle to drive you from Paris to Berlin.

Many recent improvement in AI will come handy - image recognition could be used to locate other cars and pedestrians around you, text recognition will let you read the signs on the road, etc. 

However, the car ultimately needs to take *decisions* to bring you from point A to point B. This is where reinforcement learning takes the stage.

In reinforcement learning, we train an **agent** to decide which **action** should be performed given the current situation. In the case of our self-driving car, this agent could take low-level decisions such as the angle of the steering weel or the pressure on the gas pedal. It could also take higher-level decisions, such as the general way to take to reach the destination as fast as possible.

This kind of problems can't be handled by traditional supervised and unsupervised learning approaches. The diagram below shows how the sub-fields of machine learning interact.

<TODO>

How to learn a behavior
---

The core question of reinforcement learning is as follow:

> Given the current state, what is the optimal action in order to maximize the expected reward?

There are many approaches to tackle this question.

#### Evolution strategies

The simplest, most intuitive approach may be the **evolution strategy** family of algorithms. 
The idea is  

#### Value-based methods

[More details about value-based methods...](value-based-methods)


Reinforcement learning lingo
---

In general, the agent can not access an exhaustive description of its environment. Instead, it needs to work with an **observation** of that state.


A short history of reinforcement learning
---

The history of reinforcement learning is actually nothing but short.

The field as it exists today combines elements from different directions.