Welcome to ECNU Quadruped Documentation!
===========================================

The program has been tested on ``Ubuntu18(gazebo9)`` and ``Ubuntu20(gazebo11)``. 
Make sure that you computer computation resource is enough. 
The cost time of running a while loop in the main function(s.t., in ``exec/test.cpp``) indicates the information. 
In gazebo simulation, if the cost time is smaller than 1 ms, the controller is able to run in realtime. 
If it is larger than 1 ms but smaller than 3ms, the controller runs successfully under ros time, which is slowed down. 
For example, to keep the controller making action with frequency at 500 Hz(in simulation time measurement), 
while the loop cost time (in realworld time measurement) is 2.5 ms, you need to set the ``real_time_update_rate`` 
in ``.world`` configuration file of gazebo to be ``1000/2.5 = 400``, and make ``useRosTime`` true.

.. note::

   This project is under active development.


.. toctree::
   :maxdepth: 2
   
   index.rst
   install.rst
   helloworld.rst
   demo.rst
