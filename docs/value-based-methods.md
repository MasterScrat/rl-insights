# Value-Based Methods


> However, we need to do better than deep Q-learning, because it has two important
  limitations. First, the deterministic nature of the optimal policy limits its use in adversarial domains.
  Second, finding the greedy action with respect to the Q function is costly for large action spaces.

-- ACER https://arxiv.org/pdf/1611.01224.pdf


> Such methods are indirect
in the sense that they do not try to optimize directly over a policy space. A
method of this type may succeed in constructing a "good" approximation of
the value function, yet lack reliable guarantees in terms of near-optimality
of the resulting policy. 

-- Actor Critic https://papers.nips.cc/paper/1786-actor-critic-algorithms.pdf