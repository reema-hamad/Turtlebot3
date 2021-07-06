# خطوات تثبيت الادوات من أجل المحاكاة لروبوت السلحفاة والتحكم فيه ورسم الخرائط 

.  ROS مثبتا بداخله VM قيد التشغيل مع ubuntu كما عملنا مسبقا بأستخدام 

:  نبدأ بكتابة الاوامر البرمجية  التالية   

1.  : ROS 1 نقوم بتثبيت 

 $ sudo apt-get update
 $ sudo apt-get upgrade
 $ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh
 $ chmod 755 ./install_ros_kinetic.sh 
 $ bash ./install_ros_kinetic.sh


1. : التابعة ROS 1 نقوم بتثبيت حزم 


 $ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy \
  ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc \
  ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan \
  ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python \
  ros-kinetic-rosserial-server ros-kinetic-rosserial-client \
  ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server \
  ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro \
  ros-kinetic-compressed-image-transport ros-kinetic-rqt* \
  ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers




1. TurtleBot3  نقوم بتثبيت حزم 

 $ sudo apt-get install ros-kinetic-dynamixel-sdk
 $ sudo apt-get install ros-kinetic-turtlebot3-msgs
 $ sudo apt-get install ros-kinetic-turtlebot3

1. أدخل هذه الرموز في الجهاز لتثبيت حزم المحاكاة

 * : نثبت المحاكاة 

 $ cd ~/catkin_ws/src/
 $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
 $ cd ~/catkin_ws && catkin_make


1. ​نقوم بفتح new terminal : 
  
*  اكتب هذا الأمر

 $ source ~/catkin_ws/devel/setup.bash

*  launch the simulation world هذا الامر لأجل : 

 $ export TURTLEBOT3_MODEL=burger
 $ roslaunch turtlebot3_gazebo turtlebot3_world.launch


.  ​نقوم بفتح new terminal : 

* launch the SLAM Node  هذا الامر لأجل 

"Run SLAM Node"

 $ export TURTLEBOT3_MODEL=burger
 $ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping



.  ​نقوم بفتح new terminal : 

*  : نقوم بتشغيل هذا الأمر لتتمكن من التفاعل والتحكم في الروبوت

Run Teleoperation Node

 $ export TURTLEBOT3_MODEL=burger
 $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

* الآن يمكنك البدء في رسم الخرائط
 terminal عن طريق 

![Untitled15](https://user-images.githubusercontent.com/85697922/124582239-8386bb00-de5a-11eb-80a7-7608c8cdc82b.png)


وهكذا سوف تصبح بعد التحكم 

![Untitled11](https://user-images.githubusercontent.com/85697922/124581707-00656500-de5a-11eb-9eff-6709d2dca799.png)
![Untitled12](https://user-images.githubusercontent.com/85697922/124581719-05c2af80-de5a-11eb-9276-6e8b3b1f2aab.png)
![Untitled13](https://user-images.githubusercontent.com/85697922/124581743-0c512700-de5a-11eb-961e-d154255cb85e.png)
![Untitled14](https://user-images.githubusercontent.com/85697922/124581762-1115db00-de5a-11eb-925e-e0e317dd5b17.png)

.  نقوم بفتح new terminal لحفظ الخريطة 

 $ rosrun map_server map_saver -f ~/map

ستجد الخريطة في المستندات وهنا صورة لخريطتي


![Untitled16](https://user-images.githubusercontent.com/85697922/124582544-c6489300-de5a-11eb-87b0-68f54a12129b.png)



*Have fun*


For more information go to https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/ .

