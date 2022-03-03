HOW TO RUN: please use $roslaunch wall_follower wall_follower.launch

This will launch all three of the nodes correctly if they are marked as executable.

scan_value_handler.py reads from the lidar data and filters the values to be within the maximum or minimum perceptible distance. 
It then uses the minimum value to determine the distance of the nearest wall and the angle of the wall relative to the robot. It uses this information
to determine the state of the robot and sends that information to PID.py. 
 PID.py has two states for the proportion component. In one state, the robot sees a wall ahead and gradually turns towards the wall. If the robot overshoots the distance, 
 it turns away from the wall. If the robot is following the wall, the proportion component is the value time -1. 
 If the robot is too close to the wall, this pushes the robot away from the wall, and if the robot is too far from the wall, 
 this pushes the robot towards the wall. This PID assumes that derivative component is related to the desired angle for the robot relative to wall. 
 In this case, the robot wants to be 270 degrees relative to the wall. This value is divided by that angle, to normalize
 the value from becoming too large. The integral component is assumed to be the sum of the previous ten values of the calculated error. # wall_follower
