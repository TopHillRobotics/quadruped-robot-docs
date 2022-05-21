Step 4: run the controller
============================

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
