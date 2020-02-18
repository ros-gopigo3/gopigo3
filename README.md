# Installation

Follow the complete guide at [Learning Robotics with ROS made easy](https://medium.com/@brjapon/learning-robotics-with-ros-made-easy-304bde0a9dfc).

Include ROS package [teleop_tools](https://github.com/ros-teleop/teleop_tools) for teleoperating the robot.
Whenever you want to control the robot in Gazebo or the physical GoPiGo3, launch the node as follows:

- `$ rosrun key_teleop key_teleop.py /key_vel:=/cmd_vel`


# Package `gopigo3_description`
The package `gopigo3_description` contains the URDF description of GoPiGo3 that you can use to perform simulations of the robot.

1. `$ roslaunch gopigo3_description gopigo3_rviz.launch`
    - Load the current `gopigo3.urdf.xacro` model of the robot

1. `$ roslaunch gopigo3_description gopigo3_rviz.launch gui:=True`
    - Plus widget to interactively rotate the right and left wheels

# Package `gopigo3_fake`
The package `gopigo3_fake` allows to experiment with GoPiGo3 without needing the physical one. Yo can use if, for example, to explore its kinematics 

`$ roslaunch gopigo3_fake gopigo3_fake.launch`
   - `$ rosrun key_teleop key_teleop.py /key_vel:=/cmd_vel`

# Package `gopigo3_bringup`
The package `gopigo3_bringup` allows the user to operate the robot including the distance sensor and the servomotors of the wheels.

BRINGUP GOPIGO3

   - `$ roslaunch gopigo3_bringup starter_kit.launch` for Starter Kit configuration: servomotors of the wheels + distance sensor

TEST INDIVIDUALLY for each of the involved hardware

1. Distance sensor: `$ roslaunch bringup_car distance_sensor.launch`
    - Subscribe to the topic in another terminal: `$ rostopic echo distance_sensor/distance`
    - Plot the graph of distance vs time in the laptop: `$ rqt_plot` and write the name of topic `/distance_sensor/distance`
    
1. Drives (teleoperation) `$ roslaunch bringup_car differential_drives.launch`
    - `$ rosrun key_teleop key_teleop.py /key_vel:=/cmd_vel`