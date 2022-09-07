Hello quadruped-robot
*********************

In the distribution of ``demo/demo_hellowold`` is a Hello World project. This introduction is used to help you to have a basic understanding. We'll descirbe the ``demo_helloworld`` in more detail to let you understand the logic of our code better.

There we use a1 quadruped robot of unitree to perform a simplest demo.

Launch Gazebo
=============

Firstly, you should go into your workspace and open a terminal here. Please always run ``source devel/setup.bash`` (or ``source devel/setup.zsh`` if you are using zsh) before running our project. Then you can run ``roslaunch unitree_gazebo normal.launch`` to launch gazebo to load a ``.world`` file and the quadruped robot model. If all goes will you will see gazebo was started after running previous command and the quadruped robot model also show in gazebo with a sit down state.

Run the demo_helloworld
=======================

Now you should turn on another terminal and go into your workspace. Then run ``rosrun a1sim demo_helloworld``.

Initialize the ros node
=======================

Our project is based on ROS, so we should initialize the ROS node first. One ROS node is an executable file and different executable files communicate with others by ROS node.

.. code-block:: c++

    ros::init(argc, argv, "demo_helloworld");
    ros::NodeHandle nh;

Get the path
============

We have to load parameters from ``.yaml`` files and each demo have their own parameters. So we have to get the path of file that is used to storge the ``.yaml`` files.

.. code-block:: c++
    std::string pathToPackage = ros::package::getPath("a1sim");
    std::string pathToNode =  pathToPackage + ros::this_node::getName();

Reset the gazebo controller and robot model
===========================================

To develop fastly, we do not hope to relaunch gazebo after each time that the quadruped robot fall down or other situation that make the process close accidentally, so we need to reset the gazebo controller and the robot model when we run the demo every time. And this will let gazebo to reload the controller plugins and put the robot model to an fixed position where we set in advance.

.. code-block:: c++
    
    ResetRobotBySystem(nh);

Create the robot
================

After processing in gazebo, we should do some initialization for controller. The most important entity is robot, so we need to create the robot with the parameters in ``.yaml`` file. Then we have to update some attributes in robot by receiving observation from gazebo for an initialization.

.. code-block:: c++

    qrRobot *quadruped = new qrRobotA1Sim(nh, pathToNode + "/config/a1_sim.yaml");
    quadruped->ReceiveObservation();

Execute actions
===============

Now we already complete all basic initialization of this demo, we can let the robot to do some action for a look. Firstly we order the dog to stand up from the sit down state. This action will consume 3 seconds and the quadruped robot is abandon doing everything during 5 seconds. The control frequency is 1000Hz. You can change these parameters if you want to see different results.

.. code-block:: c++

    Action::StandUp(quadruped, 3.f, 5.f, 0.001f);

After standing up we let the quadruped robot keep standing for 20 seconds, and the control frequency is also 1000Hz.

.. code-block:: c++

    Action::StandUp(quadruped, 3.f, 5.f, 0.001f);

Finally the quadruped robot will sit down in 3 seconds with 1000Hz control frequency.

.. code-block:: c++

    Action::StandUp(quadruped, 3.f, 5.f, 0.001f);

Shut down the ROS node
======================

The demo here is end, we should shut down ROS node to end this process.

.. code-block:: c++

    ros::shutdown();
