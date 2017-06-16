# Hierarchical Deep Reinforcement Learning: Integrating Temporal Abstraction and Intrinsic Motivation

They present a framework that integrates DRL with hierarchical value functions (h-DQN) where the agent is motivated to solve intrinsic goals to aid exploration of the state space. They propose that intrinsic motivation can help the agent with the problem of sparse rewards. The show very good results in some Atari games like *Montezuma's Revenge* where previous approaches did not perform nearly as well.

### Keynotes:

- The agent learns value functions which are not only functions of the state *s* but also of the current goal *g*: V(s,g).
- The agent learns to achieve *intrinsically generated* goals and then it learns how to properly chain these policies together in order to achieve global (extrinsic) goals.
- They approximate the value function V using NN: V(s,g; &theta;).
- They have a hierarchical representation where a *meta-controller* takes the current state and proposes a new goal. The low-level *controller* is then responsible for reaching this goal by properly selecting actions. Once the goal is reached or the episode terminates, the *meta-controller* selects a new goal.
- The *meta-controller* runs at a slower time-scale than the *controller*. It collects one *experience transition* only after the *controller* has experienced several steps and performed several actions.
- Two DQN's are implemented. One for the *meta-controller* and one for the *controller*. These networks are trained normally using the individual experience replay buffers.

 #### Meta-controller:
 - Receives a state *s<sub>t</sub>* and chooses a goal *g<sub>t</sub>* ∈ *G*. Where *G* denotes all set of possible current goals and is predefined by the authors according to the environment/task.
 - The *meta-controller's* objective is to maximize the *extrinsic reward* received from the environment.
 - It collects transitions (*s<sub>t</sub>*,*g<sub>t</sub>*,*f<sub>t</sub>*,*s<sub>t+1</sub>*) and stores them in a replay memory for training. Where *f<sub>t</sub>* is the extrinsic reward.

 #### Controller:
 - Takes the current state *s<sub>t</sub>* and goal *g<sub>t</sub>* and selects an action *a<sub>t</sub>*.
 - The goal *g<sub>t</sub>* remains fixed for the next few steps either until it is achieved or a terminal state is reached.
 - The internal critic is in charge of evaluating whether the goal is achieved or not and provides an appropriate *intrinsic reward* *r<sub>t</sub>(g)*.
 - The controller's objective is to maximize this intrinsic reward.
 - It collects transitions (*s<sub>t</sub>*,*a<sub>t</sub>*,*g<sub>t</sub>*,*r<sub>t</sub>*,*s<sub>t+1</sub>*)

### Atari experiments - Montezuma's Revenge:
- Use of entities or objects in the scene to parameterize goals.
- They built a custom object detector from images to provide object/goals candidates.
- The internal critic is defined in the space <*entity<sub>1</sub>*,*relation*,*entity<sub>2</sub>*>, where *relation* defines a configuration of the *entities* (like for example: *entity<sub>1</sub>* reaches *entity<sub>2</sub>*).
- The agent is free to choose *entity<sub>2</sub>*.
  * They only handle one relation: entity *reaches* entity... but they propose to develop a parameterized intrinsic reward function given entities as future work.

<hr>

## Comments:

- I like both the ideas of a having hierarchical approach and using intrinsic motivation. Given that we are talking about reinforcement learning, however, it would be useful if the agent could learn how to set internal goals on its own, without the need of predefining a fixed set of goals.
- Moreover, the development of the *internal critic* looks like a really exciting field of research. Right now, a limited amount of *relations* needs to be defined. It could be possible for the critic to evolve autonomously by learning more complex relations or high-level abstractions: instead of evaluating if <*entity<sub>1</sub>* reaches *entity<sub>2</sub>*>, it could evaluate if <*entity<sub>door</sub>* is now *open*>.
