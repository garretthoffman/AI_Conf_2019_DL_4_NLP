# Set the base image to Ubuntu
FROM tensorflow/tensorflow:latest-py3-jupyter

# File Author / Maintainer
MAINTAINER Garrett Hoffman

COPY requirements.txt /root/

RUN pip install -r /root/requirements.txt
RUN rm /root/requirements.txt

WORKDIR /root

CMD ["/bin/bash"]
