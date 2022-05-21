## Step 1: install the third party dependencies:

- Eigen3
- yaml-cpp
- lcm
- Quadprogpp
- ros

```bash
apt install libyaml-cpp-dev
apt install libeigen3-dev
apt install libglm-dev
git clone https://gitee.com/zhulinsen1/robots.git ./robots
cd ${ROBOTS_DIR}/src/ascend-quadruped-cpp/third_party/lcm-1.4.0
mkdir build && cd build
cmake .. && make && sudo make install 
```
install ros, related ros packages and gazebo

After that, to install ros-gazebo packages, run the following command

`sudo apt update && apt install ros-{version_name}-catkin ros-{version_name}-gazebo* `