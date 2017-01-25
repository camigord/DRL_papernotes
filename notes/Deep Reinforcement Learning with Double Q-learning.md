# Deep Reinforcement Learning with Double Q-learning

In this paper the authors show that the standard DQN effectively *overstimates* the action values which in turn hinders the performance 
of the agent. They also propose the use of Double Q-learning to alleviate this problem and they show how to generalize this technique from the tabular settings into arbitrary function aproximators (like deep neural networks). The proposed algorithm is then named **Double DQN** and it obtains state-of-the-art results on the Atari domain.

### Keynotes:

- *"The max operator in standard Q-learning and DQN ... uses the same values both to select and to evaluate an action. This makes it more likely to select overstimated values, resulting in overoptimistic value estimates. To prevent this, we can decouple the selection from the evaluation".*

- In general, they change the original DQN target update from:

<p align="center">
  Y<sub>t</sub><sup>Q</sup> = R<sub>t+1</sub> + &gamma; Q(S<sub>t+1</sub>, argmax<sub>a</sub> Q(S<sub>t+1</sub>,a; &theta;<sub>t</sub>); <b> &theta;<sub>t</sub></b>)
</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; into:

<p align="center">
  Y<sub>t</sub><sup>Double Q</sup> = R<sub>t+1</sub> + &gamma; Q(S<sub>t+1</sub>, argmax<sub>a</sub> Q(S<sub>t+1</sub>,a; &theta;<sub>t</sub>); <b>&theta;'<sub>t</sub></b> )
</p>

<p align="center">
<i>"The selection of the action (inside the argmax) is still due to the online weights &theta;. ... However, we use the second set of weights &theta;' to fairly evaluate the value of this policy"</i>
</p>

With this relatively *small* change they were able to find better policies in many of the tested games, thus obtaining state-of-the-art results on the Atari 2600 domain.
