#This is the base image
FROM fedora:28
#FROM python:3

#WORKDIR /home/user

#Copies the program into the image
#ADD myhelloworld.py /
#Install packages necessary for code into image
#RUN pip3 install flask
#RUN pip3 install flask_restful
#Expose application port, 3333 to outside world
#EXPOSE 3333
#What runs when podman run is entered

COPY requirements.txt /
COPY Input-py3.ipynb /
COPY input.yml /
COPY run.sh /

RUN dnf install python3-pip
RUN chmod +x run.sh
RUN pip3 install jupyter-client
RUN export PYTHON_LIB_PATH=/usr/lib64/python3.6/site-packages && \
  export LD_LIBRARY_PATH="/usr/lib64:/usr/local/lib${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}" && \
  rm -fr /usr/bin/python && \
  ln -s /usr/bin/python3.6 /usr/bin/python && \
  rm -fr /usr/bin/pip && \
  ln -s /usr/bin/pip-3 /usr/bin/pip && \
  pip install -r requirements.txt 
  

CMD [ "bash", "./run.sh"]

