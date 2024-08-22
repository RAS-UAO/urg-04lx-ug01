# Guide for using URG-04LX-UG01 in ROS2


# Guide for using URG-04LX-UG01 in ROS2

In this repository, a step-by-step guide for using URG-04LX-UG01 in ROS2 Humble is presented

![image](https://github.com/user-attachments/assets/47dd4c0c-76fb-4f94-9774-301d2dc7c735)

# Phase 1: Hardware integration

The URG-04LX-UG01's connection is pretty simple. It's just a serial-type, just like a USB memory

![Hardware](https://github.com/user-attachments/assets/40e6ff9d-b54a-44a2-9181-e4f7b55c84d5)

See? Nothing complicated about it

# Phase 2: Software commands
**Step 1:** You need to install all the respectives packages:

    sudo apt install ros-humble-urg-node*
    sudo apt install ros-humble-rviz*

**Step 2:** Once, you've installed the URG-04LX-UG01's package. Then, you can connect it as described in the *hardware integration* sections. After that, you can check if you URG-04LX-UG01's connected by typing the following command line:

    ls -l /dev/ttyACM0

If you LiDAR is connected, then you should see something similar to this in your screen:

    crw-rw-rw- 1 root dialout 166, 0 Aug 13 19:24 /dev/ttyACM0

**Step 3:** You need to enable your URG-04LX-UG01's serial port so it can be used for your purposes. You can do that by typing:

    sudo chmod a+rw /dev/ttyACM0

**Step 4:** Ok! Now you can run your LiDAR in ROS2 by typing: 

    ros2 run urg_node urg_node_driver --ros-args --params-file /opt/ros/humble/share/urg_node/launch/urg_node_serial.yaml

**Step 4:** The LiDAR is now running, but you're not visualizing its information. To visualize it in RViz, you must type the following in *another* terminal:

    rviz2

**Step 5:** You need to make a couple of changes:

 - You must put *laser* in Fixed Frame. This is usually any LiDAR's frame.

<img width="568" alt="Fixed Frame" src="https://github.com/user-attachments/assets/c631e5d5-4374-4d8f-bff0-9353623c2287">
 
 - You must add /scan topic. It must have the *LaserScan* message, which the message that broadcast LiDAR's sensing.
 - 
![Topic](https://github.com/user-attachments/assets/b78e4089-cfc0-4e8b-aac0-1fa20d38281d)

**Step 6:** Now, you must see something like this:

![Final](https://github.com/user-attachments/assets/43c707a7-7acf-4562-97e6-052e4f4bfd69)

**Congratulations!** You just run and visualized the URG-04LX-UG01's sensing.
