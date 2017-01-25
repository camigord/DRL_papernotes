# Target-driven Visual Navigation in Indoor Scenes using Deep Reinforcement Learning

They proposed a DRL model for visual navigation which generalizes across targets and scenes. They trained using simulated experiences (from a high-quality rendering simulator) and they were able to fine-tune the model to generalize in real robot navigation.

### Keynotes:

- The model takes both the current state (first person view of the environment) and the target goal (image of the goal) as inputs, and it outputs an action in 3D.
- The idea is that the agent should learn how to take actions according not only to the current state, but also on the current target.
- They developed a simulation framework with high-quality 3D scenes: The House Of inteRactions (AI2-THOR). They worked with 32 different scenes representing 4 common household environments: kitchen, living room, bedroom and bathroom. Hopefully they release this environment soon XD.
- They used a discrete set of actions (forward, backwards, turn left, turn right). They added some gaussian noise to the actions in order to simulate system dynamics.
- They focused on minimizing the trajectory length of the navigation. They provided a reward when reaching the target and a small time penalty as immediate reward.
- They proposed the 'siamese model' presented in the next figure. They used actor-critic methods to train the model using DRL.

<p align="center">
<img src="https://github.com/camigord/DRL_papernotes/blob/master/assets/targetDriven.png" width="600">
</p>

- They have 'scene specific' layers which are used to generalize across targets within the same scene. 
- When training, each A3C thread uses a different target. 

### Experiments:

1. Navigation: They compared their performance against heuristic strategies and other DRL models. They showed that their model converges faster and achieves shorter trajectory paths. They claimed that their model may be learning a rough map of the environment (or scenes) and it can therefore localize itself with respect to the input target.

  * I do not understand and they do not clarify, however, how did they train the standard A3C models. Were these models trained using fixed targets? Were they trained using different targets, and in that case how did the models know about where they were supposed to go? I guess that if you do not have your target as an input, the only thing the network can do is to randomly move looking for common targets...
  
2. Generalizing across targets: Their model seems to be capable of remembering not only the location of the targets used during training, but also the location of nearby objects (objects which were never used during training). As the distance between these objects and the trained targets gets larger, however, the success rate decreases.

3. Robot experiments: They were able to transfer knowledge from the simulation training into a real robot navigation task. However, the real scenes were quite small, so I am not sure if the robot can handle more complex environments.
