# ROS noetic
To manipulate the turtlesim package in ROS Noetic, follow these steps:
### 1. Install the Turtlesim Package

```
sudo apt install ros-noetic-turtlesim
```
### 2. Start the ROS Master
Open a terminal:

```
roscore
```
### 3. Launch Turtlesim
In a new terminal:

```
rosrun turtlesim turtlesim_node
```
### 4. Control the Turtle
Open another terminal and run:

```
rosrun turtlesim turtle_teleop_key
```

Use arrow keys to move the turtle.

### 5.	Programmatically Control the Turtle (Optional):
•	Create and edit move_turtle.py:

```
#!/usr/bin/env python
import rospy
from geometry_msgs.msg import Twist

def move_turtle():
    rospy.init_node('move_turtle', anonymous=True)
    pub = rospy.Publisher('/turtle1/cmd_vel', Twist, queue_size=10)
    rate = rospy.Rate(10)
    move_cmd = Twist()
    move_cmd.linear.x = 2.0
    move_cmd.angular.z = 1.0

    while not rospy.is_shutdown():
        pub.publish(move_cmd)
        rate.sleep()

if __name__ == '__main__':
    try:
        move_turtle()
    except rospy.ROSInterruptException:
        pass
```

•	Run the script:

```
python move_turtle.py
```

### Now you're ready to control the turtle in the turtlesim package by controlling the turtle either through keyboard commands or programmatically using a custom Python script.





