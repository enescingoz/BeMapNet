FROM nvidia/cuda:11.1.1-devel-ubuntu20.04
ENV DEBIAN_FRONTEND=noninteractive


RUN apt-get update && apt-get upgrade -y

#### DEPENDENCIES BeMapNet
# PYTHON 3.8 AND PIP3
RUN apt-get install wget git -y 
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:deadsnakes/ppa -y
RUN apt-get install -y python3.8
RUN ln -s /usr/bin/python3.8 /usr/bin/python
RUN apt-get install -y libgl1-mesa-dev libglib2.0-0
RUN apt-get install -y python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# OTHER DEPENDENCIES
RUN pip3 install torch==1.10.1+cu111 torchvision==0.11.2+cu111 -f https://download.pytorch.org/whl/torch_stable.html

# PIP
RUN pip3 install -U pip setuptools
RUN pip3 install -U setuptools
RUN pip3 install -U six
RUN pip3 install -U opencv-python-headless

# MMCV
RUN pip3 install -U openmim
RUN mim install mmcv==1.7.1

# Detectron2
RUN python3 -m pip install detectron2 -f https://dl.fbaipublicfiles.com/detectron2/wheels/cu111/torch1.10/index.html



SHELL ["/bin/bash", "-c"]


# SETUP WORKSPACE
RUN mkdir -p ~/workspace/src \
    && cd ~/workspace/src \
    && git clone https://github.com/enescingoz/BeMapNet.git \
    && cd BeMapNet \
    && pip3 install -r requirement.txt
    


WORKDIR /root/workspace