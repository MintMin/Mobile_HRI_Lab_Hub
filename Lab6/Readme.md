# Choreographing Movement
**List the names and NetID for your partners here.**

Qianti Min qm45  
Ananya Ganesh ag2227  
Calvin Tirrell cat248  
Jonah Brucker-Cohen jb2662  

It is about time to have a functioning mobile robot! Starting from this lab, you should prioritize either robot building and/or study design. 

## Prep
### Watch the following tutorials:
- [How to crimp wires](https://www.youtube.com/watch?v=SaU00MMjzn0&ab_channel=GrizzlyBuilds)

- [Beginner's Guide on Soldering](https://www.makerspaces.com/how-to-solder/)


- [How to Solder Wires Together](https://youtu.be/NSqPHQ1zQco)



### For this lab, you will need:
1. Your laptop
2. Cardboard
3. Utility knife
4. Your hoverboard base

### Deliverables for this lab are: 

0. Photos of your robot prototype
1. A video of your robot moving around
2. A sketch of a series movements based on your final project
3. A video showing your robot perform the movements in item #2.
4. Reflect upon your design, what would you do differently?


## Lab Overview
For this assignment, you are going to:

A) [Build your chassis](#part-a-build-your-chassis)

B) [Move it around](#part-b-move-it-around)

C) [Plan a movement](#part-c-plan-a-movement)

D) [Optional Spinning your LiDAR](#part-d-optional-spinning-your-LiDAR)

Labs are due on Tuesdays before class. Make sure this page is linked to on your main class hub page.

## Part A. Build your chassis
If you haven't already, now is a good time to actually mockup a low fidelity version robot for your final project. At least, you should have a chassis that safely host all the hardware you have (ODrive, wheels, battery, etc).

Feel free to use any material we have in lab to build your chassis. Things you might find useful are cardboard, gluegun, zip ties, duo locks, etc. 

## Part B. Move it around
Once you build your chassis, test it out! Power on your hoverboard and connect your controller. Drive your robot around! (Take a video while you do that!)

A few questions to consider:
- when your robot accelerate, is the chassis stable?
- what are all the possible motions (action space) your robot can perform? (e.g. rotating in place, moving foward/backward, ...)
- reflect on your design and think what would you do differently next time.

## Part C. Plan a movement
Based on your scenario, sketch out a sequence of movement in a storyboard format. 
Then, control your robot to execute that sequence of movement. (Take a video while you do that!)


## Part D. Optional spinning your LiDAR
If you plan to use LiDAR for your final project, or are simply curious about how it works, let's set it up!

```
# Install LiDAR SDK
# In your RPi terminal
sudo apt install cmake pkg-config
cd ~
git clone https://github.com/YDLIDAR/YDLidar-SDK.git
cd YDLidar-SDK
mkdir build
cd build
cmake ..
make
sudo make install
```

```
cd ~/mobilehri_ws/src/mobilehri2023
git checkout ydlidar_ros2_driver
cd ~/mobilehri_ws
colcon build

chmod 0777 src/ydlidar_ros2_driver/startup/*
sudo sh src/ydlidar_ros2_driver/startup/initenv.sh

```
Now, plug in your LiDAR.
```
# start your LiDAR
source install setup.bash
ros2 launch ydlidar_ros2_driver ydlidar_launch.py 
```

To visualize your LiDAR reading, open foxglove studio in vnc viewer. Then, click 3D in the left panel.

### Again, deliverables for this lab are: 

0. Photos of your robot prototype
![IMG_7167](https://user-images.githubusercontent.com/32082801/228095578-57850414-2ceb-42fc-a55d-baf02e22b0be.jpg)

1. A video of your robot moving around
- Testing the wheels
https://user-images.githubusercontent.com/32082801/226505437-4e8230b8-80cf-4834-b684-75c1d82c4f59.mov

- First move!
https://user-images.githubusercontent.com/32082801/226505496-6fe093a8-2a9b-4baf-af24-3bf3b572505d.MOV

- Moving....
https://drive.google.com/file/d/17W5t3W3yKhHHLK-1u9SKWv86DSj87ncm/view?usp=sharing


2. A sketch of a series movements based on your final project
![IMG_7168](https://user-images.githubusercontent.com/32082801/228095588-ca0de6c3-1c0d-44b5-ab9a-d51a15660a81.jpg)
![IMG_7169](https://user-images.githubusercontent.com/32082801/228095592-02c4412a-ffb9-40ad-9b3d-86320fa53191.jpg)

3. A video showing your robot perform the movements in 2.
Please see the videos in the end (when we build a sturdier body with extra wheels)

4. Reflect upon your design, what would you do differently?
- Build a sturdier body for the electronics
  - Try foam
  - Try wood
- Modify the velocity of the wheels, so the initial velocity could be smoother. The initial jolt causes the cardboard body to flip and move unexpectedly. This is not sturdy enough for the electronics. 

### Improvement:
We added two more wheels to make the robot move in a more balanced way.
![IMG_6954](https://user-images.githubusercontent.com/32082801/228096482-679a6eca-e6e0-4eaa-aa5f-f4393f7bc7d2.JPG)

It worked very well!
Here is the video of robot dancing around, as drew in the sketch:
https://drive.google.com/file/d/1Ko9Zt-yNPlVsPmMmM11UK6opU5ULNM9U/view?usp=sharing








https://user-images.githubusercontent.com/32082801/228096528-00719361-436a-4575-8062-af81ca9f61fe.MOV

