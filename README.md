# mp42ros
The program only Publish MP4 videos with the specified topic name and period.


```
rm -rf build install log \
&& colcon build \
&& source install/setup.bash \
&& source install/local_setup.bash

ros2 run mp42ros runner \
--ros-args \
-p mp4_file_path:=test.mp4 \
-p send_topic_name:=/zed2i/zed_node/rgb_raw/image_raw_color \
-p loop:=True \
-p fps:=15.0
```