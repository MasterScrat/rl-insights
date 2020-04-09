# Actor-Critic Algorithms

!!! tldr
    Introduces **Actor-Critic Algorithms**.
     
    **Published February 2016 - Very Influential - [Link](https://papers.nips.cc/paper/1786-actor-critic-algorithms.pdf)**

### Summary

This paper introduces the the notion of actor-critic methods, which is the basis of a large part of the [reinforcement learning methods](rl-approaches.md) today.  

This idea is to combine a value-function approximation, the critic, which helps reduce the variance of a policy-gradient approximation, the actor.

This idea will further be extended with the notion of *advantage*.


Note that this work only considers linear approximations, ie it doesn't use neural networks.

In the actor-critic setting, learning the critic can be seen as a supervised learning problem. This means it can either be learned using TD-learning, or simply least square.

It is important to understand that the goal of the critic is to approximate the returns that the actor will receive, and not the returns of the optimal policy. 
But the critic is regularly updated, which means that the critic is trying to learn a moving target! in practice, this is not a problem as the actor is updated more slowly than the critic

Silver lecture on PG methods: https://www.youtube.com/watch?v=KHZVXao4qXs (actor-critic from https://youtu.be/KHZVXao4qXs?t=3178)

Pretty much all the gradient-based approaches are now actor-critic methods, so this doesn't mean much anymore! https://github.com/openai/spinningup/issues/156#issuecomment-494596739



TODO cover Degris paper, the original resource for off-policy AC: https://arxiv.org/abs/1205.4839