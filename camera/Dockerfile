FROM balenalib/rpi-raspbian:jessie

ENV fps=5
ENV x=640
ENV y=480
ENV flags=""

RUN sudo apt-get update && apt-get install -y \
    git \
    build-essential \
    cmake \
    libjpeg8-dev \
    libv4l-dev \
    imagemagick \
    libraspberrypi-dev

RUN git clone https://github.com/jacksonliam/mjpg-streamer.git

RUN sudo ln -s /usr/include/linux/videodev2.h /usr/include/linux/videodev.h

WORKDIR /mjpg-streamer/mjpg-streamer-experimental

RUN make
RUN sudo make install
RUN sudo chmod +x docker-start.sh

RUN export LD_LIBRARY_PATH=.

EXPOSE 8080

CMD sudo ./mjpg_streamer -o "output_http.so -w ./www" \
-i "input_raspicam.so \
-fps ${fps} \
-x ${x} \
-y ${y} \
${flags}"
