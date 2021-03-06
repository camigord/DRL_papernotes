# Playing Doom with SLAM-Augmented Deep Reinforcement Learning



### Keynotes:
- They agment the raw image input to a DQN by adding details about the detected objects along with the agent localization.
- The idea is to use *semantic concepts* or *abstractions* to augment the input to the DQN.
- They create a 2D map (top-down view) of the environment where they locate obstacles, enemies, agent location, etc. They update this representation as the agent explores the environment. They encode objects using different grayscales.
- By building this *semantic map* the agent does no longer need to *remember* the past. Moreover, it can still act properly when a given object is not within its field of view.
- They input this *semantic map* as an additional channel to the DQN with the same resolution (84x84) as the RGB images.
- Although DOOM accepts any combination of 43 unique keystrokes as input, they selected the top 13 actions which are more frequently used by human players. 
- The reward is given as a function of current health and number of eliminated opponents.

#### Semantic representation:
- They encode the location of the agent, position of walls, obstacles, enemies... etc onto a 2D map with a **fixed size!**.
- Objects which can move or dissapear from the environment (like enemies) are only mapped if they are visible in the current view. They propose the use of data association techniques to improve this. **If we could predict what will happen with some objects, we could still map them either if they are not visible: i.e. model the movement of an enemy or the probability of him picking up a health pack.**

#### Recognition and Reconstruction:
- They self-supervised the training of a deep model (Faster-RCNN) which detects and localizes 5 different classes in the raw RGB images.
- They use camera pose estimation techniques to determine location based on RGBD images. 
- Mapping: Using the camera pose and the object detection mask they project the current frame into a 3D map. They then take a top-view image of this 3D map (ignoring areas which would occlude the map).

### Experiments:
1. Oracle semantic maps: They test the performance of the model assuming perfect localization, mapping and object detection. They show that the network learns faster and outperforms baseline method (DQN).

2. Noisy oracle semantic maps: They test the performance after adding noise to the ground-truth maps. They show that in the worse case, the network learns to ignore this input and performs similar to the baseline.

3. Reconstructed semantic maps: Testing the performance using the maps generated by the proposed approach. They got significantly better results than the baseline (although not as good as using the ground-truth). **They propose that the remianing gap can be reduced by improving the proposed techniques**.

4. Prioritized Duel DQN: They compared their approach with a model trained using Prioritized Double Q learning and obtained better performance. They also mention that their approach could be enhanced combining these techniques (Double Q and prioritized mem. replay). **Maybe also A3C.**

### Comments:
- I like a lot the idea of using object detection and semantic segmentation together with DRL. This could simplify a lot the complexity of the environments and could encourage the models to focus in learning behaviors and not in recognizing states.

![model](https://github.com/camigord/DRL_papernotes/blob/master/assets/SLAM-Aug_Doom.png)
