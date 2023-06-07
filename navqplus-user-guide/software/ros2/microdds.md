# MicroDDS Agent/MicroROS

## Introduction

{% hint style="success" %}
The following was user contributed content and edited by NXP. Note that there are several methods available for communication between ROS and PX4. This documents an established method.
{% endhint %}

## Setting up the MicroDDS Agent/MicroROS

One method used to communicate between the NavQPlus and the FMUK66v3 using T1 or Serial is by using MicroROS or the XRCE-dds Agent. \
\
To install these tools:

```
git clone https://github.com/eProsima/Micro-XRCE-DDS-Agent
cd Micro-XRCE-DDS-Agent
mkdir build && cd build
cmake ..
make
sudo make install
```

If using yocto, you can use the WIP meta package in your recipe.

```
https://github.com/dirksavage88/meta-dds
```

Alternatively, you can install micro-ROS through the ubuntu snap store

{% embed url="https://snapcraft.io/install/micro-ros-agent/ubuntu" %}
micro-ROS snap package
{% endembed %}

Another way to get micro-ROS is through Github as a ROS2 package. You can use the colcon build tools after sourcing the ROS setup.bash script in "/opt/ros/galactic/setup.bash"

{% embed url="https://github.com/micro-ROS/micro_ros_setup.git" %}
micro-ROS package
{% endembed %}

```
colcon build --symlink-install
```

Follow the instructions for each package on how to run the agent. The agent is a broker for clients on the network (including the FMUK66) and allows topics from the pixhawk to be shared with the DDS global space.

To set up the NavQ+, follow instructions in the Setup Guide -eMMC for a static IP. The FMUK66 is IP "10.0.0.1". As an example, you can set the NavQ+ to "10.0.0.3" with a blank ipv4.gateway (no quotes or anything) on Wired Connection 1.

Then start the microdds agent that is installed in the home directory in the Micro-XRCE-DDS-Agent build folder.

```
./MicroXRCEAgent udp4 -p 2019
```

On the FMUK66, ensure you have flashed to main and enter the following command.

```
microdds_client start -t udp -h 10.0.0.3 -p 2019
```

You should see the topic listed in the mavlink console after running the client start, as well as topic, publishers, data writers, and creators on the agent side.
