# Mobile_Platform_example
You should create catkin_ws directory and clone this repo inside src folder.
Requirements : 
ubuntu 20.04
Ros noetic, install guide :
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

sudo apt install curl

curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

sudo apt update

sudo apt install ros-noetic-desktop-full

source /opt/ros/noetic/setup.bash
^^source every time you want to use ros noetic
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential

sudo apt install python3-rosdep

sudo rosdep init

rosdep update

Guide : http://wiki.ros.org/noetic/Installation/Ubuntu

Additional dependencies : 
sudo apt-get install ros-noetic-ros-control
sudo apt-get install ros-noetic-ros-controllers
sudo apt-get install ros-noetic-gazebo-ros-control

When inside catkin_ws directory : 
catkin_make

For using example  :
roslaunch mobile_manipulator_body base_gazebo_control.launch

In another terminal, after sourced /opt/ros/noetic/setup.bash : 
rosrun rqt_robot_steering rqt_robot_steering
Now you must change Robot Steering topic to : 
/robot_base_velocity_controller/cmd_vel

You could go to another terminal, and see topic list (after sourcing setup.bash) :
rostopic list

Resources : 

https://automaticaddison.com/how-to-build-a-simulated-mobile-manipulator-using-ros/?fbclid=IwAR3K5lET6mD-uIjI4N_832OBdfDKRjYWYyrmm31dZ0ChFQkJFEeGJrraR3M
