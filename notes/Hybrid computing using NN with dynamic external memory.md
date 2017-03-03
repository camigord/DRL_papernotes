# Hybrid computing using a neural network with dynamic external memory

### Authors: Alex Graves, Greg Wayne, Malcolm Reynolds, Tim Harley, Ivo Danihelka, Agnieszka Grabska-Barwińska, Sergio Gómez Colmenarejo, Edward Grefenstette, Tiago Ramalho, John Agapiou, Adrià Puigdomènech, Karl Moritz Hermann, Yori Zwols, Georg Ostrovski, Adam Cain, Helen King, Christopher Summerfield, Phil Blunsom, Koray Kavukcuoglu, Demis Hassabis

## Keynotes

- The goal of the paper is to provide neural networks with read-write access to external memory storage.

- They propose a system which is differentiable and can therefore be trained end-to-end using gradient descent. The network should learn how to operate and organize the memory in a goal-oriented manner.

- The network is independent of the memory size.

- The authors named their system DNC for _Differentiable Neural Computer_, and can be understood as an extension/improvement of their previous work: [Neural Turing Machine](https://arxiv.org/abs/1410.5401).

- DNC uses "differentiable attention mechanisms" to address memory contents. Instead of using unique addresses like regular computers, the network can weight the degree to which each location in memory is involved in a read/write operation.



## Comments

- The idea is really good and by the time I read the paper it had already inspired a lot of interesting approaches in the area of DRL. The implementation and training of such a network seems a little complex, but it would be very useful for understanding to implement a "simple" version of the idea in a dummy task.
