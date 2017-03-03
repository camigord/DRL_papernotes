# Neural Map : Structured Memory for Deep Reinforcement Learning

### Authors: Emilio Parisotto, Ruslan Salakhutdinov

## Keynotes

- The authors address the problem of providing memory to agents trained using DRL and discuss about the unsatisfactory results obtained by current architectures/methods employing simple LSTM layers or temporal convolutions.

- They propose the concept of a _Neural Map_ which represents the agent's internal memory storage. The agent can read from and write to this memory while interacting with the environment, but the writing operator is limited to affect only the part of the _neural map_ representing the area where the agent is currently located.

- They employ a modified _synchronous_ version of the [A3C](https://arxiv.org/abs/1602.01783) framework.

- They performed experiments on 2D mazes, where their model was capable of navigating the maze using local observations while also learning to reach specific target according to previously given information (it had to retain some information in memory about the goal type).

- They performed similar experiments in a 3D Doom environment where they got promising results after slightly modifying the original architecture.

- One disadvantage of the proposed approach is the need of some sort of oracle providing the current (x,y) position of the agent. The authors propose some modifications to their original and tested architecture and elaborate on the idea of _Ego-centric neural maps_. They do not provide any experimental results with these new settings, however.


## Comments

- Overall, I thinks this is an exciting paper with really promising results. However, as the authors pointed out themselves in the paper, the proposed approach presents some clear "disadvantages" or limitations:

  - The need of the current agent location: The authors present some possible modifications in order to alleviate this problem, but it is not clear how would the performance be affected based on those new settings.

  - The Neural Map dimension: The authors proposed the use of a normalization function to map from the current location (x,y) into neural map space (x',y'). However, the resolution of the neural map space will still affect the performance of the agent in large environments. 

- The idea of having a well structured memory like the _Neural Map_ capable of performing this well in the introduced experiments is quite interesting. It opens up a lot of possibilities in order to scale up this kind of systems to achieve more robust performance in more complex environments.
