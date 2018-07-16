# Autoware for autonomous vehicle

Software for urban autonomous driving, firstly developed by [Tier IV](http://www.tier4.jp) and then the package is customized for egg vehicle. The following functions are supported:

- 3D Localization
- 3D Mapping
- Path Planning
- Path Following
- Accel/Brake/Steering Control
- Data Logging
- Car/Pedestrian/Object Detection
- Traffic Signal Detection
- Traffic Light Recognition
- Lane Detection
- Object Tracking
- Sensor Calibration
- Sensor Fusion
- Cloud-oriented Maps
- Connected Automation
- Smartphone Navigation
- Software Simulation
- Virtual Reality

## Spec Recommendation

- Number of CPU cores: 8
- RAM size: 32GB
- Storage size: 30GB

## Requirements

- ROS indigo (Ubuntu 14.04) or ROS jade (Ubuntu 15.04) or ROS kinetic (Ubuntu 16.04)
- OpenCV 2.4.10 or higher
- Qt 5.2.1 or higher
- CUDA(Optional)
- FlyCapture2 (Optional)
- Armadillo (Optional)

### Install dependencies for Ubuntu 14.04 indigo

```
% sudo apt-get install ros-indigo-desktop-full ros-indigo-nmea-msgs ros-indigo-nmea-navsat-driver ros-indigo-sound-play ros-indigo-jsk-visualization ros-indigo-grid-map ros-indigo-gps-common
% sudo apt-get install ros-indigo-controller-manager ros-indigo-ros-control ros-indigo-ros-controllers ros-indigo-gazebo-ros-control ros-indigo-sicktoolbox ros-indigo-sicktoolbox-wrapper ros-indigo-joystick-drivers ros-indigo-novatel-span-driver
% sudo apt-get install libnlopt-dev freeglut3-dev qtbase5-dev libqt5opengl5-dev libssh2-1-dev libarmadillo-dev libpcap-dev gksu libgl1-mesa-dev libglew-dev
```

**NOTE: Please do not install ros-indigo-velodyne-pointcloud package. Please uninstall it if you already installed.**


**NOTE: Following packages are not supported in ROS Kinetic.**
- gazebo
- orb slam
- dpm ocv

## How to Build

```
$ cd $HOME
$ git clone https://github.com/CPFL/Autoware.git
$ cd ~/Autoware/ros/src
$ catkin_init_workspace
$ cd ../
$ ./catkin_make_release
```
###Caffe based object detectors
CV based detectors RCNN and SSD nodes are not automatically built.

To build these nodes please follow the respective node's README
[SSD](ros/src/computing/perception/detection/packages/cv_tracker/nodes/ssd/README.md)
[RCNN](ros/src/computing/perception/detection/lib/image/librcnn/README.md)
[Yolo2](ros/src/computing/perception/detection/packages/cv_tracker/nodes/yolo2/README.md)


## How to Start

```
$ cd $HOME/Autoware/ros
$ ./run
```

## How to use this for Egg Vehicle

please refer to the video (not available)

[![Public Road Demonstration](http://img.youtube.com/vi/5DaQBZvZwAI/mqdefault.jpg)](https://www.youtube.com/watch?v=5DaQBZvZwAI)

Steps:
- 1. Open the LiDAR driver in https://github.com/weisongwen/15_velodyne. if you have any questions about the connection between               the computer and the 3D LiDAR, you can refer to the https://github.com/weisongwen/15_velodyne.
- 2. connect the egg vehicle to the computer by run the launch file in /home/wenws/Autoware/ros/src/computing/perception/localization/packages/ivactuator/launch directory (change the directory as you may need) starup.launch, using the follwoing command.
```
$ roslaunch startup.launch
```
- 3. implemment the ndt_matching-based localization based on Autoware UI.
- 4. run the egg vehicle control node in the /home/wenws/Autoware/ros/src/computing/perception/localization/packages/ndt_localizer/nodes/ndt_matching using the following command.
```
$ python eggvehiclecontrol.py
```


## Research Papers for Citation

1. S. Kato, E. Takeuchi, Y. Ishiguro, Y. Ninomiya, K. Takeda, and T. Hamada. "An Open Approach to Autonomous Vehicles", IEEE Micro, Vol. 35, No. 6, pp. 60-69, 2015. [![Link](http://online.qmags.com/MIC1115/default.aspx?sessionID=7CF18C36BF00A40746B87387B&cid=3230522&eid=19656&pg=62&mode=2#pg62&mode2)](http://online.qmags.com/MIC1115/default.aspx?sessionID=7CF18C36BF00A40746B87387B&cid=3230522&eid=19656&pg=62&mode=2#pg62&mode2)

## Demo Videos

### Public Road Demonstration
[![Public Road Demonstration](http://img.youtube.com/vi/5DaQBZvZwAI/mqdefault.jpg)](https://www.youtube.com/watch?v=5DaQBZvZwAI)

## Instruction Videos

### Quick Start
[![Quick Start](http://img.youtube.com/vi/m-4U84K7lvg/mqdefault.jpg)](https://www.youtube.com/watch?v=m-4U84K7lvg)

### Loading Map Data
[![Loading Map Data](http://img.youtube.com/vi/EJa4PHnjdRY/mqdefault.jpg)](https://www.youtube.com/watch?v=EJa4PHnjdRY)

### Localization with GNSS
[![Localization with GNSS](http://img.youtube.com/vi/5bj7gkFlul0/mqdefault.jpg)](https://www.youtube.com/watch?v=5bj7gkFlul0)

### Localization without GNSS
[![Localization without GNSS](http://img.youtube.com/vi/ODlxMzGTJzw/mqdefault.jpg)](https://www.youtube.com/watch?v=ODlxMzGTJzw)

### Mapping
[![Mapping](http://img.youtube.com/vi/HlQ0ohxvlgA/mqdefault.jpg)](https://www.youtube.com/watch?v=HlQ0ohxvlgA)

### Detection with SSD
[![SSD](http://img.youtube.com/vi/EjamMJjkjBA/mqdefault.jpg)](https://youtu.be/EjamMJjkjBA)

### Detection with Yolo2
[![Yolo2](http://img.youtube.com/vi/gG_ojWOmDO0/mqdefault.jpg)](https://youtu.be/gG_ojWOmDO0)

### Detection with DPM
[![DPM](http://img.youtube.com/vi/P_BFQNbudlg/mqdefault.jpg)](https://youtu.be/P_BFQNbudlg)

### Detection with Euclidean Clustering
[![Clustering](http://img.youtube.com/vi/Tma2DKMxt4Y/mqdefault.jpg)](https://youtu.be/Tma2DKMxt4Y)

### Traffic Light Recognition
[![Traffic Light Recognition](http://img.youtube.com/vi/KmOdBms9r2w/mqdefault.jpg)](https://youtu.be/KmOdBms9r2w)

### Planning with ROSBAG
[![Planning with ROSBAG](http://img.youtube.com/vi/LZTCDbcjIdw/mqdefault.jpg)](https://www.youtube.com/watch?v=LZTCDbcjIdw)

### Planning with wf_simulator
[![Planning with wf_simulator](http://img.youtube.com/vi/HwB2NKqj2yg/mqdefault.jpg)](https://www.youtube.com/watch?v=HwB2NKqj2yg)

### Planning with Hybrid State A*
[![Planning with wf_simulator](http://img.youtube.com/vi/1WiqAHZHj8U/mqdefault.jpg)](https://www.youtube.com/watch?v=1WiqAHZHj8U)

### Calibration Toolkit
[![Calibration Toolkit](http://img.youtube.com/vi/pfBmfgHf6zg/mqdefault.jpg)](https://www.youtube.com/watch?v=pfBmfgHf6zg)

### Data Processor for Bag File
[![Data Processor](http://img.youtube.com/vi/M38Obmy-3Ko/mqdefault.jpg)](https://youtu.be/M38Obmy-3Ko)

### Ftrace
[![Ftrace](http://img.youtube.com/vi/RoIqKgerDUw/mqdefault.jpg)](https://youtu.be/RoIqKgerDUw)


