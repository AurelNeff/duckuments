# Demo Saviors {#demo-saviors status=beta}

This is the description of the saviors obstacle avoidance demo.

<div class='requirements' markdown="1">

Requires: Duckiebot in configuration DB17-wjd.

Requires: [Camera calibration](#camera-calib) completed. 

Requires: [Wheel calibration](#wheel-calibration) completed. 

Requires: [Joystick demo](#rc-control) successfully launched. 

</div>

## Video of expected results {#demo-saviors-expected}

Video will be added when framework is defined/provided. The duckiebot should stop if an obstacle (duckie or cone) is placed in front of the duckiebot. 

## Duckietown setup notes {#demo-saviors-duckietown-setup}

Duckietown built to specifications. No special requirements like april-tags, traffic lights or similar needed.

To demonstrate functionality, place obstacles (duckies S/M/L or cones) on driving lane. Best performance is achieved when obstacles are placed on the straights, not immediately after a curve.

## Duckiebot setup notes {#demo-saviors-duckiebot-setup}

Currently the bot has to be on the devel-saviors-jan15 branch on git. Furthermore the additional package sk-image has to be installed (`sudo apt-get install python-skimage`)

## Pre-flight checklist {#demo-saviors-pre-flight}

Check: Joystick is turned on

Check: Sufficient battery charge on duckiebot 

## Demo instructions {#demo-saviors-run}

Step by step instructions to run demo:

Step 1: On the duckiebot, navigate to `DUCKIETOWN_ROOT` and run 

    duckiebot $ source environment.sh

    duckiebot $ catkin_make -C catkin_ws/

    duckiebot $ make demo-lane-following

Wait for a couple of seconds until everything has been properly launched.

Step 2: In a second terminal on the duckiebot, run: 

    duckiebot $ roslaunch obst_avoid obst_avoid_lane_follow_light.launch veh:=robot_name

This launches the obstacle avoidance node, wait again until it's properly started up. 

Step 3: Press the X button on the joystick to generate an anti-instagram transformation. Repeat if needed until confirmation message is shown in the `obst_avoid` window (Confirmation message: "!!!!!!!!!!!!!!!!!!!!TRAFO WAS COMPUTED SO WE ARE READY TO GO!!!!!!!!!!!!" in YELLOW letters).

Step 4: To visualise output of the nodes run the following commands on your notebook:

    laptop $ source set_ros_master.sh robot_name

    laptop $ roslaunch obst_avoid obst_avoid_visual.launch veh:=robot_name

    laptop $ rviz

Topics of interest are: `/robot_name/obst_detect_visual/visualize_obstacles` (Markers which show obstacles), `/robot_name/obst_detect_visual/image/compressed` (Image with obstacle detection overlay), `/robot_name/obst_detect_visual/bb_linelist` (bounding box of obstacle detection), `/robot_name/duckiebot_visualizer/segment_list_markers` (line segments). Add more individual topics if needed.

Step 5: To drive press R1 to start lane following. Duckiebot stops if obstacle detected and in reach of the duckiebot. Removal of the obstacle should lead to continuation of lane following.  


## Troubleshooting {#demo-saviors-troubleshooting}

P: Objects aren't properly detected, random stops on track. 

S: Make sure that anti instagram was run properly. Repeat Step 3 if needed. 

P: Duckiebot crashes obstacles. 

S: Might be due to processes not running fast enough. Check if CPU load is too high, reduce if needed. 

## Demo failure demonstration {#demo-saviors-failure}

Video will be added when framework is defined/provided.
