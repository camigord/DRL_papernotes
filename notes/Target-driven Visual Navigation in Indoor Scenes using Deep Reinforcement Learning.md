# Target-driven Visual Navigation in Indoor Scenes using Deep Reinforcement Learning

They proposed a DRL model for visual navigation which generalizes across targets and scenes. They trained using simulated experiences (from a high-quality rendering simulator) and they were able to fine-tuned the model to generalize in real robot navigation.

### Keynotes:

- The model takes both the current state (first person view of the environment) and the target goal (image of the goal) as inputs, and it outputs an action in 3D.
- The idea is that the agent should learn how to take actions according not only to the current state, but also on the current target.
- They developed a simulation framework with high-quality 3D scenes: The House Of inteRactions (AI2-THOR). They worked with 32 different scenes representing 4 common household environments: kitchen, living room, bedroom and bathroom. Hopefully they release this environment soon XD.

