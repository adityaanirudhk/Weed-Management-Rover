# Autonomous Agricultural Weed Management Rover
  The purpose of this project was to design a simple model of Weed Management Rover in SolidWorks, and simulate and control it in ROS using 
  appropriate speed and velocity contollers. The rover has a 5-DOF UR5 Robotic manipulator attached to its body to collect soil samples and destroy weed from the             agricultural land surface. The rover has a four-wheel drive powered by electric motors along with steerable front wheels.The speed and steering action are controlled     using JointPositionController and JointVelcoityController respectively. The motion of joints of the manipulators was controlled using JointTrajectoryController.  
    
  The Forward and Inverse Kinematics for the UR5 Manipulator was calculated using DH parameters and Jacobian Matrix. The DH parameters were validated by making the end-effector of the maniplator to plot a circle. The workspace study of the manipulator was being done by plotting the positions of end-effector for various joint angles. 

![image](https://github.com/adityaanirudhk/Weed-Management-Rover/assets/103492081/a24bbd38-9b53-45fa-851e-1b40cb369c7e)

![image](https://github.com/adityaanirudhk/Weed-Management-Rover/assets/103492081/1912403f-7656-4a98-9f61-3b2f92f9b348)

# Instructions to run project
Copy below packages from mars_rover/packages inside zip file into catkin_ws/src/
1) kr5_description
2) kr5_control
3) kr5_gazebo
4) kr5_moveit_config

cd ~/catkin_ws/
catkin_make clean && catkin_make
source devel/setup.bash

# RViz
roslaunch kr5_description start_kr5_description_rviz.launch

# Gazebo 
roslaunch kr5_gazebo rviz_connected_with_gz_using_moveit.launch

# Teleop
cd ~/catkin_ws/src/kr5_description/
python3 teleop_template.py

# Gazebo with controller commands
roslaunch kr5_gazebo gz_connected_with_rviz.launch  
rostopic pub /kuka/link_1_controller/command std_msgs/Float64 "data: 3.14"  
rostopic pub /kuka/link_2_controller/command std_msgs/Float64 "data: -1.0"  
rostopic pub /kuka/link_3_controller/command std_msgs/Float64 "data: -1.0"
