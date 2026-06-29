---
title: "A3C and DDPG robot picker"
excerpt: "Using the A3C and DDPG RL algorithms made a robot pick up objects in a MuJoCo environment. <br/><img src='/images/portfolio/A3C_mujoco.JPG'>"
collection: portfolio
---

I trained both DDPG and A3C models to pickup multi-shaped objects in a MuJoCo environment. This project utilized skills in RL, MuJoCo, Python, and the gym python library. The A3C model was trained on the CPU of the machine, while DDPG was trained on GPU. As A3C uses multiple agents using asynchronous parallel CPU training is more efficient for using computational resources. 

As part of a reinforcement learning project, I implemented and evaluated two state-of-the-art continuous control algorithms: Deep Deterministic Policy Gradient (DDPG) and Asynchronous Advantage Actor-Critic (A3C). The goal was to train a robotic manipulator to perform a control task within a simulated environment and compare the strengths and weaknesses of different reinforcement learning approaches.

This project provided hands-on experience with neural network design, policy optimization, exploration strategies, hyperparameter tuning, and reinforcement learning performance analysis. In the project I did the following:

- Implement DDPG and A3C reinforcement learning agents.
- Train agents in a continuous-action robotic simulated environment (MuJoCo).
- Analyze training stability, convergence behavior, and exploration performance.
- Evaluate the impact of network architecture and hyperparameter selection.
- Compare off-policy and on-policy learning approaches.

The Deep Deterministic Policy Gradient (DDPG) algorithm was selected due to its effectiveness in continuous action spaces. This implementation included the following:

- Actor-Critic neural network architecture
- Target networks for training stability
- Experience replay buffer
- Exploration noise for action selection
- Soft target updates
- Training on the GPU

A significant portion of the project focused on tuning exploration strategies and replay buffer behavior. Multiple network architectures and hyperparameter configurations were evaluated in an attempt to improve training stability and policy performance.

During training, the agent frequently converged to undesirable behaviors, including becoming trapped in local minima where the robotic arm repeatedly moved into workspace corners and failed to recover. Various approaches were explored to address these issues, including:

- Exploration noise tuning
- Replay buffer adjustments
- Actor and critic network resizing
- Learning rate modifications
- Target network parameter tuning

These experiments highlighted the sensitivity of DDPG to hyperparameter selection and environment design.

On the other hand the Asynchronous Advantage Actor-Critic (A3C) algorithm was implemented as an alternative approach with improved exploration and parallelized training. It utilized:

- Shared global network
- Actor-Critic learning framework
- Entropy-based exploration
- Multi-worker asynchronous training
- Training on the CPU due to its global approach to learning the environment

Unlike DDPG, A3C does not rely on an experience replay buffer and instead learns directly from current interactions with the environment. This allowed for faster experimentation and more efficient use of CPU resources.

Shared versus separate actor and critic pathways
Different hidden layer sizes
Entropy coefficient tuning
Learning rate adjustments
Action output activation functions

One particularly impactful modification involved removing the final tanh activation layer from the action network. This increased action-space differentiation and improved reward performance by avoiding excessive compression of action outputs.

In the end the models were fairly successfull at picking up the objects, however they were very "temperamental" during training.