Hello World
*********************

The Hello World demo (``demo/demo_hellowold``) is a good exaple to understand the logistic of running with our code. Here, we use a unitree A1 quadruped robot to explain the helloworld demo.

Initializzing the ROS node
=======================

Since our simulation is developped in ROS, we first need to initialize the ROS node first. It initializes the ROS components that our program needs in order to communicate to other programs.

.. code-block:: c++

    ros::init(argc, argv, "demo_helloworld");
    ros::NodeHandle nh;

Getting the YMAL path
============

Every demo has its own configuration and parameters. These parameters are stored in a ``.yaml`` file. We need to tell where the ``.yaml`` is and later we can load parameters from the given ``.yaml`` file. In this example, a unitree A1 robot is used and its configurations are store in ``a1sim`` for simulation. the helloworld example is stored in the directory ``a1sim``. We can use the following commands to get the directory ``a1sim/demo_helloworld``.

.. code-block:: c++
    std::string pathToPackage = ros::package::getPath("a1sim");
    std::string pathToNode =  pathToPackage + ros::this_node::getName();

Resetting the Gazebo controller and robot model
===========================================

We reset the Gazebo simulator's controller and the robot model. This can avoid relaunching the Gazebo every time when we run the helloword demo repetitively. This allows the Gazebo to reload the controller plugins and locate the robot at a given position and orientation.

.. code-block:: c++
    
    ResetRobotBySystem(nh);


Creating a robot
================

After launching the Gazebo, we create a robot (unitree A1) using the specified parameters stored in the  ``a1sim/demo_helloworld/config/a1_sim.yaml`` file.

.. code-block:: c++

    qrRobot *quadruped = new qrRobotA1Sim(nh, pathToNode + "/config/a1_sim.yaml");

 We also need to initialize a few robot properties by receiving observation from Gazebo.

.. code-block:: c++

    quadruped->ReceiveObservation();


Executing actions
===============

Now the initiliazation is finished. We are ready to execute actions. First, we let the robot perform the first action, standing up. It takes 3 seconds to stand up and keep 5 seconds before any other action. The parameter 0.001 is the specified time step (control frequency). You may try different arguments to understand the action. 

.. code-block:: c++

    Action::StandUp(quadruped, 3.f, 5.f, 0.001f);

After standing up we let the quadruped robot keep standing for 20 seconds, and the control frequency is also 1000Hz.

.. code-block:: c++

    Action::StandUp(quadruped, 3.f, 5.f, 0.001f);

Finally the quadruped robot will sit down in 3 seconds with 1000Hz control frequency.

.. code-block:: c++

    Action::StandUp(quadruped, 3.f, 5.f, 0.001f);


Finishing and shutting down the ROS node
======================

After the demo is finished, we shut down the ROS nodes.

.. code-block:: c++

    ros::shutdown();


Launching the demo
=============

To run the demo, we first launch Gazebo, a high fidelity robot simulator widely used in ROS community. First, in one terminal, source the setup.bash to set up the environment

.. code-block:: c++

    source ${your_workspace}/devel/setup.bash

Second, run the Gazebo simulator and load a robot.

.. code-block:: c++

    roslaunch unitree_gazebo normal.launch

Third, in a new terminal, launch a demo and run the quadruped controller node. Here, a demo helloworld lets the quadruped robot stand up.

.. code-block:: c++

    rosrun a1sim demo_helloworld

