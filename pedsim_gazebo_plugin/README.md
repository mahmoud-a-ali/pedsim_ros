# pedsim_gazebo_plugin package

This package integrates the Pedestrian Simulator pedsim_simulator into Gazebo.

### Features
- it converts pedsim scenarios to gazebo worlds 
- it spawns pedsim agents into gazebo  
- it continously updates the poses of the spawned agents

### Sample usage
#### Step 1. Generate gazebo world + launch file for the `social_contexts.xml` scenario
====
```
$ rosrun pedsim_gazebo_plugin pedsim_to_gazbo_world.py 
```
This script will ask you to enter the name of the scenario you want to convert to gazebo world (in this case it is `social_contexts.xml`). NOte that the scenario_file should be stored in the `pedsim_simulator/scenarios/` directory,
```
social_contexts.xml
```

#### Step 2. in one terminal run the `social_contexts.xml` scenario in pedsim simulator using the `airport_activities.launch`
```
$ roslaunch pedsim_simulator simple_ped.launch
```

#### Step 3. in another terminal run the launch file generated from step 1 `social_contexts.launch` 
```
$ roslaunch pedsim_gazebo_plugin simple_pedestrians.launch
```

#### Step 4. To synchronize your own robot with the diff_robot that is included in the pedsim package: 
##### 1. Spawn your own robot (diff_drive_robot), consider the same coordinates in the scenario file.
##### 2. Remap `/pedbot/control/cmd_vel` to the topic you are using to control your own robot 

