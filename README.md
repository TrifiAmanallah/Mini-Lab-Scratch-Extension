# Mini-Lab-Scratch-Extension
Scource code of the Minilab's Sratch Extension.
Developped by Amanallah Trifi (T.amanallah1992@gmail.com)
for Enova Robotics (www.enovarobotics.eu/)
#Using ScratchX :
Scratch is a programming language and online community where you can create your own interactive stories, games, and animations. ScratchX is a separate experimental platform built to test experimental Scratch features, also known as Experimental Extensions. There is no login or community component to ScratchX, and projects created within ScratchX can only be run on ScratchX.
ScratchX is a platform that enables people to test experimental functionality built by developers for the visual programming language Scratch.
The ScratchX interface is very similar to the Scratch 2.0 interface with the exception of a set of features for #loading Experimental Extensions.
#Load the Mini-Lab's Sratch Extension: 
To load the minilab's extension just copy and paste this adress to your favorit browser's adress bar:
http://scratchx.org/?url=https://rawgit.com/TrifiAmanallah/Mini-Lab-Scratch-Extension/master/Minilab_Scratch.js
Or you can do it manually:
 1-go to : http://scratchx.org/
 2-click on " Open Extension URL "
 3-past the link:https://rawgit.com/TrifiAmanallah/Mini-Lab-Scratch-Extension/master/Minilab_Scratch.js
 4-In the popup dialog box click "I understand, continue"
 That's it!
 #Using the minilab's sratch extension:
 This tutorial will show how to use the Mini-Lab's scratch Extension with the Gazebo simulator. Thus to use the extension with the Minilab Robot, you can just follow the same instructions.
 ## Connect to the Robot/Gazebo:
The extension uses  the ROS JavaScript Library (roslibjs) witch is the core JavaScript library for interacting with ROS from the browser. It uses WebSockets to connect with rosbridge and provides publishing, subscribing, service calls, actionlib, TF, URDF parsing, and other essential ROS functionality.
So to be able to use the extension you need to have the rosbridge_server package installed on your Robot or your   Gazebo's host Computer, you can learn how to do that here:
http://wiki.ros.org/rosbridge_server
Then you need to launch The rosbridge server using the following command:
roslaunch rosbridge_server rosbridge_websocket.launch
Once this is done, you can use the connection Block to start the connection with the robot/gazebo:
(the block takes two parameters the host adress and the communication port, the full adress would be
ws://adress:port) 

In case of problems you can view the Log messages using the JavaScript Console 
(To start the console on Google chrome: ctrl+maj+j )
The extension also provide a Hat block that return true if the connection is succefully established:

N.B: Most of the extension's blocks wont be able to work unless the connection is succefully established.
Also dont forget to start the roscore node and the Minilab's gazebo simulation
(further information on how to do this: http://wiki.ros.org/Mini-Lab/Tutorials )
##Moving the Robot:
After starting the Connection, we can start Moving the robot using these blocks:
(the block takes two parametres one for the direction and one for the speed, the command would be something like this NewPosition=OldPosition+speed)

You can find a keyboard Teleop example on the following link:

##Reading the robot position:
The extension provide differents reporter block to allow reading of the robot's position and orientation on a 3d coordinates system.All values are in meters. 

##Reading Values from the laser sensor:
The extension provide all tools needed to use the laser sensor of the minilab Robot. These tools are a set of reporters blocks that allow access to these vales:
*start/end angle of the scan [rad]
*angular distance between measurements [rad]
*time between measurements [seconds]
*time between scans [seconds]
*minimum/maximum range value [m]
*Finally the range of a specied angle [m]

These blocks could be used for diffrents applications like obstacle avoidance,map scaning,...
##Streaming live video from Minilab/Gazebo:
The extension provide a block that can stream live video on a new popup window.This block uses the web_video_server package wich should be installed on your robot or your Gazebo's host computer. Instructions could be found here:
http://wiki.ros.org/web_video_server
Then you have to start the web video server using this command:
rosrun web_video_server web_video_server
Once this is done you can use the block after specifing the adress of the host and the communication port.

There is also a block to set the video parametres width,height and quality (1-100).This block must be executed befor the streaming block.

After the execution of the two blocks the full adress to video would be something like that: 
http://'adress':'port'/stream_viewer?topic=/camera/rgb/image_raw&width='specified_width'&height='specified_height'&quality='specified_quality'
##Streaming Map Scaning from Minilab/gazebo:
The extension provide a block that can stream real time map scaning with a visualisation of the robot's position.
To be able to use this block you need first to run these commands on your robot or your gazebo's host computer:
$ roslaunch minilab_description minilab_state_publisher.launch
$ roslaunch minilab_navigation gmapping.launch
(Further information could be found here: http://wiki.ros.org/Mini-Lab/Tutorials/Laser_mapping)
After specifing the adress and port wich by the way are the same parametres of the connection block, a popup window should appear containing a visulisation of the robot's posion and the map scaning process.

There is also a block to set the map parametres width,height and refresh rate (sec).This block must be executed befor the Map streaming block.

N.B There might be some Javascript related issues with the refresh function of the map's popup window , so you might need to refresh the Map streaming block manually in order to view the real time advancement of the scaning process. 


  
 
 
 
 
 
