---
title: "Whats behind MR.ROBOT ?"
date: 2024-02-25
image: images/blog/mr_robot/cover_mr_robot.jpeg
feature_image: images/blog/mr_robot/cover_thumbnai_mr_robot.jpeg
author: Kiriti Nain
linkdein: https://www.linkedin.com/in/kiritinain/
---

# MR Robot

Let's think of something that people have made in their likeness—I'm talking about robots. We get excited when we talk about robots, but there's also a healthy dose of curiosity, which often results in the development of more likely-to-be human robots. That is exactly the reason why we at A.T.O.M. came up with the idea of fabrication of “MR Robot”. Fascinating right? Let’s dive more into “MR Robot” then.

{{<figure src="/images/blog/mr_robot/cover_mr_robot.jpeg" caption="mr robot" width="100%">}}
MR Robot is a kind of autonomous mobile robot (AMR), it can understand and move through its environment without being overseen directly by an operator or limited to a fixed, predetermined path. It is designed to navigate its environment using the ROS (Robot Operating System) navigation stack. The project is designed with versatility in mind; that is, it is composed of plug-and-play components that may be altered to accommodate various use cases. ROS navigation stack consists of several software packages that enable robot mapping and navigation. This enables “MR-ROBOT” to precisely explore its environment and avoid obstacles by utilizing sensors like LIDAR, cameras, and IMU.

MR Robot leverages Simultaneous Localization and Mapping (SLAM) algorithms to autonomously navigate, understand, and interact with their environment by simultaneously estimating their own position and constructing a map of the surroundings using sensor data, enabling real-time decision-making and adaptive behavior in dynamic environments.
The modularity of the “MR-ROBOT” project is one of its main advantages. Sensors and manipulators are just a few examples of the interchangeable elements and components that enable this modularity. Combining the strength of the ROS navigation stack with the adaptability of a modular robot design, the MR Robot represents an exciting advancement in the field of autonomous robotics. This implies that it can be tailored to fit a variety of uses, such as medical robots and warehouse automation.

## Working of MR Robot

### Hardware Working

MR Robot is equipped with two encoder motors, an ESP32 micro controller, a Raspberry Pi 4, an IMU, a LiDAR, a motor driver, and a 5V buck converter. The robot is designed to calculate the movement of the motors and send it to the microcontroller. The data is then published to a topic and used to calculate the odometry. The LiDAR and IMU are linked to the Raspberry Pi 4, and the motor driver is used to form an H-bridge for differential drive.Let's go over each of these specialized terminology in detail now.

- Encoder Motors :- MR Robot is equipped with two encoder motors. The encoder motor calculates the movement of the motor and sends it to the microcontroller. This data is then used to calculate the odometry.
- ESP32 Microcontroller :- It receives data from the encoder motors and processes it. The microcontroller then publishes the data to a topic that is used to calculate the odometry.
- Raspberry Pi 4 :- The Raspberry Pi 4 is used to link the LiDAR and IMU. The LiDAR and IMU are connected to the Raspberry Pi 4, which processes the data from the sensors.
- IMU :- The IMU is used to measure the orientation, acceleration, and angular velocity of the robot. The data from the IMU is processed by the Raspberry Pi 4 using a Kalman filter. The Kalman filter is used to estimate the orientation, acceleration, and angular velocity of the robot.
- LiDAR X 2L Model :- The LiDAR X2L Model is a type of LiDAR sensor that is used to detect the distance and angle of objects in the environment. The LiDAR X2L Model is connected to the Raspberry Pi 4 and is used to create a map of the environment.
- Motor Driver :- The motor driver is used to form an H-bridge for differential drive. The motor driver is connected to the microcontroller and the encoder motors. The motor driver is responsible for controlling the speed and direction of the motors.
- 5V Buck Converter :- The 5V Buck Converter is used to convert the voltage from the battery to 5V.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ALdvA4_olxw?si=s58Hr8uuV8Bx7oVN&amp;controls=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

To wrap things up, MR Robot is an intricately engineered robotic system, integrating cutting-edge sensors and components for seamless environmental navigation. With LiDAR, IMU, and Encoder Motor, this robot boasts precision in its movements. Motor control is facilitated through a motor driver, while sensor data processing is efficiently managed by a microcontroller. In essence, MR Robot stands as a formidable and adaptable platform, adept at executing diverse tasks with finesse.

### Software Working

MR Robot employs the ROS Serial protocol for seamless communication with its various components. It relies on Twist to PWM for precise motor control and ESP_Diff_TF for accurate odometry calculation. Additionally, equipped with a LiDAR sensor interfaced with the Raspberry Pi 4, the robot harnesses its capabilities for robust mapping and navigation tasks.

- ROS Serial Protocol :- ROS Serial is a protocol used to communicate with the robot’s components, such as the microcontroller and motor driver. It allows for the exchange of messages between the robot and the computer. This protocol is used to send and receive data from the robot, such as motor commands and sensor data.
- Twist to PWM :- The Twist to PWM converter is used to control the speed and direction of the robot’s motors. It takes in Twist messages, which represent the desired linear and angular velocities of the robot, and converts them to PWM signals that are sent to the motor driver.
- ESP_Diff_TF :- The ESP_Diff_TF node is used to calculate the robot’s odometry. It takes in the encoder data from the motor driver and uses it to calculate the robot’s position and orientation. The calculated odometry data is then sent to the Navigation Stack.
- AMCL :- The Adaptive Monte Carlo Localization (AMCL) node is used to localize the robot within a map. It takes in sensor data, such as the LiDAR data from the Raspberry Pi 4, and uses it to estimate the robot’s position within the map. AMCL is a part of the Navigation Stack and is responsible for accurately determining the robot’s position.
  Move Base :- The Move Base node is used for robot navigation. It takes in a goal location and uses the odometry and localization data from AMCL to navigate the robot to the goal location. Move Base utilizes a global planner and a local planner to plan a path to the goal and avoid obstacles in real-time.
- LiDAR Data :- The LiDAR data from the Raspberry Pi 4 is used for mapping and navigation. The LiDAR sensor scans the environment and creates a 2D map of the surroundings. This map is then used by the Navigation Stack to determine the robot’s position and plan a path to the goal.
- GMapping :- The LiDAR data from the Raspberry Pi 4 can also be used for mapping using the GMapping node. GMapping is a SLAM algorithm that uses the LiDAR data to create a map of the environment. The generated map can then be used for navigation by the Navigation Stack.

<iframe width="560" height="315" src="https://www.youtube.com/embed/07gnPGQ0gUo?si=A0t1fevo3TFhm7kz&amp;controls=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Summarizing, MR Robot represents an advanced and robust robotic platform, leveraging ROS Serial, Twist to PWM, and ESP_Diff_TF for precise motor control and odometry calculation. Navigation and localization are facilitated by the Navigation Stack, incorporating AMCL and Move Base algorithms. With the Raspberry Pi 4 interfacing with a LiDAR sensor, MR Robot adeptly harnesses LiDAR data for mapping and navigation tasks through the Navigation Stack, and alternatively utilizes GMapping for mapping purposes. In essence, MR Robot emerges as a versatile and adept solution, perfectly suited for a multitude of tasks.

Now, setting aside the technical aspects, let's delve into the more enjoyable facets of MR Robot. MR Robot is equipped with teleoperation capabilities, allowing manual control via a joystick interface for movement.This feature enable users to navigate the robot remotely, directing it’s motion with precision and flexibility. By manipulating the joystick, operators can command the robot to move forward,backward,turn and adjust it’s speed in real-time,facilitating smooth and intuitive control. Map-based techniques use pre-defined routes or optimal paths. Dynamic replanning adjusts trajectories based on real-time data, resembling rapid repositioning.

A COST map, or Coordinate System map, serves as a crucial tool for MR Robot to navigate through surroundings efficiently. By integrating data from various sensors such as LiDAR and cameras(VSLAM), the robot constructs a detailed representation of its environment within a coordinate system. This map allows MR Robot to identify obstacles, landmarks, and other relevant features, enabling it to plan and execute optimal paths to navigate safely and autonomously. By referencing the COST map in real-time, it can continuously update its position and adjust its trajectory, ensuring precise and reliable navigation through complex environments.

ROSJS serves as a vital bridge between ROS-controlled MR Robot and users within the same network, offering a seamless interface for control and interaction. By leveraging JavaScript, ROSJS facilitates the development of web-based graphical user interfaces (GUIs) that enable users to command MR Robot remotely. This enables users sharing the same network to access the MR Robot's functionalities conveniently through their web browsers. Additionally, ROSJS allows for the integration of robot control directly into websites, enabling developers to embed robot control interfaces seamlessly into web applications. With ROSJS, the barriers between website-based interfaces and ROS-controlled systems are bridged, facilitating intuitive and accessible control of robots within local network environments.

MR Robot takes on a futuristic and visually captivating appearance with the integration of neo pixel lights, whether used for aesthetic appeal or functional purposes such as signaling, these pixel lights enhance the MR Robot’s visual presence, making it stand out in various environments. Additionally, the ability to synchronize lighting with the robot's movements or interactions adds an extra layer of sophistication and charm, captivating observers. With the capability to integrate a 2D map, Setting a destination goal enables MR Robot to traverse the path effortlessly. Adding to its versatility, adjusting the speed allows for mood modulation, enhancing the interactive experience with MR Robot :

- Normal Speed ~ Happy Mood
- Sudden acceleration ~ Excited Mood
- Braking ~ Angry Mood
- Immobile ~ Bored Mood

MR Robot represents the cutting edge of technological advancement, with the ability to navigate complex environments with precision, interact seamlessly with users via intuitive controls, and exude personality through mood modulation and dynamic lighting. The combination of cutting-edge technologies like G-mapping, joystick control, new pixel lighting, live video feeds, mood modification features, and SLAM technology with plug-and-play components has transformed the landscape of autonomous mobile robots. These new features not only improve MR Robot’s functioning and versatility, but also it’s visual appeal and user experience. It holds promise for a wide range of applications across industries. As we continue to push the boundaries of MR Robot’s innovation, the future holds even more exciting opportunities for the evolution of autonomous mobile robots.

Source Links :
https://github.com/atom-robotics-lab/atom-robotics-lab.github.io/tree/main/content
