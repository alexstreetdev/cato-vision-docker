FROM balenalib/raspberry-pi-debian:latest

RUN sudo apt-get update && apt-get install -y \
    git \
    build-essential \
    cmake \
    libjpeg8-dev \
    libv4l-dev \
    imagemagick \
    libraspberrypi-dev

RUN git clone https://github.com/jacksonliam/mjpg-streamer.git

WORKDIR /mjpg-streamer/mjpg-streamer-experimental

RUN make
RUN sudo make install
#    && chmod +x docker-start.sh

RUN export LD_LIBRARY_PATH=.

CMD ./mjpg_streamer -i "input_raspicam.so" -o "output_http.so -w ./www"
