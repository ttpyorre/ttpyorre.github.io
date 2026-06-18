---
title: "Shepherd Swarm"
excerpt: "Made a swarm of sheeps and shepherds, where the shepherd agents collected all the sheep agents into a circle. Initial state of the world was randomized. <br/><img src='/images/portfolio/swarm/shepherd_and_sheep.png' <br/><img src='/images/portfolio/swarm/herding.png' >"
collection: portfolio
---

This work aims to enable a swarm of resource-limited shepherd robots in the sheepdog penning problem to accurately lead a flock of sheep robots into an enclosed space. Resource-limited robots cannot perform hardware intensive tasks such as multi-robot SLAM or self localization due to limitations on memory and/or computational power. Therefore, we made a centralized, highly robust communication network to enable these computationally expensive tasks. Our system guided sheep from a large enclosure to a narrow corridor that funneled them into a smaller, enclosed pen. This shepherding system has a multitude of alternative applications, such as: cleaning oil spills, protecting aircraft from bird strikes, or handling micro-organisms. For this project we used the programming language buzz that is designed for programming swarms, and a simulator called ARGoS that is also designed for simulating large-scale swarms. 

<img src='/images/portfolio/swarm/swarm_state_machine.png'>

This state machine showcases how the system works. For shepherding, the shepherds all follow the same formula. The sheep followed a simpler state machine of clustering together, avoiding obstacles, and avoiding shepherds. The goal of the shephers is the surround all the sheep, and then guide them to the pen. 

<img src='/images/portfolio/swarm/herding.png'>

Here is an example of the herding in action. Overall, the herding functionality was very successful with 29 out of every 30 runs herding the sheep with none lost. Even in the two trial runs out of our 60 where the sheep were not herded completely, only one managed to escape out of the 20 sheep.