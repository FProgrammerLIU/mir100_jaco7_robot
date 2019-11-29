# mir100_jaco7_robot
Consists of MIR 100, Kinova jaco 7d3f, pan_tilt, Realsense D435i, Kinect V2, support. This repo contains bringup launch files, Mobile crawl demo, URDF description, navigation stack , moveit config, rviz display.  If you find a bug or missing feature in this software, please report it on the issue tracker.
## Package overview
- mir100_jaco7_app: Mobile craw demo
- mir100_jaco7_bringup: Bringup launch files
- mir100_jaco7_moveit_config: Moveit config
- mir100_jaco7_rviz: Rviz display
- mir100_jaco7_description:  URDF description
- mir_navigation: Navigation stack
## Source install
For a source install, run the commands below
```bash
# create a catkin workspace
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src/

# clone mir_robot into the catkin workspace
https://github.com/FProgrammerLIU/iqr_mir_jaco.git

# use rosdep to install all dependencies (including ROS itself)
sudo apt-get update
sudo apt-get install python-rosdep
sudo rosdep init
rosdep update
rosdep install --from-paths ./ -i -y --rosdistro kinetic

# build all packages in the catkin workspace
source /opt/ros/kinetic/setup.bash
cd ~/catkin_ws
catkin_make 
source ~/catkin_ws/devel/setup.bash
```
For realsence and Kinect V2 needs SDK.
## Navigation stack
```bash
# 启动
roslaunch mir100_jaco7_bringup mir100_jaco7_bringup
# 建图
roslaunch mir100_jaco7_navigation gmapping.launch
# 观察地图
roslaunch mir100_jaco7_rviz view_gmapping.launch
# 保存地图
rosrun map_server map_saver -f ~/...src/mir100_jaco7_navigation/map/map
# 启动导航
roslaunch mir100_jaco7_navigation navigation.launch
# 观察导航
roslaunch mir100_jaco7_rviz view_navigation.launch
```
## Moveit!
```bash
# 启动
roslaunch mir100_jaco7_bringup mir100_jaco7_bringup
# 启动Moveit！
roslaunch mir100_jaco7_moveit_config mir_jaco_moveit_excute.launch
```
## Mobile craw
```bash
# 启动机器人
roslaunch mir100_jaco7_bringup mir100_jaco7_bringup
# 启动导航
roslaunch mir100_jaco7_navigation navigation.launch
# 导航视图
roslaunch mir100_jaco7_rviz view_navigation.launch
# 启动Moveit！
roslaunch mir100_jaco7_moveit_config mir_jaco_moveit_excute.launch
# 启动移动抓取demo
roslaunch mir100_jaco7_app mir100_jaco7_app.launch
```
## Package links
aruco_ros: https://github.com/pal-robotics/aruco_ros
https://github.com/code-iai/iai_kinect2
https://github.com/QuartzYan/mir_robot
https://github.com/I-Quotient-Robotics/iqr_pan_tilt
