# Installation

Follow the complete guide at [Learning Robotics with ROS made easy](https://medium.com/@brjapon/learning-robotics-with-ros-made-easy-304bde0a9dfc).

Include ROS package [teleop_tools](https://github.com/ros-teleop/teleop_tools) for teleoperating the robot.
Whenever you want to teleoperate the robot in Gazebo or the physical GoPiGo3, launch the node as follows:

- `$ rosrun key_teleop key_teleop.py /key_vel:=/cmd_vel`


# Package `gopigo3_description`

1. `$ roslaunch gopigo3_description gopigo3_rviz.launch`
    - Load the current `gopigo3.urdf` model of the robot

1. `$ roslaunch gopigo3_description gopigo3_rviz.launch gui:=True`
    - Plus widget to interactively rotate the right and left wheels

# Package `gopigo3_fake`
1. `$ roslaunch gopigo3_fake gopigo3_fake.launch`
    - `$ rosrun key_teleop key_teleop.py /key_vel:=/cmd_vel`

# Package `gopigo3_bringup`

BRINGUP GOPIGO3

   - `$ roslaunch gopigo3_bringup starter_kit.launch` for full configuration: drives + distance sensor + LDS + camera (yet to be included)

TEST INDIVIDUALLY for each of the involved hardware

1. Distance sensor: `$ roslaunch bringup_car distance_sensor.launch`
    - Subscribe to the topic in another terminal: `$ rostopic echo distance_sensor/distance`
    - Plot the graph of distance vs time in the laptop: `$ rqt_plot` and write the name of topic `/distance_sensor/distance`
    
1. Drives (teleoperation) `$ roslaunch bringup_car differential_drives.launch`
    - `$ rosrun key_teleop key_teleop.py /key_vel:=/cmd_vel`