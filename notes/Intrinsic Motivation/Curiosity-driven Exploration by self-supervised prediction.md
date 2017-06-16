# Curiosity-driven Exploration by Self-supervised Prediction

### Deepak Pathak - Pulkit Agrawal - Alexei A. Efros - Trevor Darrell (2017)

## Related work:

- Recent related work in DRL:
  - Unifying Count-Based Exploration and Intrinsic Motivation. (2016)
  - Variational information maximization for intrinsically motivated reinforcement learning. (2015)


## Contributions:
  - From the paper: "_... intrisic reward signal based on prediction error of the agent's knowledge about its environment that scales to high-dimensional continuous state spaces like images, bypasses the hard problems of predicting pixels and is unaffected by the unpredictable aspects of the environment that do not affect the agent._"
  - They evaluate how can curiosity be used to transfer knowledge between different scenarios.


## Comments

  - Intrinsic reward is generated based on how hard it is for the agent to predict the outcome of its own actions. However, the systems attempts to predict only those changes in the environment that could possibly be caused by its actions (or affect the agent somehow) and ignore the rest.
  - Instead of attempting to predict raw sensory information (as pixels), they try to predict a feature representation where only relevant information is represented.
  - A neural network is trained using self-supervision to learn the inverse-dynamics: learning which action was taken given previous and current states. Since only the action is predicted, the NN has no incentive to learn non-relevant features which do not affect the agent or which are not controlled by its actions.
  - A second model (forwards dynamics model) is then trained to predict the feature representation of the next state given the current state representation and the selected action. The prediction error is then given to the agent as an intrinsic reward to __encourage curiosity__.

  - The authors mentions that there are currently no known computationally feasible mechanism for measuring learning progress. (?)

  - The authors propose to divide all sources that can modify the agent's observations into the following three cases and explain that a good feature space for curiosity should model (1) and (2) and be unaffected by (3):

    1. Things that can be controlled by the agent.
    2. Things that the agent cannot control but that can affect the agent.
    3. Things out of the agent's control and not affecting the agent.
