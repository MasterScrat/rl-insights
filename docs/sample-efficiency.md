TODO
- Improving Sample Efficiency in Model-Free Reinforcement Learning from Images https://arxiv.org/abs/1910.01741

> This need for sample efficiency is even more compelling
when agents are deployed in the real world

-- ACER paper

> A number of approaches have been proposed in the literature
to address the sample inefficiency of deep RL algorithms.
Broadly, they can be classified into two streams of research,
though not mutually exclusive: (i) Auxiliary tasks on the
agent’s sensory observations; (ii) World models that predict
the future. While the former class of methods use auxiliary
self-supervision tasks to accelerate the learning progress of
model-free RL methods (Jaderberg et al., 2016; Mirowski
et al., 2016), the latter class of methods build explicit predictive models of the world and use those models to plan
through or collect fictitious rollouts for model-free methods to learn from (Sutton, 1990; Ha & Schmidhuber, 2018;
Kaiser et al., 2019; Schrittwieser et al., 2019).

-- CURL paper

> The DMControl suite has been used widely by
  Yarats et al. (2019), Hafner et al. (2018), Hafner et al. (2019)
  and Lee et al. (2019) for benchmarking sample-efficiency
  for image based continuous control methods. As for Atari,
  Kaiser et al. (2019) propose to use the 100k interaction steps
  benchmark for sample-efficiency which has been adopted
  in Kielak (2020); van Hasselt et al. (2019). The Rainbow
  DQN (Hessel et al., 2017) was originally proposed for maximum sample-efficiency on the Atari benchmark and in
  recent times has been adapted to a version known as DataEfficient Rainbow (van Hasselt et al., 2019) with competitive performance to SimPLe without learning world models.
  
-- CURL paper

> We measure the data-efficiency and performance of our
  method and baselines at 100k interaction steps on both DMControl and Atari, which we will henceforth refer to as
  DMControl100k and Atari100k for clarity. Benchmarking at 100k steps makes for a fixed experimental setup that
  is easy to reproduce and has been common practice when
  investigating data-efficiency on Atari Kaiser et al. (2019);
  Kielak (2020). A broader motivation is that while RL al-
  CURL: Contrastive Unsupervised Representations for Reinforcement Learning
  gorithms can achieve super-human performance on many
  Atari games, they are still far from the data-efficiency of a
  human learner. Training for 100k steps is within the order
  of magnitude that we would expect for humans to a learn
  similar tasks. In our experiments, 100k steps corresponds
  to 300-400k frames (due to using a frame-skip of 3 or 4),
  which equates to roughly a 2-4 hours of human game play.
  
-- CURL paper