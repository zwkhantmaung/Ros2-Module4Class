we need only these three steps for ros2:
    write yml file 
    write urdf file
    write launch file

sudo apt install ros-humble-gazebo-ros*
ros2 run xacro xacro my_robot.xacro > my_robot.urdf
ros2 launch rom2109_gazebo simulation.launch.py
ros2 run teleop_twist_keyboard teleop_twist_keyboard /cmd_vel:=/cmd_vel_keyboard

ros2 interface proto sensor_msgs/msg/Imu
ros2 topic list
ros2 topic info /diff_cont/odom
ros2 interface proto nav_msgs/msg/Odometry
ros2 topic echo /diff_cont/odom
ros2 topic list
ros2 topic info /imu_plugin/out
ros2 interface proto sensor_msgs/msg/Imu
ros2 topic list
ros2 topic info /scan
ros2 interface proto sensor_msgs/msg/LaserScan
ros2 topic echo sensor_msgs/msg/LaserScan
ros2 topic echo /scan 


Hardware:
    micro-controller (stm32, )
    motor
    motor driver
    lidar
    IMU
    battery
    computer (miniPC, Pi, JetsonNano)

Simulation (Gazebo):
    Robot Body Design (URDF file)
    Description package (urdf file read, robot state & joint state launch)
    ros2_control_name tag xacro, gazebo plugin (sensors, hardware interface) > Generate urdf file
    ros2_control config yaml file
    gazebo package (diff_cont, joint_broad, spawner robot, gazebo, description launch, rvit)

Actual Robot:
    Micro-controller Firmware and communicate with pc
    Serial Communication + ros2_control
    Robot Body Design (URDF file)
    Description package (urdf file read, robot state & joint state launch)
    ros2_control_name tag xacro, plugin microcontroller hardware interface Name
    Hardware Interface
    ros2_control config yaml file
    controller package (diff_cont, joint_broad, controller_manager, robot_state)
