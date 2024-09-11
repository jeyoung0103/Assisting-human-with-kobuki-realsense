### Assisting-human-with-kobuki-realsense

## 1. Settings
# 1-1. Kobuki setting
(ref.  https://gosury32.tistory.com/5
       https://github.com/martinerk0/kobuki_noetic/blob/master/install_kobuki_noetic.sh)
1) Using Ubuntu 20.04
   (we used this version due to set ROS1 for kobuki)

2) Set ROS1 (ros noetic)
   Follow the steps : http://wiki.ros.org/noetic/Installation/Ubuntu

3) After setting ROS1 in Ubuntu, set Kobuki
  sudo apt install liborocos-kdl-dev
  sudo apt install ros-noetic-ecl-*
  sudo apt install libusb-dev
  sudo apt install libftdi-dev
  source /opt/ros/noetic/setup.bash
  mkdir -p ~/catkin_ws/src
  cd ~/catkin_ws/src
  git clone https://github.com/yujinrobot/kobuki.git
  git clone https://github.com/yujinrobot/yujin_ocs.git
  git clone https://github.com/yujinrobot/kobuki_msgs.git
  git clone https://github.com/yujinrobot/kobuki_core.git
  cd yujin_ocs
  mkdir save
  mv yocs_cmd_vel_mux save
  mv yocs_controllers save
  mv yocs_velocity_smoother save
  rm -rf yocs*
  cd save
  mv * ..
  cd .. && rmdir save
  cd ~/catkin_ws/
  rosdep install --from-paths src --ignore-src -r -y
  catkin_make
  rosrun kobuki_ftdi create_udev_rules
  source ~/catkin_ws/devel/setup.bash
  roslaunch kobuki_node minimal.launch
  roslaunch kobuki_keyop keyop.launch
   
   
