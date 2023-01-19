# ROS2

{% hint style="info" %}
If using an downloaded image, check first that these packages are not already installed.
{% endhint %}

## Installing ROS2 on the NavQPlus

We have prepared an install script that will install ROS2 and all necessary packages on the NavQPlus.

To get the install script and run it, you can run the following in the terminal:

```
wget https://raw.githubusercontent.com/rudislabs/nxp_install/main/install.sh
chmod +x install.sh
./install.sh
```

## Setting up the MicroDDS Agent/MicroROS

In order to communicate with the FMUK66v3 (via T1 or Serial), you will need to install either MicroROS or the XRCE-dds Agent.

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

Then I start the microdds agent that is installed in my home directory in the Micro-XRCE-DDS-Agent build folder.

```
./MicroXRCEAgent udp4 -p 2019
```

On the FMUK66, ensure you have flashed to main and enter the following command.

```
microdds_client start -t udp -h 10.0.0.3 -p 2019
```

You should see the topic listed in the mavlink console after running the client start, as well as topic, publishers, data writers, and creators on the agent side.
