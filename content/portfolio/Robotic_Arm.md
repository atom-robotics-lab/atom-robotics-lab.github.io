---
title: "ROBOTIC ARM"
date: 2024-07-5
type: portfolio
image: "/images/projects/robotic-arm.png"
category: ["ROS | OpenCV | Gazebo | Robot-Perception | React | Javascript"]
---

{{<youtube kM_5QzVYqo8>}}
<br><br>

<style>.image{display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%}</style>
  
A.J.G.A.R project, which features a 6 Degrees of Freedom (DoF) robotic arm that can move in six directions. A robotic manipulator is commonly used in industrial and manufacturing settings for tasks such as pick and place, assembly, and welding.

## ABOUT A.J.G.A.R

 A.J.G.A.R is designed to autonomously handle objects, utilizing computer vision technology for this purpose. It also supports remote operation via teleoperation. 

{{<figure src="/images/projects/robotic-arm-cad.png" caption="Fig1 : Cad model of Robotic Arm" width="300" height="500">}}

The six degrees of freedom are typically achieved through the use of six stepper motors. Each stepper motor controls a single joint of the robotic arm, and together they allow the arm to move in a wide range of motions. The stepper motors are controlled by a microcontroller, which sends signals to the motors via stepper driver.

{{<figure src="/images/projects/arm.png" caption="Fig2 : Robotic arm with multiple articulated joints, mounted on a base and connected to an electronic control board." width="300" height="350">}}

This project is divided mainly into three parts:

**SOFTWARE** : The programming of this project is done using moveit, ikpy, gazebo and rviz simulation and perception. With the help of a kinect camera we precisely predicted its environment in 3D space, which improved the interaction with objects and people.

**HARDWARE** : Firstly a cad model was designed for optimized use case then all the components and 3D printed parts were manufactured and assembled.

**ELECTRONICS**: The electronics comprised of circuit desgin, sensor interfacing and wiring placing.

<!-- Github : https://github.com/atom-robotics-lab/robotic-arm-atom -->
