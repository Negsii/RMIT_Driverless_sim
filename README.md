# RMIT Driverless Simulator.  
  
Based apon CAT vehicle, see below for details.  
To use as is of 26/8/2020,  
1: install cat vehicle sim as below  
2: download this repository onto your desktop  
3: Open files in ubuntuand use the command (CTRL+H) to see hidden folders.   
4. Navigate to ~/Home/.gazebo/models/  
5: Open a new tab in files (CTRL+T) and navigate to the dowloaded repository  
6: In the tracks folder, copy all folders (acceleration, big_track, skidpad, small_track)  
7. Paste these in ~/Home/.gazebo/models/  
8: now copy the 'urdf', 'worlds', 'meshes' and 'launch' folders from the downloaded depository  
9: paste them in 'your_workspace'/src/catvehicle and overwrite the folders that are named identicly, you may need to delete them first  
10: you should be good to launch them now  

# Launching and running model with gazebo:  
1: Open a terminal and run, $ roscore  
2: In a new terminal window or tab (CTRL+shift+t) run $ roslaunch catvehicle catvehicle_big_track.launch  
2a: other tracks include,                             $ roslaunch catvehicle catvehicle_small_track.launch  
                                                      $ roslaunch catvehicle catvehicle_skidpad.launch  
                                                      $ roslaunch catvehicle catvehicle_acceleration.launch  
3: In a new terminal run $ gzclient  
4: This will open gazebo, click on gazebo and the model should be in the enviroment you launched  
# optional   
5: To move the vehicle open a new terminal and run $ rosrun telop_twist_keyboard telop_twist_keyboard.py /cmd_vel:=/catvehicle/cmd_vel  
5a: This window must be open and currently clicked on to recieve keystrokes. speed is very slow to begin so hold q to increase speed.  
6: To view cameras and lidar data and to visualise it use $ rosrun rviz rviz   
6a: In rvis set Fixed Frame to catvehicle/odom, and use add to add lidar or cameras from topic menu. To add the robot use add and select RobotModel from 'By Display Type'. Then change Robot Description to catvehicle/robot_description and TF Prefix to catvehicle  
  

# Cognitive and Autonomous Test Vehicle (CAT Vehicle) Testbed
The CAT Vehicle is a ROS based simulator to facilitate the development of autonomous vehicle applications. This repository houses the files that utilize the Gazebo simulator, and additional interfaces to the physical CAT Vehicle Testbed available at the University of Arizona - Department of Electrical and Computer Engineering.

# Dependencies
* ROS
* [obstaclestopper](https://github.com/jmscslgroup/obstaclestopper)
* [control_toolbox](https://github.com/jmscslgroup/control_toolbox)
* [sicktoolbox](https://github.com/jmscslgroup/sicktoolbox)
* [sicktoolbox_wrapper](https://github.com/jmscslgroup/sicktoolbox_wrapper)
* [stepvel](https://github.com/jmscslgroup/stepvel)
* [cmdvel2gazebo](https://github.com/jmscslgroup/cmdvel2gazebo)
* Controller manager (allows the car to move around with ROS messages)
```shell
  sudo apt-get install ros-melodic-controller-manager
  sudo apt-get install ros-melodic-ros-control ros-melodic-ros-controllers
  sudo apt-get install ros-melodic-gazebo-ros-control
  ```

# System Requirements
* Ubuntu 18.04 LTS (We cannot guarantee if it works on any other version of Ubuntu)
* RAM: 4GB required, > 8GB recommended.


# Citing this work
If you find this work useful please give credits to the authors and developers by citing:
```json
Rahul Bhadani, Jonathan Sprinkle, Matthew Bunting. "The CAT Vehicle Testbed: 
A Simulator with Hardware in the Loop for Autonomous Vehicle Applications". 
Proceedings 2nd International Workshop on Safe Control of Autonomous Vehicles (SCAV 2018),
Porto, Portugal, 10th April 2018, Electronic Proceedings in Theoretical Computer Science 269,
pp. 32–47.  Download:  http://dx.doi.org/10.4204/EPTCS.269.4.
```

bibtex:
```
@article{bhadani2018cat,
  title={{The CAT Vehicle Testbed: A Simulator with Hardware 
  in the Loop for Autonomous Vehicle Applications}},
  author={Bhadani, Rahul and Sprinkle, Jonathan and Bunting, Matthew},
  journal={{Proceedings of 2nd International Workshop on Safe Control of Autonomous Vehicles
  (SCAV 2018), Porto, Portugal, 10th April 2018, Electronic Proceedings
  in Theoretical Computer Science 269, pp. 32–47}},
year={2018}
}
```

# What's new
* Released for Ubuntu 18.04 LTS, ROS Melodic and Gazebo 9.0
* Support for front camera
* More stable vehicle dynamics
* Bug fixes and improvements

# How to use it

## Installing ROS
* Follow the steps mentioned in the [ROS wiki page](http://wiki.ros.org/melodic/Installation/Ubuntu%C2%A0) on how to install ROS Melodic. 
* In addition to that we are required to install some additional ros packages
```shell
sudo apt-get install ros-melodic-velodyne ros-melodic-novatel-span-driver
```

## Creating catkin workspace
In order to use the catvehicle ROS package, you should work within a catkin workspace. If you do not already have one:
```shell
cd ~
mkdir -p catvehicle_ws/src
cd catvehicle_ws/src
catkin_init_workspace
cd ..
catkin_make
```

At this point, you can extract this release package from [catvehicle-3.0.1](https://github.com/jmscslgroup/catvehicle/releases/download/3.0.1/catvehicle-3.0.1.tar.xz) and other dependent package into your src directory
```shell
cd ~/catvehicle_ws/src
git clone https://github.com/jmscslgroup/catvehicle
git clone https://github.com/jmscslgroup/obstaclestopper
git clone https://github.com/jmscslgroup/control_toolbox
git clone https://github.com/jmscslgroup/sicktoolbox
git clone https://github.com/jmscslgroup/sicktoolbox_wrapper
git clone https://github.com/jmscslgroup/stepvel
git clone https://github.com/jmscslgroup/cmdvel2gazebo
cd ..
catkin_make
```
## Sourcing workspace to the environment path
```bash
echo "source ~/catvehicle_ws/devel/setup.bash" >> ~/.bashrc
```

# Simple tutorial and examples
Follow the tutorials on the CAT Vehicle Testbed group on the [CPS Virtual Organization](https://cps-vo.org/group/CATVehicleTestbed) to see how to use the testbed.

# Issues
If you run into a problem, please feel free to post to [issues](https://github.com/jmscslgroup/catvehicle/issues). If the issue is urgent, please email to catvehicle@list.arizona.edu.

# Acknowledgements
## License
Copyright (c) 2013-2020 Arizona Board of Regents; The University of Arizona
All rights reserved

Permission is hereby granted, without written agreement and without 
license or royalty fees, to use, copy, modify, and distribute this
software and its documentation for any purpose, provided that the 
above copyright notice and the following two paragraphs appear in 
all copies of this software.
 
IN NO EVENT SHALL THE ARIZONA BOARD OF REGENTS BE LIABLE TO ANY PARTY 
FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES 
ARISING OUT OF THE USE OF THIS SOFTWARE AND ITS DOCUMENTATION, EVEN 
IF THE ARIZONA BOARD OF REGENTS HAS BEEN ADVISED OF THE POSSIBILITY OF 
SUCH DAMAGE.

THE ARIZONA BOARD OF REGENTS SPECIFICALLY DISCLAIMS ANY WARRANTIES, 
INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY 
AND FITNESS FOR A PARTICULAR PURPOSE. THE SOFTWARE PROVIDED HEREUNDER
IS ON AN "AS IS" BASIS, AND THE ARIZONA BOARD OF REGENTS HAS NO OBLIGATION
TO PROVIDE MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR MODIFICATIONS.

## Authors and contributors
* Jonathan Sprinkle (sprinkjm@email.arizona.edu)
* Rahul Bhadani (rahulbhadani@email.arizona.edu)
* Sam Taylor
* Kennon McKeever (kennondmckeever@email.arizona.edu)
* Alex Warren
* Swati Munjal (smunjal@email.arizona.edu)
* Ashley Kang (askang@email.arizona.edu)
* Matt Bunting (mosfet@email.arizona.edu)
* Sean Whitsitt

## Support
This work was supported by the National Science Foundation and AFOSR under awards 1659428, 1521617, 1446435, 1262960 and 1253334. Any opinions, findings, and conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the National Science Foundation.

#RMIT_Driverless_sim
