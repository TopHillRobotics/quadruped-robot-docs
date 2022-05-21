## Step 5 (Option): Advances

* Joy Control
  With ROS joy package, we can use gamepad (such as Logitech F710) to send speed command to control quadruped. Press Key `A` to switch to joy-control mode after open JOY Node. Then manipulate handles to control the quadruped.
* Visualization
  `xpp` is a ROS package for legged roobt visualization, that wraping Rviz internally. We adopt it for unitree A1 robot. To start it, run following command in terminal:
  ```bash
  roslaunch xpp_example a1_bag.launch
  ```
* Realsense Camera
  In `normal.launch` file, you can determines wheather to use camera or not, by setting `use_camera` param true or false.

If you have any problems about this repository, pls contact with Yijie Zhu([zhuyijie2@hisilicon.com](mailto:zhuyijie2@hisilicon.com)).
