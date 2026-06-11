---
title: "Active Vision Grasping"
excerpt: "Found the optimal grasp for a cylindrical object using an active vision approach. We looked at the object from multiple viewpoints, created a pointcloud representation of the object, and found the best grasp given the viewpoints. <br/><img src='/images/portfolio/AVG_Gazebo.JPG'>"
collection: portfolio
---

I developed an active vision pipeline capable of generating grasp points for unknown objects using point cloud data. The system used an RGB-D camera in a ROS2 and Gazebo simulation environment to observe an object, generate a 3D point cloud, estimate surface normals, and identify stable grasp locations for a robotic gripper.

The project demonstrated the integration of computer vision, point cloud processing, geometric reasoning, and robotic grasp planning.

Objectives:
- Generate 3D point clouds from camera observations.
- Remove environmental noise and isolate target objects.
- Estimate surface normals across the object surface.
- Identify stable grasp locations using geometric analysis.
- Visualize candidate grasp points in real time.

The project was developed using ROS2 and Gazebo.

The simulation environment consisted of:

- An RGB-D camera mounted above the workspace.
- A tabletop environment.
- A cylindrical object used as the grasp target.

Multiple viewpoints were captured to support active vision and improve object understanding.

Using the Point Cloud Library (PCL), depth information from the camera was converted into a 3D point cloud representation of the scene. This allowed the object geometry to be analyzed directly in three-dimensional space rather than relying solely on image-based features. Raw point clouds contained both the target object and environmental structures such as the table surface.

To isolate the object, RANSAC plane segmentation was applied to identify and remove the dominant planar surface. After segmentation, only the object point cloud remained. Surface normals were calculated for points across the segmented object, and they provided information about local surface orientation and were used to evaluate grasp quality. Normal estimation enabled the system to reason about how a gripper would interact with the object's geometry.

A custom grasp evaluation algorithm was developed to identify stable two-point grasps for a parallel-jaw gripper. This algorithm did the following:

- Evaluated pairs of surface points.
- Computed surface normal vectors.
- Used dot-product calculations to measure angular relationships.
- Identified candidate pairs whose normals opposed one another.
- Selected the grasp closest to the object's centroid to maximize stability.

Grasp candidates were accepted when the opposing surface normals formed angles near 0° or 180°, indicating that gripping forces would be directed toward one another and generate a stable grasp.

The selected grasp points were visualized in RViz2 by highlighting the corresponding point cloud coordinates in magenta.

The system successfully:

- Generated 3D point clouds from camera observations.
- Removed background geometry using RANSAC segmentation.
- Estimated surface normals across the object surface.
- Identified stable grasp locations for a cylindrical object.
- Visualized grasp points directly within RViz2.

The final grasp planner consistently selected opposing contact points that produced stable grasp configurations while remaining close to the object's centroid.
