---
description: A simple ROS2 example
---

# ROS2 example

## Introduction

This page will go through a simple example using ROS on the NavQPlus.  More examples and details can be found on the ROS webpage linked bellow. This example is a shortened version of the Publisher Subscriber for Python tutorial. You will need to have ROS2 installed already before trying this example.&#x20;

{% embed url="http://docs.ros.org/en/humble/Tutorials.html" %}

## ROS2 Publisher Subscriber in Python example

In this tutorial, you will create [nodes](http://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html) that pass information in the form of string messages to each other over a [topic](http://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html). The example used here is a simple “talker” and “listener” system; one node publishes data and the other subscribes to the topic so it can receive that data.

### Step 1 - Create workspace

First step is to make a [workspace](http://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html#new-directory) for your project to build in. Go to your home folder and create a workspace called `/ros2_ws`. With another directory inside `/src` for your project to be in.

```
mkdir -p ~/ros2_ws/src
```

Then move into the `/src` directory:

```
cd ~/ros2_ws/src
```

### Step 2 - Create package

Now we want to create a package inside the directory we just created.

```
ros2 pkg create --build-type ament_python py_pubsub
```

Your terminal will return a message verifying the creation of your package `py_pubsub` and all its necessary files and folders.

### Step 3 - Publisher code

Navigate to the new directory location created.&#x20;

```
cd ~/ros2_ws/src/py_pubsub/py_pubsub
```

Now download the example publisher code:

```
wget https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
```

You should now see a new file located in the `py_pubsub` directory. To understand more about the code, follow the tutorial through the [ROS webpage](http://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Publisher-And-Subscriber.html).

### Step 4 - Subscriber code

For the subscriber code stay in the same directory and download the following:

```
wget https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py
```

With this done you will have both `publisher_member_function.py` and `subscriber_member_function.py` files in your directory. Plus, the `__init__.py`.

### Step 5 - Add dependencies

The next step is to modify some of the files created to support the code we just downloaded. We will be adding the dependencies. Navigate one level back to `~/ros2_ws/src/pubsub`.

Open the `package.xml` file with a text editor. We will be using `nano` for this tutorial.

```
nano package.xml
```

After the `<license>` line add the following lines of code:

```
<exec_depend>rclpy</exec_depend>
<exec_depend>std_msgs</exec_depend>
```

Your new file now should look something similar to this:

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

Exit the file editor and save.

### Step 6 - Add entry point

&#x20;The next file you will have to modify is the `setup.py` file.&#x20;

```
nano setup.py
```

Add the following line within the `console_scripts` brackets of the `entry_points` field:

```
entry_points={
        'console_scripts': [
                'talker = py_pubsub.publisher_member_function:main',
                'listener = py_pubsub.subscriber_member_function:main',
        ],
},
```

Don't forget to save!

### Step 7 - Building and running

First, go back to the root of your workspace:

```
cd ~/ros2_ws
```

Then, check if you have any missing dependencies in your code by running:

```
rosdep install -i --from-path src --rosdistro humble -y
```

If everything is installed successfully you can build your package with `colcon`:

```
colcon build --packages-select py_pubsub
```

With the build finished we need to source the setup files.&#x20;

```
source install/setup.bash
```

Finally, we can run the code. You will need two terminals to run both the publisher and subscriber.&#x20;

{% hint style="warning" %}
On the new terminal you will have to go to the workspace the project is in and source the setup files.
{% endhint %}

In one terminal run the publisher:

```
ros2 run py_pubsub talker
```

You should see that the code starts running and prints:

```
[INFO] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [minimal_publisher]: Publishing: "Hello World: 3"
[INFO] [minimal_publisher]: Publishing: "Hello World: 4"
...
```

On the other terminal run the subscriber:

```
ros2 run py_pubsub listener
```

When you run the listener, you will start to see the message from the publisher:

```
[INFO] [minimal_subscriber]: I heard: "Hello World: 10"
[INFO] [minimal_subscriber]: I heard: "Hello World: 11"
[INFO] [minimal_subscriber]: I heard: "Hello World: 12"
[INFO] [minimal_subscriber]: I heard: "Hello World: 13"
[INFO] [minimal_subscriber]: I heard: "Hello World: 14"
```

Use `Ctlr + C` in each terminal to stop the code.

### &#x20;Summary

You created two nodes to publish and subscribe to data over a topic. Before running them, you added their dependencies and entry points to the package configuration files.
