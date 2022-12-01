# NavQPlus\_MR-Buggy3 Tradeshow Demo Guide

## Description

{% hint style="info" %}
This section documents a tradeshow demo using both the NavQPlus and The NXP MR-Buggy3 platform. Please note that this demo is subject to ongoing changes and updates and may at some point be "broken". The information here may be useful for similar types of demonstrators.
{% endhint %}

The NavQPlus\_MR-Buggy3 demo is a demonstration of the capabilities of the NavQPlus, the MR-Buggy3 platform, and NXP's CAN Bus hardware and software support for ROS2. This guide will walk you through setting up the MR-Buggy3 demo on both your laptop and the NavQPlus. This demo consists of:

* A Gazebo Ignition simulation environment with the MR-Buggy3 model running
* Connection to the actual Buggy3 hardware meaning HITL (hardware in the loop) control of the real life MR-Buggy3
* A showcase of the NPU (neural accelerator) on the NavQPlus running inference on the real world camera data **as well as** a virtual camera from the simulation environment
* ROS2 <-> Cyphal\* <-> uORB transport (\*transport layer only)
* CAN communications from NavQ+ to the UCANS32K146 CAN-FD node driving a PWM and LED
* PWM control in PX4 using the PCA9685

### Setting up the laptop

To run this demo, you must have an Ubuntu 20.04 or 22.04 machine. It is recommended that you use a machine that has a dedicated GPU and that is running Ubuntu natively.

### First step: Running the NXP install script

Download the nxp\_install.sh script using a webbrowser to your local Linux machine.(Currently this) is located at&#x20;

`https://github.com/rudislabs/nxp_install.git`

Run&#x20;

`chmod a+x install.sh`

on this script and run it on your machine.&#x20;

This will install ROS2 and all required dependencies.

{% hint style="info" %}
On systems where you have upgraded from Ubuntu 20.04 to 22.04 errors may be  encountered. This can become somewhat complex to resolve. A clean install is always best. Alternatively, try completely removing the old ROS directories (save any personal work) and any repository references to ROS Foxy vs Humble.\
\
The base thing to try first:\
If there is an error with the install.sh script, the first remedy to try is repeating the ROS2 sources install steps as outlined here:\
[https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html#setup-sources](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html#setup-sources)\

{% endhint %}

### Second step: Creating a ROS2 workspace and building sim\_ignition\_bringup

It is recommended that you create a ROS2 workspace at \~/git/ros2/, but you are free to create it wherever you want. In this gude, we will use that location. Follow the steps below.

```
$ mkdir -p ~/git/ros2/src
$ cd ~/git/ros2/src
$ git clone https://github.com/rudislabs/sim_ignition_bringup.git -b RoverGamesDemo
$ cd ..
$ colcon build --symlink-install
$ echo "source /home/$USER/git/ros2/install/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```

## Setting up the NavQ+

### First step: Running the NXP install script

Follow the steps used above for your laptop to set up ROS2 on your NavQ+.

### Second step:

You'll want to also create a ROS2 workspace on your NavQPlus. This step is similar to the step for setting up the laptop, but instead of cloning sim\_ignition\_bringup, you'll want to clone ros2\_orchestrator. Follow the steps below.

```
$ mkdir -p ~/git/ros2/src
$ cd ~/git/ros2/src
$ git clone https://github.com/rudislabs/ros2_orchestrator.git -b NavQPlusPX4Demo
$ cd ..
$ colcon build --symlink-install
$ echo "source /home/$USER/git/ros2/install/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```

## Running the simulation

Once you have connected everything according to the block diagram shown below, you will be ready to run the demo.

![](../.gitbook/assets/mr-buggy3-demo-block-diagram.pdf)

To run the demo, open 4 terminal windows. Start with the battery plugged in and powering everything over the PDB, and make sure that the ESC is turned OFF.

### Terminal 1

SSH into the NavQ+, then navigate to \~/git/ros2/src/canfd\_msgs/scripts/. Inside this folder, run `./launch_example.sh`. You should see the UCAN board turn on, start sending heartbeat messages, and then stop. NOTE: You should also see a 64 byte CAN frame get sent. This is the initialization for the PCA9685 PWM Driver. Once this message is sent, you are free to turn on your ESC.

### Terminal 2

Run `ros2 launch sim_ignition_bringup sim_ignition_bringup.launch.py` and wait for the simulation to fully start.

### Terminal 3

SSH into the NavQ+, then run `ros2 launch ros2_orchestrator orchestrate.launch.py`

### Terminal 4

This terminal is for checking ros2 topics, launching additional rqt\_image\_views, and other commands as needed.

You should now have a working demo! The simulated car should be driving around the track. In each of the rqt\_image\_view windows that open, you can view the various camera streams that are running. Camera streams that are labeled "Debug" show the NPU inference running.
