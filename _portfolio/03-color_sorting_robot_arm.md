---
title: "Color Sorting Using a Robotic Arm"
excerpt: "Using classical vision techniques, had a physical robot arm pick up different colored and shaped objects. During my masters studies I also ended up being a teaching assistant for this class. <br/><img src='/images/portfolio/color_sort/RBE3001_robot.JPG'>"
collection: portfolio
---

As the capstone project for a robotics kinematics course, I developed a vision-guided robotic sorting system capable of identifying, locating, and sorting colored objects autonomously. The project integrated robotic kinematics, computer vision, coordinate transformations, and trajectory planning to create a complete pick-and-place solution.

The system used a 3-degree-of-freedom robotic arm and an overhead camera to detect colored spheres on a checkerboard workspace, determine their real-world coordinates, and sort them into designated locations based on color.

<img src='/images/portfolio/color_sort/RBE3001_robot.JPG'>

Our objectives were:
- Implement forward and inverse kinematics for robotic arm control.
- Calibrate and register a camera with the robot workspace.
- Detect and classify objects using computer vision techniques.
- Convert image coordinates into robot task-space coordinates.
- Develop an autonomous sorting algorithm capable of repeatedly locating and sorting objects.


Forward and inverse kinematics were developed using Denavit-Hartenberg (DH) parameters and transformation matrices. These calculations enabled the robot to accurately convert between joint-space and task-space coordinates, allowing precise end-effector positioning throughout the workspace.

Camera calibration was performed using MATLAB's calibration tools and checkerboard images captured from multiple angles. Intrinsic camera parameters were calculated to minimize reprojection error and accurately map image coordinates to physical space.

Extrinsic calibration was then used to determine the transformation between the camera coordinate frame and the robot base frame, enabling direct conversion from image pixels to robot task-space coordinates.

<img src='/images/portfolio/color_sort/pixel_to_board.JPG'>

Object detection was implemented using HSV color masking to identify red, yellow, green, and orange objects against the checkerboard background. On top of this we managed to identify single colored shapes with simple blob detection.

The vision pipeline included:
- Color thresholding and masking
- Circle detection using image-processing algorithms
- Centroid extraction for object localization

The robot utilized quintic trajectory planning in joint space to generate smooth and continuous movements.

For each detected object, the system generated a sequence of motions:

- Move above the object.
- Align the gripper.
- Lower to grasp.
- Lift above surrounding objects.
- Move to the designated sorting location.
- Return to the home position.

The final system successfully identified and sorted colored objects autonomously using computer vision and robotic manipulation.
