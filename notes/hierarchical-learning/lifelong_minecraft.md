# A Deep Hierarchical Approach to Lifelong Learning in Minecraft
---
### Authors:
<p align="center">
  Chen Tessler, Shahar Givony, Tom Zahavy, Daniel J. Mankowitz, Shie Mannor
</p>


### Summary:

- Authors propose a Hierarchical Deep Reinforcement Learning Network (_H-DRLN_) capable of reusing previously learned _skills_.

- The architecture was tested on _Minecraft_.

- The main idea is to learn _skills_ by solving sub-problems in the environment. These sub-problems are usually much simpler than the final task and allow the system to understand the dynamics of the environment and to learn "basic" behaviors which can be very useful in other scenarios. Building a house, for example, can be decomposed into several sub-problems like chopping wood, collecting materials and finally assembling the house.

- To learn reusable skills in a lifelong learning setting the systems must:

  - Learn skills
  - Learn when a skill should be used and reused
  - Efficiently accumulate skills


### Model:

<p align="center">
  <img src="./assets/image4.jpg">
</p>

The _H-DRLN_ architecture is shown in the figure above. The controller learns to solve complex tasks by learning reusable skills in the form of pre-trained _Deep Skill Networks (DSNs)_ (trained a-priori on various sub-tasks using DQN). These skills are __retained__ by incorporating them into a _Deep Skill module_. Given an input state _s_ and a skill index _i_, the _Deep Skill module_ outputs an action _a_ according to the corresponding DSN policy. The authors proposed and tested two types of _Deep Skill modules_:

  1. DSN array: an array of pre-trained DSNs where each DSN is represented by a separate DQN
  2. _Multi-skill distillation_ network: a single deep network that represents multiple DSNs. All the DSNs share the hidden layers while a separate output layer is trained for each DSN via policy distillation. This approach makes the architecture scalable with respect to the number of skills.

As shown in the figure, the _H-DRLN_ controller learns a policy that determines when to use primitive actions and when to _reuse_ pre-learned _skills_. If a primitive action is chosen, that action is executed for one time step. If the controller chooses to execute a skill _i_, then DSN _i_ wull execute its policy until termination.

The authors properly modify the objective function to incorporate skills and define an experience replay memory capable of storing skill experiences.

### Experiments:

The authors trained DSNs in sub-domains of Minecraft by defining "simple" problems like navigating from one point to another, picking up objects or breaking stones. These setups were simple enough that a DQN was capable of reaching a 100% success rate in all of them.

Once the DSNs had been trained, the authors proceeded to train the _H-DRLN_ agent in a complex task.

### Results:

The success rate of _H-DRLN_ was significantly higher in the complex tasks compared to a standard DQN policy trained in the same task. 

### Future work:

- Learning skills _online_ instead of pre-training them in simple problems.
- Refine previously learned skills.
- Automatically add new skills to the _Deep Skill_ module as new behaviors are learned.
