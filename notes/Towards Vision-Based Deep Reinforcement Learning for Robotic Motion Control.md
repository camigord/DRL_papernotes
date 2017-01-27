# Towards Vision-Based Deep Reinforcement Learning for Robotic Motion Control

The authors developed a system for learning target reaching with a 3-joint robot manipulator using a standard DQN. They use visual perception only. The results, however, are not very promising neither in simulation nor in real-world experiments.

### Keynotes:
- They created a 2D simulation environment to train the network (simulating a 3-joint robot manipulator). 
- The network has 9 discrete actions, 3 for each joint: increase/decrease joint angle and hold. The step is constant (0.02 rad).
- Their reward function is quite simple and would not work in all cases: Give a positive reward if end-effector gets closer to target or negative reward otherwise.
- They train the model using the simulator and introducing different noise sources. The results when testing on simulated data, however, do not look very promising...
- The model failed when tested on real world images with a success rate of 0.
