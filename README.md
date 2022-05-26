# Mobile platform with robotic arm example




# Prerequsites :
1. Ubuntu 20.04 :
[Ubuntu 20.04 download link](http://handlebarsjs.com/),
2. Ros Noetic, follow this [link](http://wiki.ros.org/noetic/Installation/Ubuntu)  or guide below : 
  ```sh
  sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
  sudo apt install curl -y
  curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
  sudo apt update
  sudo apt install ros-noetic-desktop-full -y
  ```
  Now you can source your ROS setup file by typing : 
  ``` sh
  source /opt/ros/noetic/setup.bash
  ```
  3. Additional dependencies : 
  ``` sh
sudo apt install -y python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
sudo apt install -y python3-rosdep
sudo apt-get install -y ros-noetic-ros-control
sudo apt-get install -y ros-noetic-ros-controllers
sudo apt-get install -y ros-noetic-gazebo-ros-control
  ```
  Now you can init your rosdep : 
  ``` sh
sudo rosdep init
rosdep update
  ```
  4. Create your catkin workspace, clone git repository and make launch files: 
   ``` sh
   cd ~
mkdir -p catkin_ws/src && cd catkin_ws/src
git clone https://github.com/Edekheh/Mobile_Platform_example.git
cd ~/catkin_ws && catkin_make
  ```
  # Play with example :
Now you cant start using this example, if you have terminator you can split it to 3 windows, and source setup file in every window. For using tab(helping you with finding packages and commands you must source devel/setup.bash in addition.
  ``` sh
source /opt/ros/noetic/setup.bash
source ~/catkin_ws/devel/setup.bash
  ```
  1. To start playing with mobile platform only you can use (every command in separate window or terminal): 
  ``` sh
roslaunch mobile_manipulator_body base_gazebo_control.launch
rosrun rqt_robot_steering rqt_robot_steering
rostopic list
  ```
  After launching rqt_robot_steering you must change publish topic for Robot Steering to : 
  ``` sh
/robot_base_velocity_controller/cmd_vel
 ```

  2.  To start playing with mobile platform only you can use (every command in separate window or terminal): 
  ``` sh
roslaunch mobile_manipulator_body arm_gazebo_control.launch
rostopic list
rostopic pub /arm_controller/command trajectory_msgs/JointTrajectory '{joint_names: ["arm_base_joint","shoulder_joint", "bottom_wrist_joint", "elbow_joint","top_wrist_joint"], points: [{positions: [-0.1, 0.5, 0.02, 0, 0], time_from_start: [1,0]}]}' -1
  ```

  3.   To start playing with mobile platform with robotic arm you can use (every command in separate window or terminal): 
  ``` sh
roslaunch mobile_manipulator_body mobile_manipulator_gazebo.launch
rostopic list
  ```
  For stearing mobile platform or robotic arm use commands from points 1 and 2.
Resources :  https://automaticaddison.com/how-to-build-a-simulated-mobile-manipulator-using-ros/?fbclid=IwAR3K5lET6mD-uIjI4N_832OBdfDKRjYWYyrmm31dZ0ChFQkJFEeGJrraR3M
