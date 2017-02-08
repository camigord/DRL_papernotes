# Learning Hand-Eye Coordination for Robotic Grasping with Deep Learning and Large-Scale Data Collection

The paper presents an approach based on CNNs for learning hand-eye coordination for grasping objects using robotic manipulators. The authors collected over 800000 grasp attempts using 14 robotic manipulators over the course of 2 months. This dataset was then used to train a CNN to predict the success rate of a specific trajectory based on monocular camera images. 

The dataset and additional resources are provided by the authors [here](https://sites.google.com/site/brainrobotdata/home).

### Keynotes:

- 800000 grasping attempts were collected without any manual annotation or supervision.
- To improve generalization, the specific configuration of each robot varied in terms of camera location/calibration.
- A sensor on the gripper and automatic visual inspection were used to label each attempted trajectory.
- A CNN was trained to predict the success rate of a grasping trajectory *v<sub>t</sub>* based on the current camera observation *I<sub>t</sub>*.
- A controller then chooses motor commands which maximize the probability of succesfully grasping an object. 

### Opinion:

- It is a really interesting proof of concept, showing the generalization power of deep models and their applicability in real robotic applications. It also shows that, with proper and sufficient data, current models are capable of learning quite complex task. I will argue, however, than not everybody can afford having 14 robot manipulators collecting experiences for more than 2 months! This again encourages the research of more data efficient techniques or proper data transfer approaches capable of generalizing from simulated experiences to real world scenarios.

![model](https://github.com/camigord/DRL_papernotes/blob/master/assets/HandEyeCoordination.png)
