
Overview
=========

This project provides an architecture and some key algorithms to control quadruped robots, including state estimator, gait generator, stance and swing leg controllers. 
This project supports three control modes

* **velocity mode** allows a user to control the robot's linear and angular velocity.

* **position mode** generates user-defined gaits using gait configurations and control the robot's step position.

* **hybrid mode** uses position and torque to implement flexible locomotion.

The project now supports A1 robot (Unitree-Robotics) and Lite2A robot (Deep-Robotics). This project can be easily extended to support other quadruped robots such as AlienGO/GO1 (Unitree-Robotics), Jueying/X20(Deep-Robotics) and Anymal. For more information about quadruped robots, check out the following websites

* `Unitree Robotics <https://github.com/unitreerobotics>`_

* `DEEP_ROBOTS <https://www.deeprobotics.cn/>`_

* `AnyRobotics <https://www.anybotics.com/anymal-autonomous-legged-robot/>`_

.. image:: images/trot-mpc.gif
    :width: 600

.. image:: images/walk-locomotion.gif
    :width: 600

.. image:: images/real.gif
    :width: 600

------------------

Source Code Structure
==================

You can find the source code at `GitHub <https://github.com/TopHillRobotics/quadruped-robot/>`_. The source code includes five major directories

* **demo** has many demo examples to help users understand the software usage and the project architecture itself.
* **extern** contains the third-party dependencies to successfully compile and run the code.
* **navigation** contains the codes for SLAM and navigation.
* **quadruped** contains the core modules defining robots, state, planner, dynamics and supporting algorithms.
* **simulation** contains the configuration to run demos in simulation.
