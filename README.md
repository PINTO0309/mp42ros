# mp42rosimg
The program only Publish MP4 videos with the specified topic name and period. https://github.com/PINTO0309/simple-ros2-processing-tools
## 1. Install ROS2
```bash
DISTRO=humble

sudo apt update && sudo apt install -y locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

sudo apt install software-properties-common
sudo add-apt-repository universe

sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key \
  -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
sudo apt install -y \
ros-${DISTRO}-rosbag2 \
ros-${DISTRO}-vision-opencv \
ros-${DISTRO}-vision-msgs \
ros-${DISTRO}-image-pipeline

pip install opencv-contrib-python
```
## 2. Usage
```bash
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

https://github.com/PINTO0309/mp42ros/assets/33194443/8042fa00-6fd1-49b0-bff4-c1c5e2a6e31f


https://github.com/PINTO0309/rosimg2mp4
