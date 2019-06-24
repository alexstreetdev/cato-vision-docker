FROM alexstreet/opencv-base:3.4.4headless

RUN sudo apt-get update && apt-get install -y \
 git \
 python3-pip

RUN pip3 install \
 imutils \
 pika \
 jsonpickle \
 requests

WORKDIR app

RUN git clone https://github.com/alexstreetdev/cato-vision

ENV input_url='http://192.168.0.47:8080/?action=stream'
ENV output_url='http://192.168.0.44:5000'
ENV camera_name='camera'
ENV threshold=10000
ENV mqenabled='N'
ENV mqserver='127.0.0.1'
ENV mqq='hello'

CMD python3 -u ./camera-movement.py -i ${input_url} -o ${output_url} -n ${camera_name} -t ${threshold} -r ${mqenabled} -s ${mqserver} -q ${mqq}
