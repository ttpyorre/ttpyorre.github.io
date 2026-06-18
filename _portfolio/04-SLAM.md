---
title: "SLAM Navigation"
excerpt: "With turtlebots safely explored and mapped a maze, and afterwards localized after being \"kidnapped\". During my masters studies I also ended up being a teaching assistant for this class. <br/><img src='/images/portfolio/replace_SLAM.jpg'>"
collection: portfolio
---

This project focused on developing a fully autonomous navigation system for a TurtleBot using ROS. The robot was required to explore an unknown environment, generate a map using SLAM, identify unexplored regions, autonomously navigate to them, return to a designated location, and later relocalize itself within the saved map using Monte Carlo Localization (AMCL).

The project combined occupancy grid processing, configuration space generation, frontier-based exploration, A* path planning, and probabilistic localization into a complete autonomous navigation pipeline.

* Autonomous exploration of unknown environments
* Frontier detection and selection
* Occupancy grid configuration-space (C-space) generation, using both 4 and 8-neighbor node checking
* Optimized A* path planning with custom heuristics
* Map generation and saving using ROS Gmapping
* Adaptive Monte Carlo Localization (AMCL)
* State-machine-based system architecture
* Autonomous navigation to user-defined goals using Rviz

## Configuration Space Generation

To safely navigate around obstacles, I implemented a configuration-space (C-space) expansion algorithm that inflated walls based on the TurtleBot's physical dimensions. This ensured that the turtlebot could safely navigate, and stop itself before attempting to go through too narrow of a path.

Rather than repeatedly expanding every obstacle cell, the algorithm created a distinguishable outer layer around obstacles using a value of 99 while occupied cells retained a value of 100. Additional padding iterations only expanded cells marked as 99.

As the TurtleBot had a max radius of 8cm that it could go through, the map resolution was set to 2.3cm/cell, with a padding radius of 4, giving an effective clearance of 9.2cm. This ensured that even if the sensor reading were faulty to a degree, the turtlebot could clear the path it tried to attempt to go through.

An additional wall-proximity cost layer was added to encourage paths that maintained greater distance from obstacles whenever possible.

## Frontier-Based Exploration

To autonomously map unknown environments, the robot used frontier-based exploration.

Frontiers were identified as free cells adjacent to unexplored space. The detection process consisted of:

* Identifying all free cells in the occupancy grid.
* Performing neighbor searches to locate cells bordering unknown regions.
* Grouping connected frontier cells into frontier regions.
* Computing frontier centroids and region sizes.

Alternate way to detect the frontiers would be to use CV with the map, to identify the border cells.

A scoring system to determine which unexplored space the robot wanted to explore was developed, it balanced:

* Distance to the frontier
* Frontier size

This allowed the robot to prioritize large information-rich frontiers while avoiding unnecessary travel to distant regions.

The exploration cycle repeated until no valid frontiers remained, indicating that the environment had been fully mapped.

## A* Path Planning

Navigation was performed using an A* planner operating on the generated C-space.

The planner used:

* Euclidean distance
* Travel cost accumulation
* Turn penalties
* Wall proximity penalties

Turn penalties discouraged excessive heading changes, producing smoother paths that were easier for the TurtleBot to follow. Wall penalties further encouraged safer trajectories that maintained additional clearance from obstacles.

The resulting paths were both efficient and robust in cluttered environments. These paths could later be combined with either a PID controller to follow the trajectory, or a pure pursuit (algorithm)[https://wiki.purduesigbots.com/software/control-algorithms/basic-pure-pursuit]. 

## Map Saving and Goal Navigation

After exploration was completed, the generated occupancy map was saved using the ROS `map_server` package.

The robot could then:

* Navigate back to its starting location
* Accept arbitrary navigation goals from RViz
* Plan and execute paths across the completed map

## Monte Carlo Localization (AMCL)

The final phase of the project simulated the "kidnapped robot" problem.

After loading the previously generated map, the robot was taken and moved to an unknown location where it had to relocalize itself using AMCL.

Localization was performed by:

1. Loading the saved occupancy grid.
2. Spinning in place to gather laser scan information.
3. Monitoring pose covariance.
4. Waiting until localization uncertainty dropped below a predefined threshold.

Once localized, the robot could successfully navigate to any point within the map using the same planning framework developed during exploration.

Following parameter tuning, localization consistently converged within approximately 20 seconds.

## System Architecture

The overall system was organized as a ROS state machine coordinating multiple nodes:

* Frontier Detection Node
* Path Planning Node
* C-Space Generation Node
* Navigation Controller Node
* AMCL Localization Node

This modular architecture simplified development, testing, and debugging while allowing each subsystem to operate independently.

## Results

The complete system successfully achieved autonomous exploration, mapping, localization, and navigation.

Key outcomes included:

* Reliable frontier detection and autonomous exploration
* Safe obstacle avoidance through C-space inflation
* Efficient A* path planning
* Consistent map generation and saving
* Robust AMCL localization within 20 seconds
* Successful navigation to arbitrary goals on the generated map

Performance optimizations, including NumPy-based occupancy grid processing, significantly reduced computation time for map operations and obstacle inflation.
