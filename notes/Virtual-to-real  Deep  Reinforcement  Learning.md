# Virtual-to-real  Deep  Reinforcement  Learning: Continuous  Control  of  Mobile  Robots  for  Mapless  Navigation

### Authors: Lei Tai, Giuseppe Paolo, Ming Liu

## Keynotes

- They focus on robot navigation both in simulated and real environments using asynchronous DRL.
- The system takes as inputs: A 10-dimensional laser scan, a 2D vector containing the previous velocity
 and a 2D coordinate of the relative target position.
- The range information is normalized to (0,1). The target position is represented in polar coordinates
(distance and angle).
- The 2D action velocities include the angular and linear velocities of the differential mobile robot.
- The model then outputs a continuous control action.
- They trained the model using Async DRL to learn how to arrive to the target while avoiding obstacles.
- The reason why they can "transfer" knowledge from simulated runs into real worlds scenarios is that
they used a "highly abstracted" representation of the environments by employing laser scans and by
considering only 10-dimensional measurements (10 directions sampled between -90 and 90 degrees in a fixed
angle distribution).
- They claim that this simplification allows them to reduce the gap between simulation and real world and
that it also would allows them to use low-cost range sensors.

- They present an asynchronous extension of the [DDPG](https://arxiv.org/abs/1509.02971) algorithm for continuous control which seems to be more efficient than the original version.

- The reward function was designed so that reaching the goal or getting closer to it was rewarded while collisions were penalized. The inconvenience with this approach is that in some environments, where a direct trajectory between current position and the target is not available, the agent will not be able to learn to perform detours or surround obstacles.

## Comments

- I find the idea of using "simplified" laser scans to obtain simple abstractions about our current state and allow transferring knowledge between simulation and real world scenarios quite interesting. However, the reward function that the authors propose will not allow the agent to solve complex environments. This is probably a problem of every mapless approach; given that the agent has no historical information of where it has been in relation to the target, it can only hope that getting closer will lead to reaching it, which is not always the case.
