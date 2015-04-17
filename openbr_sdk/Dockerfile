FROM ubuntu

RUN apt-get update && apt-get upgrade -y

# Following http://openbiometrics.org/doxygen/latest/linux_gcc.html

RUN apt-get install -y build-essential cmake cmake-curses-gui git

# From 4.
RUN apt-get install -y qt5-default libqt5svg5-dev qtcreator

RUN apt-get install -y wget unzip

ENV OPENCV_VERSION 2.4.10

RUN wget -O opencv.zip http://downloads.sourceforge.net/project/opencvlibrary/opencv-unix/$OPENCV_VERSION/opencv-$OPENCV_VERSION.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fopencvlibrary%2Ffiles%2F%3Fsource%3Dnavbar

RUN unzip opencv.zip

RUN cd opencv-$OPENCV_VERSION && mkdir build && cd build && cmake -DCMAKE_BUILD_TYPE=Release .. && make -j4 && make install && cd ../..

RUN rm -rf opencv-$OPENCV_VERSION opencv.zip

RUN git clone https://github.com/biometrics/openbr.git

RUN cd openbr && git checkout 0.5 && git submodule init && git submodule update && mkdir build && cd build && cmake -DCMAKE_BUILD_TYPE=Release .. && make -j4 && sudo make install

# sharing X11 as in http://stackoverflow.com/a/25280523/535203
ENV DISPLAY :0
ENV XAUTHORITY /tmp/.docker.xauth
