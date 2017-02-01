# Asynchronous Methods for Deep Reinforcement Learning

The basic idea of this paper is to replace the Exp. Replay used in DRL by using multiple agents executed in parallel. The authors were able not only to outperform previous methods but also to speed up training significantly. The idea is quite simple in general, but the results are outstanding. They tested different RL methods: Q-learning, Sarsa, n-step Q-learning, and advantage actor-critic.

### Keynotes:

- Replace the use of experience replay by executing several agents in parallel on multiple instances of the environment. 
- Learning from the experiences collected from different agents stabilizes the training process: the parallelism decorrelates the experiences.
- Removing Exp. Replay allows them to use on-policy RL methods. 
- In general, all the agents share the network parameters and update these parameters asynchronously every N steps. 
- They pointed out that the different agents could have different exploration strategies, thus improving the diversity of collected experiences. 
- They obtained a reduction in training time which is roughly linear in the number of parallel agents. 
- They evaluated different optimization methods in order to test their performance when using asynchronous updates. They propose a version of the RMSProp which they call Shared RMSProp.
