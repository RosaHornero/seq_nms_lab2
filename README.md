# Seq_nms_YOLO
This project is adapted from https://github.com/melodiepupu/seq_nms_yolo to simplify the execution of Seq-NMS and YOLOv2 approaches for video object detection.
#### Membres: Yunyun SUN, Yutong YAN, Sixiang XU, Heng ZHANG


---

## Introduction

![](img/index.jpg) 

This project combines **YOLOv2**([reference](https://arxiv.org/abs/1506.02640)) and **seq-nms**([reference](https://arxiv.org/abs/1602.08465)) to realise **real time video detection**.
This tutorial is designed for Linux with Anaconda.

## Steps

1) Open a terminal in the folder where you are going to work.
2) Clone the repository and go to the seq_nm folder:

`$ git clone https://github.com/RosaHornero/seq_nms_lab2.git`

`$ cd seq_nms`

3) We create the environment. Two ways 'automatically' or 'manually'.

   3.1 Automatically. We modify the script `Yolo_env.yml`, putting the name of the environment that we want in the first line and we change in the last line the prefix with the address where we will save the environment. Then run the following command in the terminal:
  
     `$ conda env create -f Yolo_env.yml`
     
     `$ source activate env_name`
  
   3.2 Manually. 
     
     - We create an anaconda environment with python 2.7 (it is important that it is this version as it is the one supported by the code)
     
       `$ conda create --name env_name python=2.7`
       
     - Activate the environment
     
        `$ source activate env_name`
        
      - We install the following libraries
        - cv2: `$ conda install -c conda-forge opencv`
        - matplotlib: `$ conda install matplotlib`
        - scipy: `$ conda install -c anaconda scipy`
        - tensorflow: `$ conda install -c anaconda tensorflow-gpu`
        - pillow: `$ conda install -c anaconda pillow`
        - tf_object_detection: `$ conda install -c conda-forge tf_object_detection`
  
4) We install opencv with version 4.2.0.32 to avoid any warning or error when reconstructing the video.

`$ pip install opencv-python==4.2.0.32`

5) Once we have the environment activated we create the project by executing the makefile as follows:

`make`

## Reference

This project copies lots of code from [darknet](https://github.com/pjreddie/darknet) , [Seq-NMS](https://github.com/lrghust/Seq-NMS) and  [models](https://github.com/tensorflow/models).

Some instructions were extracted from: https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html


