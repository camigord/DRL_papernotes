# Learning to Navigate in Complex Environments

In this papers the authors formulate autonomous navigation as a reinforcement learning problem and they showed that the performance of the agent 
can be improved by using *auxiliary tasks*. The idea behind these *auxiliary tasks* is to provide 'denser training signals' which would help
solving the problem of sparse rewards. 

### Keynotes:
- They tested the standard A3C algorithm with an without recurrent layers and introduced two new architectures (Nav A3C - Nav A3C+D+L).
<p align="center">
<img src="https://github.com/camigord/DRL_papernotes/blob/master/assets/navComplexEnv1.png" width="400">
</p>

- The best architecture (Nav A3C+D+L) takes a first person view of the environment as an input together with the previous reward, the relative
velocity of the agent and the previous action. The model then outputs an action policy together with a *Depth prediction* and *Loop closeru detection*
flag.

- They trained and tested on a 3D maze (DeepMind Lab).

- They proposed two auxiliary tasks:
  * Depth prediction: Their environment provides depth info which they use to train a depth prediction model. This model shares the convolution
layers of the architecture and employes two specific fully connected layers. They use a coarse resolution for the depth map. **Note: They 
claimed that using depth prediction was actually better than having the real depth as an input ('depth is much more useful for self supervision
than as input to the agent'), but I can not really understand why would the model perform better without the real depth info**.

  * Loop closure prediction: The idea is that the network should learn how to integrate the velocity vector over time and be able to determine
if there is a loop closure. Knowing if we have returned to a previously visited location can be very useful in navigation. They of course 
get this velocity vector from the environment. **Note: What would happen if we introduce noise in these velocity readings? How would this affect
the predictions?**

- The authors also present a *position decoder* in order to evaluate the internal representation of location within the agent. Their model 
achieves very good performance which shows that it learns a map representation and its own location within it.

- They made several experiments where the agent needs to reach a fixed goal starting from different random locations. It seems like the 
model learns the map and it is therefore capable of coming back to the goal faster.

<p align="center">
<img src="https://github.com/camigord/DRL_papernotes/blob/master/assets/navComplexEnv2.png" width="500">
</p>
