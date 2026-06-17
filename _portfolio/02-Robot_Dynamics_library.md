---
title: "Robotic Arm MATLAB Library"
excerpt: "Throughout a graduate level robotics class I made a robotics library that included core algorithms used in modern robot kinematics, dynamics, and motion planning. <br/><img src='/images/portfolio/color_sort/RBE3001_robot.JPG'>"
collection: portfolio
---

Throughout an advanced robotics course, I developed a comprehensive MATLAB library implementing the core algorithms used in modern robot kinematics, dynamics, and motion planning. The project served as a personal robotics toolkit, allowing me to model robotic systems, solve kinematic and dynamic problems, generate trajectories, and simulate robot motion from first principles.

The library was developed incrementally over an entire semester and covers topics including:

- Forward Kinematics
- Inverse Kinematics
- Exponential Coordinates of Rotation
- Exponential Coordinates of Rigid-Body Motion
- Product of Exponentials (POE) Formulation
- Differential Kinematics
- Jacobian-Based Motion Analysis
- Singularities
- Body Frame and Space Frame Representations
- Robot Statics
- Newton-Euler Dynamics
- Recursive Newton-Euler Algorithms
- Forward Dynamics
- Lagrangian Dynamics
- Trajectory Planning
- Mobile Robot Modeling
- Key Features
- Kinematics Module

Implemented tools for computing robot end-effector positions and orientations using both traditional kinematic methods and the Product of Exponentials formulation.

- Homogeneous transformation matrices
- Rotation matrix operations
- Frame transformations
- Space and body frame representations
- Forward kinematics for serial manipulators
- Numerical and analytical inverse kinematics
- Differential Kinematics

Developed Jacobian-based algorithms to analyze robot velocity relationships and workspace behavior.

- Jacobian generation
- End-effector velocity calculations
- Joint velocity mapping
- Singularity detection and analysis

Implemented robotic dynamics algorithms based on Newton-Euler and Lagrangian formulations.

- Force and torque propagation
- Static force analysis
- Recursive Newton-Euler calculations
- Forward dynamics simulations
- Dynamic modeling of serial manipulators
- Motion Planning

Developed trajectory generation tools for smooth robotic motion.

- Joint-space trajectory planning
- Position, velocity, and acceleration profiles
- Time-parameterized motion generation
- Multi-waypoint trajectory execution

As our exams were open book, and designed in a way to take advantage of the libraries, I could simply pull out a few functions and finish the exams in a few minutes! All of this library was tested with a robotics toolbox in Matlab, see https://petercorke.com/toolboxes/robotics-toolbox/. With this toolbox we explored multiple different types of robotics arms.