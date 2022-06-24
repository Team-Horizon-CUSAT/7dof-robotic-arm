# 7dof-robotic-arm
## install and run 
1. start the roscore
   ```console
    roscore
   ```
2. create your own package in your current working cmake workspace
   ```console
   catkin_create_pkg your_package_name roscpp tf geometry_msgs urdf rviz xacro
   ```
3. install the urdf and xacro packages 
   ```console
   sudo apt-get install ros-melodic-urdf
   sudo apt-get install ros-melodic-xacro
   ```
4. Enable the ros to find the path of package , executables and custom files by sourcing it 
   ```console
   source devel/setup.bash
   ```
5. clone the files in this repo to your package folder that you just created
6. delete unnecessary files , that include
  * cd to your urdf folder
    * seven_dof_arm.gv
    * seven_dof_arm.pdf
    * seven_dof_arm.urdf
   _etc_
7. cd to your launch folder and change the following line of code in view_arm.launch file, according to your package name that u just created
   ```launch
   <param name="robot_description" command="$(find xacro)/xacro --inorder $(find your_package_name)/urdf/seven_dof_arm.xacro" />
   .................
   .................
   .................
   <node name="rviz" pkg="rviz" type="rviz" args="-d $(find mastering_ros_robot_description_pkg)/urdf.rviz" required="true" />
   ```
8. cd to urdf folder and change following line of code in seven_dof_arm.xacro
   ```xacro
     <xacro:include filename="$(find your_package_name)/urdf/sensors/xtion_pro_live.urdf.xacro"/>
   ```
9. convert the xacro files to urdf files
   ```console
   rosrun xacro xacro seven_dof_arm.xacro --inorder > seven_dof_arm.urdf
   ```
10. check for errors in urdf (_optional steps_)(_familirizig the some useful commands_)
   ```console
   check_urdf seven_dof_arm.urdf
  ```
11. visualizing urdf in graph and joint format (_optional steps_)(_familirizig the some useful commands_)
   ```console
    urdf_to_graphiz seven_dof_arm.urdf
   ```
   To view the pdf 
   ```console
   envince seven_dof_arm.pdf
   ```
   _when converting to graph and joint format .gv and .pdf files will be automatically create_
   
12. launch the rviz and start the node in one go using the launch file that we created
   ```console
   roslaunch your_package_name view_arm.launch
   ```
   # Boom there u go 
## possible and inevitable errors 
1. package folder and files not found
  ```error
   xacro: in-order processing became default in ROS Melodic. You can drop the option.
   resource not found: mastering_ros_robot_description_pkg
   ROS path [0]=/opt/ros/melodic/share/ros
   ROS path [1]=/opt/ros/melodic/share
  ```
_solution_
  source the package , whenever necesarry
  ```console
  source devel/setup.bash
  ```
2. cannot view the robot
  [image](http://52.172.92.114/files/Screenshot%20from%202022-06-24%2022-59-37.png)
