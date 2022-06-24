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
