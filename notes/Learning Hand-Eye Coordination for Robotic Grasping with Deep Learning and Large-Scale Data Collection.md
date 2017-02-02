# Learning Hand-Eye Coordination for Robotic Grasping with Deep Learning and Large-Scale Data Collection

The paper presents an approach based on CNNs for learning hand-eye coordination for grasping objects using robotic manipulators. The authors collected over 800000 grasp attempts using 14 robotic manipulators over the course of 2 months. This dataset was then used to train a CNN to predict the success rate of a specific trajectory based on monocular camera images. 

The dataset and additional resources are provided by the authors [here](https://sites.google.com/site/brainrobotdata/home).

### Keynotes:

- 800000 grasping attempts were collected without any manual annotation or supervision.
- To improve generalization, the specific configuration of each robot varied in terms of camera location/calibration.
- A sensor on the gripper and automatic visual inspection were used to label each attempted trajectory.
- A CNN was trained to predict the success rate of a grasping trajectory *v<sub>t</sub>* based on the current camera observation *I<sub>t</sub>*.

**# Incomplete**

![model](https://github.com/camigord/DRL_papernotes/blob/master/assets/HandEyeCoordination.png)
