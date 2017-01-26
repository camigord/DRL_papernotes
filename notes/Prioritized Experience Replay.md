# Prioritized Experience Replay 

The contribution of the paper is quite simple to understand but also very useful. Until now, we have been creating an experience replay buffer where we store all the experiences we collect from the environment, and from which we can then randomly sample minibatches in order to train our network. The authors, however, propose that some experiences may be more *useful* or *interesting* than others: *"... an RL agent can learn more effectively from some transitions than from others."*

*"Experience replay liberates agents from processing transitions in the exact order they are experienced. Prioritized replay further liberates agents from considering transitions with the same frequency that they are experienced."*

### Keynotes:

- They assign a *priority* to each one of the collected experiences and they sample based on these priorities.
- They propose to use the temporal-difference (TD) error as the criterion by which the importance of each transition is measured.
- Replay transitions with a higher TD error more frequently (because these transitions are still *surprising* or they present a better opportunity to learn...).
- They propose a stochastic prioritization approach in order to avoid overfitting and lack of diversity when training. 
- They proposed two approaches for sampling: *Rank-based* and *Proportional prioritization*.
- The paper also introduces some implementation issues (for memory efficiency) and propose some solutions which I will not discuss here.

### Others:

- They authors mention that their approach addresses the problem of knowing which experiences to replay and how to do it, but they do not address the problem of knowing which experiences to store.
