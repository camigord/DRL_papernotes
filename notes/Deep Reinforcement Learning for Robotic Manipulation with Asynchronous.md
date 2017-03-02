# Deep Reinforcement Learning for Robotic Manipulation with Asynchronous Off-Policy Updates

### Authors: Shixiang Gu, Ethan Holly, Timothy Lillicrap, Sergey Levine

## Keynotes

- They present a demonstration of asynchronous DRL using Normalized Advantage Function
 ([NAF](https://arxiv.org/abs/1603.00748)) which can learn complex manipulation skills
 (door opening and pick and place) on real robot platforms.

- They propose a sample-efficient asynchronous implementation suitable for real time
applications and which asynchronous nature allows the collection of experiences from
multiple robots in parallel.

- They claim that, to the best of their knowledge, this is the first approach capable of
learning complex skills on real robots without demonstrations or simulated pretraining.

- They distribute the learning process by running a centralized _"learning thread"_ in charge
of performing asynchronous updates to the network parameters based on the experiences collected
by a group of _"working threads"_. These _workers_ are executed on individual robots and
get synchronized at the beginning of each episode. This setup allows them to introduce
more _workers_ (robots) at will in order to speed up the learning process. It also allows
the robots to run in real time without experiencing delays due to computational cost.

- They introduce a _safety_ mechanism for constraining exploration at training time. These
are basically a set of constraints limiting the maximum velocity per joint, the allowed
operation range etc.

- The authors employed a simple state representations consisting of joint angles, end-effector
 position and their respective time derivatives. They also added the target position to
 the state. This target depends on the current task (i.e. the position of the door handle in the
 door opening task).

 - Interestingly, they noticed that there is a limit where increasing the number of _workers_
 and collecting more data does not help speed up learning. They hypothesize that this happens
 due to the speed of the neural network training: basically, it does not make sense to have
 100 workers collecting experiences if there is only one centralized thread which can not
 cope with all this data at the same speed.

 - They trained using up to 4 real robots in parallel. Another benefit of using several
 robots was that the system can adapt to physics or calibration discrepancies among robots.

 - The model learned how to open a door after only 2.5 hours! when using 2 robots in parallel,
 and achieved a success rate of 100% in 20 testing trials.

## Comments

- I like the paper a lot and the results are impressive. As the authors mention at the end of the paper, however, the reward function could still be interpreted as some sort of demonstration given that it provides some guidance to the system.

- I can not believe that their approach can learn that fast using only 2 robots and training directly on real data. That is very impressive and I can imagine many applications where such models could easily outperform state of the art approaches.

- The authors propose, as future work, to investigate how diverse experience can be integrated into a single policy. You could train using different door types, different end-effectors etc. and the policy should generalize across all these experiences. 
