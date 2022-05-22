Installation
=============

Step 1: install the third party dependencies:
-------------------------------------------------------------------------

- Eigen3
- yaml-cpp
- lcm
- Quadprogpp
- ros

.. code-block:: console

    apt install libyaml-cpp-dev
    apt install libeigen3-dev
    apt install libglm-dev
    git clone https://gitee.com/zhulinsen1/robots.git ./robots
    cd ${ROBOTS_DIR}/src/ascend-quadruped-cpp/third_party/lcm-1.4.0
    mkdir build && cd build
    cmake .. && make && sudo make install 

install ros, related ros packages and gazebo

After that, to install ros-gazebo packages, run the following command

``sudo apt update && apt install ros-{version_name}-catkin ros-{version_name}-gazebo*``

Step2: edit compile option
----------------------------------------------------------------

open the ``CMakeLists.txt`` file in ``ascend-quadruped-cpp`` folder, check the compile options so as to match the hardware and applications. In particular, when compiling unitree_legged_skd, the binary ``.so`` file should be ``*amd64.so`` in ``./lib/`` subdirectory, according to current X86/AMD64 platform. If you do not want to compile test examples, please disable ``ENABLE_TEST``.

Step 3: compile the exectuable locomotion controller or other ros packages
-------------------------------------------------------------------------------

.. code-block:: console

    cd ${ROBOTS_DIR}/src/ascend-quadruped-cpp/
    mkdir build && cd build
    cmake .. && make

or in ROS env (recommended),

.. code-block:: console

    cd ${ROBOTS_DIR}
    catkin_make

Currently, the locomotion controller support Velocity Mode(normal trot), Position Mode(for walk through gaps), Walk Mode(static walk) and Advanced-trot Mode(for climb up stairs), among which you can browse through ``src/ascend-quadruped-cpp/config`` directory to select corresponding configuration.

Step 4: run the controller
---------------------------

You need not to login into subdirectories to launch exec file, instead input the commands

.. code-block:: console

    roslaunch unitree_gazebo normal.launch

to launch gazebo simulation env. Then in another new terminal, launch the controller node,

.. code-block:: console

    rosrun ascend_quadruped_cpp sim


Remember always run

.. code-block:: console

    source ./devel/setup.bash

before launch local ROS nodes.

Step 5 (Option): Advances
--------------------------

* Joy Control
  With ROS joy package, we can use gamepad (such as Logitech F710) to send speed command to control quadruped. Press Key ``A`` to switch to joy-control mode after open JOY Node. Then manipulate handles to control the quadruped.
* Visualization
  ``xpp`` is a ROS package for legged roobt visualization, that wraping Rviz internally. We adopt it for unitree A1 robot. To start it, run following command in terminal:
  
  .. code-block:: console

      roslaunch xpp_example a1_bag.launch
  
* Realsense Camera
  In ``normal.launch`` file, you can determines wheather to use camera or not, by setting ``use_camera`` param true or false.

If you have any problems about this repository, pls contact with Yijie Zhu([zhuyijie2@hisilicon.com](mailto:zhuyijie2@hisilicon.com)).