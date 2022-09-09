
Overview
=========

This project provides an architecture and some key algorithms to control quadruped robots, including state estimator, gait generator, stance and swing leg controllers. 
This project supports three control modes

* **velocity mode** allows a user to control the robot's linear and angular velocity.

* **position mode** generates user-defined gaits using gait configurations.

* **hybrid mode** uses position and torque to implement flexible locomotion.

The project now supports Unitree A1 robot and DeepRobotics Lite2A robot, and can be extended to support other quadruped robots such as Unitree AlienGO/GO1, DeepRobotics Jueying/X20 and Anymal. For more information about quadruped robots, check out the following websites


* `Unitree <https://github.com/unitreerobotics>`_

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

You can find the source code at `GitHub <https://github.com/TopHillRobotics/quadruped-robot/>`_. The source code includes four directories

* **demo** contains various demos to understand the software architecture and algorithms.

* **extern** contains the third-party dependencies to successfully run our code.

* **quadruped** contains the core algorithms of our project.

* **simulation** contains the configuration to run the simulation.
