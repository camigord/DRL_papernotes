# Other notes



1. From: Emotion in Reinforcement Learning Agents and Robots: A Survey

    - Examples of appraisal dimensions are novelty, recency, control and motivational relevance. These terms of course refer to abstract cognitive concepts, but in RL literature they show a large overlap with intrinsic motivation features, being independent of a specific external resource. Instead, they are functions of the agent-environment interaction history _g_ and derived model _M_.

    - For example, some appraisal theories partition novelty into three sub-elements: familiarity, suddenness and predictability (Gratch and Marsella, 2014). Each of these seem to capture different computational concepts, and such inspiration may benefit intrinsic motivation and/or planning researchers.

    - For example, Matsuda et al (2011) maintains a separate value function for fear, which is updated when the agent gets penalized. Recent work by Jacobs et al (2014) considers the positive and negative part of the state as the hope and fear signal. Another value-based approach is by Salichs and Malfaz (2012), who model the fear for a particular state as the worst historical Q-value associated with that state. As such, their model remembers particular bad locations for which it should be afraid.

    - A large group of emotional RL implementations use emotions to modify the reward function. These approaches add an additive term to the reward function that relies on emotions __(we have only encountered additive specifications)__. The reward function is given by: R<sub>t</sub> = r<sub>extern</sub> + r<sub>intern</sub>

2. From: Curiosity-driven Exploration by Self-supervised Prediction

    - An interesting direction of future research is to use the learned exploration behavior/skill as a motor primitive/low- level policy in a more complex, hierarchical system. For example, our VizDoom agent learns to walk along corridors instead of bumping into walls. This could be a useful primitive for a navigation system.

    - While the rich and diverse real world provides ample opportunities for interaction, reward signals are sparse. Our approach excels in this setting and converts unexpected interactions that affect the agent into intrinsic rewards. However our approach does not directly extend to the scenarios where “opportunities for interactions” are also rare. In theory, one could save such events in a replay memory and use them to guide exploration. However, we leave this extension for future work.

    - In Mario our agent crosses more than 30% of Level-1 without any rewards from the game. One reason why our agent is unable to go beyond this limit is the presence of a pit at 38% of the game that requires a very specific sequence of 15-20 key presses in order to jump across it. If the agent is unable to execute this sequence, it falls in the pit and dies, receiving no further rewards from the environment. Therefore it receives no gradient information indicating that there is a world beyond the pit that could potentially be explored. This issue is somewhat orthogonal to developing models of curiosity, but presents a challenging problem for policy learning.

3. From: Surprised-Based Intrinsic Motivation for Deep Reinforcement Learning

    - How to better represent _learning progress_.
