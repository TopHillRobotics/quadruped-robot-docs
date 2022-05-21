## Step 3: compile the exectuable locomotion controller or other ros packages

```bash
cd ${ROBOTS_DIR}/src/ascend-quadruped-cpp/
mkdir build && cd build
cmake .. && make
```

or in ROS env (recommended),

```bash
cd ${ROBOTS_DIR}
catkin_make
```

Currently, the locomotion controller support Velocity Mode(normal trot), Position Mode(for walk through gaps), Walk Mode(static walk) and Advanced-trot Mode(for climb up stairs), among which you can browse through `src/ascend-quadruped-cpp/config` directory to select corresponding configuration.
