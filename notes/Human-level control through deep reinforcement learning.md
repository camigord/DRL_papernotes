# Human-level control through deep reinforcement learning

This may be the paper which is recognized for introducing deep Q-networks (although the authors had already published an initial 
paper with the name: [Playing Atari with Deep Reinforcement Learning](https://arxiv.org/abs/1312.5602)). 

Although the concept of using neural networks as function aproximators was not new, reinforcement learning was known to diverge 
or be unstable when using this kind of nonlinear functions. In their original paper, the authors proposed two very important ideas 
to solve (or alleviate) this problem:

1. The use of **Experience Replay**: In order to break the correlation between the observed experiences, they propose to store all 
these experiences (s,a,r,s',terminal) in a *replay memory*. When training the network, they use minibatches randomly sampled from 
the memory instead of the most recent observations. 

2. The use of a **Target Network**: They have two sets of identical parameters: The training network (with parameters  &theta; ) 
and the Target network (with parameters &theta;'). When training, they adjust the parameters &theta; using &theta;' as targets. The 
parameters &theta;', however, are only updated (by copying the training network parameters) every C number of steps and held fixed
between individual updates.

The proposed approach learned how to play several atari games using raw images as the only input, outperforming human players in
most of the games.

![model](https://github.com/camigord/DRL_papernotes/blob/master/assets/model.png)
