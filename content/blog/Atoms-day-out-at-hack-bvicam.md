---
title: "A.T.O.M's Day Out at Hack-BVICAM'22"
date: 2022-03-28T13:56:06+06:00
image: images/blog/hack-bvi-cam-blog/hack-bvi-cam-cover.jpg
feature_image: images/blog/hack-bvi-cam-blog/hack-bvi-cam-cover.jpg
author: Jasmeet Singh
---

On 11th March 2022, we participated in HACK-BVICAM distributed in 3 teams led by 3 of our admins Naman Malik, Jasmeet Singh and Manav Sethi.
The competition had 5 positions on the podium, out of which our teams bagged 3 positions! We won a total of 15k cash prize, 3 smartphones & many goodies leading to a total prize pool of around 50k! 

The hackathon had many tech-related themes like AI/ML, Future Mobility, IoT, FinTech etc. Out of these tracks, our teams developed real-world projects related to Future Mobility, IoT & Smart City tracks.

#### Okay, That's great.....But what is a Hackathon anyway?

If you are reading this blog, then either you know what hackathons are or you are eager to find out. In any case, let me just brief you about *'Hackathons'*. 

Hackathons are *generally* overnight events in which makers and engineers get together as teams to create a solution from scratch for some real-world problems.
Some hackathons target very generic industries like Healthcare, Education, FinTech etc. while others target really specific problem statements like 'Building an Autonomous Solution for Counting Large Steel Pipes for Inventory Management.

Participants in a 24 - 36 hour period of the hackathon, not only brainstorm over the technical aspects of a project but also over the real-world implementation of their solution as a business. Hackathons are a great opportunity for getting yourself acquainted with new technologies and new people. So even if you don't complete your project in time, you still got a ton of networking to do which is equally helpful. 

So basically the benefits of a hackathon can be summarized as follows:
 * Lots of challenging problems solving and brainstorming
 * Working on new technologies and stacks
 * Lots and Lots of Networking
 * A whole day of fun and free food (we all love that, don't we?)
 * Tons and Tons of swags like T-shirts, stickers, badges etc. (We all like to wear those t-shirts as badges of honor 😎)

And do you know the best part? It's that well-earned sleep that comes after spending a whole sleepless 24 hours working 😴.

If you want to know more about hackathons, I recommend reading [Advice to Students for Hackathons](https://abhas.io/advice-to-students-for-hackathons/) by Abhas Abhinav.

{{<figure src="/images/blog/hack-bvi-cam-blog/working_group_photo.jpg" caption="Fig 1: All A.T.O.M members working hard on their respective projects.....or are they? :p">}}

#### The Projects we made


##### Coal Miner Monitoring System: Team RUNTIME_TERROR (First Prize)

Team RUNTIME_TERROR won the first position with a cash prize of 10k and a smartphone for the best performing member. The team developed a **hardware-based** project for **monitoring the working conditions of workers in hazardous conditions like coal mines**. The project consisted of a **smart wearable device** (image below), which could be attached to the belt of the worker, like a holster. This piece of hardware contained a plethora of **sensors like accelerometer, smoke sensor, humidity sensor and temperature sensor**. Long-range **RF transceiver modules** were used to transfer this data to a central hub that was connected to the internet. This **data** was then **visualized on a web-based dashboard**, where an **admin** could **monitor sensory data** for each worker. The real-time sensor data could be used to **detect emergency conditions like fall detection, gas leak etc.**

Tech Stack Used in the Project:
 * Esp32 connected to the internet for a central hub
 * Arduino Uno for each wearable Devices
 * DHT11 temperature Sensor, MPU6050 Accelerometer, MQ2 Gas Sensor
 * HC-12 Transceiver modules with helical antenna for Long Range RF communication
 * Grafana for Data visualization Dashboard 
 * MQTT for real-time communication between Central hub and Dashboard

The project source code can be found on our GitHub page: <a href="https://github.com/atom-robotics-lab/BVPICAM-RUNTIME_TERROR">https://github.com/atom-robotics-lab/BVPICAM-RUNTIME_TERROR</a>

{{<figure src="/images/blog/hack-bvi-cam-blog/runtime_terror_award.jpg" width=100% caption="Fig 2: Team RUNTIME_TERROR receiving the award(left)  Team Leader Naman wearing the Wearable Device the Team Made(Right)">}}
{{<figure src="/images/blog/hack-bvi-cam-blog/runtime_terror_grafana.png" width=100% caption="Fig 3: Grafana Dashboard showing the sensor values for coal miner">}}


##### Holistic Traffic Management System: Team Atom (Second Prize)

Team Atom bagged the second position with a cash prize of 5k and a smartphone for the best-performing member. This team also developed a **hardware-based project** for a **holistic traffic management** related to the theme 'Smart Cities. The project had **multiple IR sensors embedded on the road** to **determine the density of traffic waiting** on a particular signal. Depending on the density of vehicles, the traffic lights were controlled to relieve the traffic on the congested side. Apart from this, an **RFID receiver** was also installed which **detected a passing emergency vehicle** such as an ambulance or police car and **appropriately assigned priority to a particular traffic light to go green.**

Tech Stacks used in the Project:

* Multiple IR Proximity sensors to detect the amount of traffic.
* Micro servo to create a barrier
* RGB led to creating traffic light
* RC522 RFID sensor module and RFID card to represent an emergency vehicle
* ESP32 module to publish traffic data over the internet
* Grafana for data visualization dashboard

The project source code can be found on our GitHub page: <a href="https://github.com/atom-robotics-lab/holistic-traffic-management-system-">https://github.com/atom-robotics-lab/holistic-traffic-management-system-</a>

{{<figure src="/images/blog/hack-bvi-cam-blog/atom_award.jpg" width=100% caption="Fig 4: Team Atom receiving the award(left)  Hardware Setup for the Team Atom's Project(Right)">}}

##### Project Know-Parking: Team Galat Family (Runner's Up) 

Team Galat Family (yep that was our team's name ¯\\\_(ツ)_/¯) received the runner's position with lots of swags and a smartphone for the best performing member. Their project, **Know-Parking**, was based on making a **Smart Parking System that allows you to Book Parking Spots in public spaces just like you book seats for a movie show**. The project used **Computer Vision** on **live video stream** from **CCTV cameras** to **detect empty parking spots** instead of installing hardware to **reduce implementation and management costs**. The **parking layout** was accordingly **updated on a web interface**. The **web interface** allowed the **user to book a spot** which was then **blocked by a barrier in real-time**. All this was **demonstrated** to the judges using a **Simulation** for better understanding. The project used **ROS** which is the **same stack used in robots**. This provided us with **many interesting future aspects like indoor navigation etc.**

Tech Stacks Used in the Project:
 * OpenCV and Python for Computer Vision
 * HTML, CSS and JavaScript for Web Interface
 * ROS (Robot Operating System) for the whole distributed system
 * Gazebo Simulator for simulating the parking space and demonstrating the OpenCV Algorithm
 * RosJS library for connecting web interface to ROS Master


The project source code can be found on our GitHub page: <a href="https://github.com/atom-robotics-lab/Know_Parking">https://github.com/atom-robotics-lab/Know_Parking</a>

{{<figure src="/images/blog/hack-bvi-cam-blog/galat_family_award.jpg" width=100% caption="Fig 5: Team Galat Family receiving the Award">}}

{{<figure src="/images/blog/hack-bvi-cam-blog/galat_family_sim.jpg" width=100% caption="Fig 6: Parking Simulation in Gazebo with Empty Parking Space Detection with OpenCV">}}

{{<figure src="/images/blog/hack-bvi-cam-blog/galat_family_frontend.jpg" width=100% caption="Fig 7: Know-Parking Web based interface">}}



> All in all, the hackathon was a great learning and bonding experience for the whole society. We met & interacted with many people with different backgrounds and ideas. It was great to attend an offline event after a long period of isolation due to the COVID19 pandemic!

