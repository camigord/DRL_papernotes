# Surprised-Based Intrinsic Motivation for Deep Reinforcement Learning

### Joshua Achiam & Shankar Sastry - UC Berkeley - (ICLR 2017)

## Related work:

- In-depth reviews about the types of intrinsic motivation:
  - Novelty or Surprise? Andrew Barto,Marco Mirolli, and Gianluca Baldassarre. (2013)
  - How can we define intrinsic motivation? Pierre-Yves Oudeyer and Frederic Kaplan. (2008)


- Recent related work in DRL:
  - Unifying Count-Based Exploration and Intrinsic Motivation. (2016)
    - __Difference__: Current paper learns a transition model as opposed to a state-action occupancy density.
  - Variational Information Maximizing Exploration. (2016)
    - __Difference__: Current paper learns a single deep dynamics model instead of maintaining a distribution over possible dynamics.
  - Incentivizing Exploration In Reinforcement LearningWith Deep Predictive Models. (2015)
    - __Difference__: Current paper encompasses environments with stochastic dynamics.

## Contributions:
- Investigate surprisal and learning progress as intrinsic rewards and demonstrate that these incentives result in efficient exploration.

- Efficient method for learning transition model together with policy.

## Comments

- Learn transition model together with the policy.
- Use the surprisal of a transition as an intrinsic reward. They propose two methods:
  1. The intrinsic reward is the surprisal of getting into _s'_ given the current model P<sub>&phi;</sub> and the context _(s,a)_ -> P<sub>&phi;</sub>(_s'\s,a_)
  2. The intrinsic reward is the _k_-step learning progress, which is defined as the difference between the model output after _k_ updates and the model output before the updates.
- They discussed that, ideally, as the model learns the transition dynamics of the environment, the intrinsic rewards should decrease to 0. This is true for the second method but not necessarily for the first one where the system could try to reach the states with the noisiest transitions.
- They normalize the intrinsic reward by keeping it upper-bounded thus keeping its scale fixed with respect to the extrinsic reward. This seems to improve the stability of the algorithm.
- They concluded that surprisal (1st method) worked better than learning progress (2nd method).

## Future work:

  - How to better represent _learning progress_.
