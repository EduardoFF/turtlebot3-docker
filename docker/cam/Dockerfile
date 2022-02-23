FROM arm64v8/ros:melodic-robot-bionic

MAINTAINER Eduardo Feo-Flushing

RUN apt-get update && apt-get install --assume-yes \
  sudo \
  ros-melodic-usb-cam \
  ros-melodic-image-proc

# create non-root user
ENV USERNAME ros
RUN adduser --ingroup sudo --disabled-password --gecos "" --shell /bin/bash --home /home/$USERNAME $USERNAME
RUN usermod -a -G video ros
RUN bash -c 'echo $USERNAME:ros | chpasswd'
ENV HOME /home/$USERNAME
USER $USERNAME

# create catkin_ws
RUN mkdir /home/$USERNAME/catkin_ws
WORKDIR /home/$USERNAME/catkin_ws

# add catkin env
RUN echo 'source /opt/ros/melodic/setup.bash' >> /home/$USERNAME/.bashrc
RUN echo 'source /home/$USERNAME/catkin_ws/devel/setup.bash' >> /home/$USERNAME/.bashrc
