FROM ubuntu:20.04

SHELL ["/bin/bash", "-c"]

RUN apt update && apt upgrade -y gnupg wget lsb-release vim tmux libglvnd0 libglvnd-dev x11-apps mesa-utils python3-pip

RUN DEBIAN_FRONTEND=noninteractive apt install -y tmux htop gedit

RUN yes | pip3 install pynput pymap3d

RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

RUN wget -q https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc -O- | apt-key add -

RUN apt update -y

RUN DEBIAN_FRONTEND=noninteractive apt install ros-noetic-desktop-full -y

RUN DEBIAN_FRONTEND=noninteractive apt install ros-noetic-rtabmap-ros -y

RUN echo "source /opt/ros/noetic/setup.bash" >> /root/.bashrc

RUN echo "source /usr/share/gazebo/setup.sh" >> /root/.bashrc

RUN source /root/.bashrc

RUN apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential

RUN echo "set -g mouse on" >> /root/.tmux.conf

RUN echo "set-option -g history-limit 20000" >> /root/.tmux.conf

RUN mkdir -p /root/catkin_ws/src

WORKDIR /root/catkin_ws
