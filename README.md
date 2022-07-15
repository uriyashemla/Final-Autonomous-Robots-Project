# Final-Autonomous-Robots-Project:
![1797828_c391_3 (3)](https://user-images.githubusercontent.com/73976733/179217929-e384055e-46cf-44dc-b9ee-01a367a8aaa7.jpg)![logo_turtlebot3__79649](https://user-images.githubusercontent.com/73976733/179218124-36d5a364-d293-45b6-8443-178f36cc582a.jpg)![slam-slam_metallic](https://user-images.githubusercontent.com/73976733/179218471-b4c86aa8-9131-4b36-bcb1-532d21c905d6.gif)![download (1) (1)](https://user-images.githubusercontent.com/73976733/179221914-198d15d7-4f55-4f5b-8f2e-544a632e6782.jpg)

ROS2 package port for multi-robot autonomous exploration of map-explore. Currently tested on Foxy distros.
# About the project:
In this project our goal was to get the "robot" to navigate each space (not outer space) according to mapping and positioning (SLAM) and navigation algorithms.
We performed these operations with the help of the Ros.2 library together with RVIZ.
In order to display the simulation we used a TurtleBot simulator on top of Gazebo.

# Installing:
Ros2 Foxy https://docs.ros.org/en/foxy/Installation.html
# Building:
Build as a standard colcon package. There are no special dependencies needed (use rosdep to resolve dependencies in ROS).
# How Run the project ?:
Install nav2 and tb3 simulation. You can follow the tutorial https://navigation.ros.org/getting_started/index.html#installation.

Then just run the nav2 stack with slam:
```
export TURTLEBOT3_MODEL=waffle
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:/opt/ros/${ROS_DISTRO}/share/turtlebot3_gazebo/models
ros2 launch nav2_bringup tb3_simulation_launch.py slam:=True
```

And run this package with
```
ros2 launch explore_lite explore.launch.py
```

You can open rviz2 and add the exploration frontiers marker (topic is `explore/frontiers`) to see the algorithm working and the frontier chosen to explore.

#### Returning to initial pose
The robot will return to its initial pose after exploration if you want by defining the parameter `return_to_init` to `True` when launching the node.

#### TB3 troubleshooting (with foxy)
If you have trouble with TB3 in simulation, as we did, add these extra steps for configuring it.

```
source /opt/ros/${ROS_DISTRO}/setup.bash
export TURTLEBOT3_MODEL=waffle
sudo rm -rf /opt/ros/${ROS_DISTRO}/share/turtlebot3_simulations
sudo git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations /opt/ros/${ROS_DISTRO}/share/turtlebot3_simulations
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:/opt/ros/${ROS_DISTRO}/share/turtlebot3_simulations/turtlebot3_gazebo/models
```

Then you'll be able to run it.

### Simulation with a TB3 robot:

https://user-images.githubusercontent.com/73976733/179230281-d159ce6d-f6c3-4592-a50d-e1935cd9a4cd.mov






