# turtlebot-autonomus-persepsi
Tugas akhir mata kuliah Persepsi Robot

**NOTE**
The first thing is that you need to make sure that ROS that is installed is the Noetic version.

## Autonomus Drive
The first step is that you need to launch your Roscore first on a remote PC.
```
$ roscore
```
Next, you need to bring up the turtlebot with this command (for example, I used Burger Model) :
```
$ ssh ubuntu@{IP_ADDRESS_OF_RASPBERRY_PI}
$ export TURTLEBOT3_MODEL=${burger}
$ roslaunch turtlebot3_bringup turtlebot3_robot.launch
```

The next step is to launch the Navigation and create a map :
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```
**NOTE** The map file directory is not always the same for everyone, so make sure the directory or path is right.

In order to create a map, you need to do teleop first. In the beginning, the turtlebot cannot drive itself because it doesn't know the environment around it :
```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
### Run the navigation
In RViz, you just need to select "2D Nav Goal" to tell the robot where they should go. If the mapping is correct, they will move perfectly and avoid all obstacles.

![Demo](https://github.com/mananispiwpiw/turtlebot-autonomus-persepsi/blob/main/ezgif.com-video-to-gif.gif)


##Line Detection (Only Calibration)
###Camera Imaging Calibration
In this step, we want to check the camera to see if it is properly connected to Turtlebot or not. 
On a remote PC, we can launch a command like this: 
```
$ roscore
```
On Turtlebot, the command is like this:
```
$ roslaunch turtlebot3_autorace_camera raspberry_pi_camera_publish.launch
```
And last, open a new terminal on the remote PC and run this command:
```
$ rqt_image_view
```

![Camera From Turtlebot]()

###Camera Extrinsic Calibration
Next is extrinsic camera calibration, before we calibrate it. I want to show you the camera view or result before the calibration.

![Before Calibration]()



