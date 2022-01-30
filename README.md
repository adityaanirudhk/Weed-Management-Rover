ENPM662 Project 2

Authors: Rohit Patil 
         Abhijit Mahale

Email:   rpatil10@umd.edu
         abhimah@umd.edu


#############################
# Instructions to run project

Copy below packages/folder from Robot_packages folder inside zip file into catkin_ws/src/
1) kr5_description
2) kuka_kr5_control
3) kuka_kr5_gazebo
4) kuka_moveit_config


cd ~/catkin_ws/
catkin_make clean && catkin_make
source devel/setup.bash


######################
# RVIZ

roslaunch kr5_description start_kr5_description_rviz.launch


####################
# GAZEBO and TELEOP

roslaunch kuka_kr5_gazebo rviz_connected_with_gz_using_moveit.launch

--------- Teleop---------
cd ~/catkin_ws/src/kr5_description/
python3 teleop_template.py


#####################################
# GAZEBO with controller commands

roslaunch kuka_kr5_gazebo gz_connected_with_rviz.launch


rostopic pub /kuka/link_1_controller/command std_msgs/Float64 "data: 3.14"

rostopic pub /kuka/link_2_controller/command std_msgs/Float64 "data: -1.0"

rostopic pub /kuka/link_3_controller/command std_msgs/Float64 "data: -1.0"

