---
title: "Quadrotor Trajectory Tracking"
excerpt: "Quadrotor control using the sliding mode control model. <br/><img src='/images/portfolio/control/Crazyflie2.0-585px.JPG'>"
collection: portfolio
---

Designed and implemented a nonlinear control system for autonomous quadrotor (specifically Crazyflie 2.0) trajectory tracking in MATLAB. The project focused on generating smooth flight trajectories using quintic polynomial planning and developing a sliding mode controller capable of tracking three-dimensional position commands while accounting for the nonlinear dynamics of the aircraft. Following the initial simulation work, the trajectory generation and control framework were further implemented in Python using ROS.

- Developed quintic trajectory generation algorithms to create smooth position, velocity, and acceleration profiles for quadrotor motion.
- Generated and analyzed trajectory paths in the x, y, and z directions for multiple waypoints of different durations.
- Modeled the full nonlinear dynamics of a six-degree-of-freedom quadrotor system.
- Derived sliding mode control laws for position and attitude regulation.
- Implemented saturation functions to reduce control chattering commonly associated with sliding mode controllers.
- Tuned controller gains and stability parameters through iterative simulation and performance analysis.
- Evaluated tracking performance and investigated controller limitations through simulation testing.
- Ported trajectory generation and control algorithms from MATLAB into Python and integrated them within a ROS-based robotics environment.

Here is a small table of the quadrotors physical parameters: 

| Parameter | Symbol | Value |
|------------|--------|--------|
| Quadrotor mass | m | 27 g |
| Quadrotor arm length | l | 46 mm |
| Quadrotor inertia along x-axis | Ix | 16.571710 × 10⁻⁶ kg·m² |
| Quadrotor inertia along y-axis | Iy | 16.571710 × 10⁻⁶ kg·m² |
| Quadrotor inertia along z-axis | Iz | 29.261652 × 10⁻⁶ kg·m² |
| Propeller moment of inertia | Ip | 12.65625 × 10⁻⁸ kg·m² |
| Propeller thrust factor | kF | 1.28192 × 10⁻⁸ N·s² |
| Propeller moment factor | kM | 5.964552 × 10⁻³ m |
| Rotor maximum speed | ωmax | 2618 rad/s |
| Rotor minimum speed | ωmin | 0 rad/s |

<img src='/images/portfolio/control/crazyflie-simulation.png'>


The quadrotor state vector was modeled using translational and rotational states:

$\[
q = [x,\; y,\; z,\; \phi,\; \theta,\; \psi]
\]$

with control inputs corresponding to thrust and rotational commands:

$\[
u = [u_1,\; u_2,\; u_3,\; u_4]
\]$

A quintic polynomial trajectory planner was used to generate smooth reference trajectories with continuous position, velocity, and acceleration profiles. The controller utilized a sliding mode framework, incorporating saturation functions to mitigate chattering effects and improve stability. The resulting control architecture was later adapted to Python and integrated with ROS for robotic system development.

## Results

The controller successfully guided the quadrotor along the desired vertical trajectory and demonstrated the ability to track reference positions. However, simulations revealed instability near the target position, where the vehicle overshot the desired waypoint and eventually diverged from the reference trajectory.

Performance analysis suggested that the controller's instability could originate from model inaccuracies, implementation issues, or parameter tuning limitations. Extensive experimentation was conducted to evaluate each possibility and understand the sensitivity of the sliding mode controller to these parameters. After the experimentation and changes from it, the controller was finally successfull! 
