FROM alexstreet/opencv-base:3.4.4

RUN apt-get update && apt-get install -y \
 git

RUN git clone https://github.com/alexstreetdev/cato-vision

RUN pip3 install \
 argparse \
 jsonpickle \
 pika \
 requests \
 -i https://www.piwheels.hostedpi.com/simple

ENV rabbit_mq_host='127.0.0.1'
ENV username='cato'
ENV password='cato'
ENV rabbit_mq_queue='vision_cmd_detect-face'
ENV haar_file='haarcascade_frontalface_default.xml'
ENV object_name='face'
ENV image_store_url='127.0.0.1:5000'

WORKDIR ./cato-vision

CMD python3 detect.py -rh=${rabbit_mq_host} -un=${username} -pw=${password} -qn=${rabbit_mq_queue} -hc=${haar_file} -nm=${object_name} -is=${image_store_url}
