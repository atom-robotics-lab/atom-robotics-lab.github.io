---
title: "Install ROS on Brainy-pi"
date: 2022-11-21T13:56:06+06:00
image: images/blog/brainy-pi/cover2.png
feature_image: images/blog/brainy-pi/blog_cover.png
author: Manan Gupta
---

This blog is mainly going to focus on answering your questions like ‘What is Brainy-Pi’, ‘What is ROS’ and ‘How to install ROS on Brainy-Pi’

## What is Brainy-Pi?

Brainy-pi is a single chip computer inspired by Raspberry-pi made by IoTIoT, an Indian startup. The brainy-pi is currently(when this blog was written) in the development stage. Its motive is to provide an made-in-India alternative version of raspberry pi.
To know more about it head on to the official [BrainyPi](https://brainypi.com) website.


![Brainy-pi dev board](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zjpqlewlgkmrtzeqyucg.png)


## What is ROS?

The Robot Operating System [(ROS)](https://www.ros.org/) is an open-source framework that helps researchers and developers build and reuse code between robotics applications. ROS is also a global open-source community of engineers, developers and hobbyists who contribute to making robots better, more accessible and available to everyone.


![ROS](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/z7vqv3st6un4krmpwiei.png)


## Installing ROS on Brainy-pi

Now to answer the big question; ‘is brainy-pi even compatible with ROS?’, The answer to that question is yes and its installation is as easy as installing ROS on any other device.

### Flashing Brainy-pi with ubuntu

To install ROS on your brainy pi you would first need to flash an image of Ubuntu in it. To flash the image first plug in your mouse and keyboard to the brainy-pi and connect the HDMI cable to a screen and power it on using a USB type-C cable. By default the brainy pi will boot into the recovery OS for the first time where you can select the OS you want to install(Ubuntu is not set as one of the default OS for brainy pi but do not worry). 

To add Ubuntu to the download options follow these steps

#### Step 1: Configure brainypi-recovery to install Ubuntu

We need to create a file at location /boot/settings/os-sources.list and change the source variable in the file to Ubuntu.
```shell
sudo mkdir -p /boot/settings
sudo touch /boot/settings/os-sources.list
cat <<EOF | sudo tee /boot/settings/os-sources.list
SOURCE_URL="http://releases.brainypi.com/ubuntu"
SOURCE_REPO="testing"
EOF
```
> Now the brainypi-recovery is configured and it will install Ubuntu 18.04.

Enable Console on the Monitor, Ubuntu 18.04 does not have a GUI, so console needs to be enabled manually.
```shell
cat <<EOF | sudo tee /boot/extlinux/extlinux.conf
label Ubuntu 18.04
    kernel /Image
    fdt /rk3399-brainypi.dtb
    append earlycon=uart8250,mmio32,0xff1a0000 swiotlb=1 coherent_pool=1m earlyprintk console=ttyS2,1500000n8 console=tty0 init=/sbin/init
EOF
```

Now reboot to the Recovery OS.

Now you should be able to install ubuntu 18.04 on brainy-pi.

Since we are using Ubuntu 18.04, we have to use the ROS version compatible with it, that is ROS melodic.(you can use any ubuntu version you like, just make sure to use the version of ROS compatible with it)

### Installation of ROS

#### Setup your source list

Setup your pc/pi to accept software from packages.ros.org.

```shell
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

#### Setup your keys

> Curl needs to be installed if you haven't already

```shell
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
#### Installation

Update your packages

```shell
sudo apt update
```

Install ROS

```shell
sudo apt install ros-melodic-desktop-full
```

### Configuration Steps

Now that you have ROS installed in your device, you need to configure it so that you can use it to the fullest.

Adding environment variables: To Automatically add ROS environment variables to your bash session every time a new shell (terminal) is launched.

```shell
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

Before you can use many ROS tools, you will need to initialise rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS. If you have not yet installed rosdep.

```shell
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
sudo rosdep init
rosdep update
```

### Installing additional packages

> You may or may not need these packages but it's good to have them in case you ever need it.

Catkin tools

```shell
sudo apt-get install ros-melodic-catkin python3-catkin-tools
```

std_msgs package
```shell
sudo apt install ros-melodic-std-msgs
```

Turtlesim
```shell
sudo apt-get install ros-melodic-ros-tutorials
```

### Creating the workspace

Having a workspace directory for ROS is important because it allows for better distribution of packages, better cross compilation, better portability, plus all your work is stored under a single directory.

Create the root workspace directory. You can name your directory anything but by ROS convention we will use catkin_ws as the name
```shell
cd ~/
mkdir -p ~/catkin_ws/src/
```

Initialise the workspace
```shell
cd catkin_ws
catkin init
```

Build the workspace
```shell
catkin_make
```

Now to make your installation detectable in ROS, we have to source the workspace
```shell
source ~/catkin_ws/devel/setup.bash
```

The setup.bash needs to be sourced everytime. So to avoid that we will simply add this command to your bashrc
```shell
sudo nano ~/.bashrc
source ~/catkin_ws/devel/setup.bash
```
> **Note**: make sure to add this line at the end of your bashrc file.
Now simply save(ctrl+o) and exit(ctrl+x)

Now that your installation is done and your workspace has been successfully created, you can create packages, scripts etc according to your use.

### Creating a ROS package

Software in ROS is organized in packages. A package might contain ROS nodes, a ROS- independent library, a dataset, conﬁguration ﬁles, a third-party piece of software, or anything else that logically constitutes a useful module.The goal of these packages it to provide this useful functionality in an easy-to-consume manner so that software can be easily reused.

To create a ROS package you first nee to  navigate to the source space directory of the catkin workspace you’ve created.
```shell
cd ~/catkin_ws/src
```

Now, use the catkin_create_pkg script to create a new package called pkg_ros_basics which depends on std_msgs, roscpp, and rospy:
```shell
catkin_create_pkg pkg_ros_basics std_msgs rospy roscpp
```

Now, you need to build the packages in the catkin workspace
```shell
cd ~/catkin_ws
catkin_make
```
> Inside the package, there are src folder, package.xml , CMakeLists.txt , and the include folders.

### Creating a ROS node and running a basic script

In this section we will learn how to create a ROS Node inside pkg_ros_basics ROS Package which we created in the previous section.

Navigate to pkg_ros_basics
```shell
cd ~/catkin_ws/src/pkg_ros_basics
```

Create a scripts folder for your Python scripts and navigate into the folder.
```shell
mkdir scripts
cd scripts
```

Create a Python script called node_hello_ros.py .
```shell
touch node_hello_ros.py
```

Open the script in any text-editor and start editing.
```shell
gedit node_hello_ros.py
```

>First line of all your Python ROS scripts should be the following shebang, i.e.
```shell
#!/usr/bin/env python3
```

Now write a ROS Node to print Hello World! on the console.
```shell
#!/usr/bin/env python
import rospy
def main():
#Initialize the new node
rospy.init_node('node_hello_ros', anonymous=True)
#  Print info on console.
rospy.loginfo("Hello World!")

if __name__ == '__main__':

    try:
        main()
    except rospy.ROSInterruptException:
        pass
```
> save the script and exit the gedit.

Make your node executable
```shell
sudo chmod +x node_hello_ros.py
```

Now to run your node

Open the terminal and run ROS master
```shell
roscore
```

Once the roscore is running open a new terminal and run the main node
```shell
rosrun pkg_ros_basics node_hello_ros.py
```
> **Note** This command will work only if you have sourced setup.bash of your catkin workspace either manually or using .bashrc .


**Congratulations. Now your brainy-pi has ROS installed in it. Now you can use it in any way you like.**