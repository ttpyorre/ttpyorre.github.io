---
title: "A3C and DDPG robot picker"
excerpt: "Using the A3C and DDPG RL algorithms made a robot pick up objects in a MuJoco environment. <br/><img src='/images/portfolio/A3C_mujoco.JPG'>"
collection: portfolio
---

I trained both a DDPG and A3C models to pickup multi-shaped objects in a MuJoco environment. This project utilized skills in RL, MuJoco, Python, and the gym python library. The A3C model was trained on the CPU of the machine, while DDPG was trained on GPU. This is because the A3C uses multiple agents, so using asynchronous CPU training is better.
