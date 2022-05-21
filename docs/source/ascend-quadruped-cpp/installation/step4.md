## Step 4: run the controller

You need not to login into subdirectories to launch exec file, instead input the commands

```bash
roslaunch unitree_gazebo normal.launch
```

to launch gazebo simulation env. Then in another new terminal, launch the controller node,

```bash
rosrun ascend_quadruped_cpp sim
```

Remember always run

```bash
source ./devel/setup.bash
```

before launch local ROS nodes.
