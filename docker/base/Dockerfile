FROM arm64v8/ros:melodic-robot-bionic

MAINTAINER Joshua Schraven

RUN apt-get update && apt-get install --assume-yes \
  vim-nox \
  sudo \
  python-pip \
  ros-melodic-turtlebot3-bringup \
  ros-melodic-turtlebot3-description \
  ros-melodic-turtlebot3-msgs \
  ros-melodic-turtlebot3-teleop


# create non-root user
ENV USERNAME ros
RUN adduser --ingroup sudo --disabled-password --gecos "" --shell /bin/bash --home /home/$USERNAME $USERNAME
RUN bash -c 'echo $USERNAME:ros | chpasswd'
ENV HOME /home/$USERNAME
USER $USERNAME

# create catkin_ws
RUN mkdir /home/$USERNAME/catkin_ws
WORKDIR /home/$USERNAME/catkin_ws

# add catkin env
RUN echo 'source /opt/ros/melodic/setup.bash' >> /home/$USERNAME/.bashrc
RUN echo 'source /home/$USERNAME/catkin_ws/devel/setup.bash' >> /home/$USERNAME/.bashrc
