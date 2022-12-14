# Seq_nms_YOLO
This project is an adaptation of https://github.com/melodiepupu/seq_nms_yolo to help install and run the Seq-NMS and YOLOv2 for video object detection.
#### Membres: Yunyun SUN, Yutong YAN, Sixiang XU, Heng ZHANG

#### Adapted by: Laura Herrera, Rosa Hornero


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

3) Create the environment. Two ways 'automatically' or 'manually'.

   3.1 Automatically. Modify the script `Yolo_env.yml`, putting the name of the environment that you want in the first line and change in the last line the prefix with the address where you will save the environment. Then run the following command in the terminal:
  
     `$ conda env create -f Yolo_env.yml`
     
     `$ source activate env_name`
  
   3.2 Manually. 
     
     - Create an anaconda environment with python 2.7 (it is important that it is this version as it is the one supported by the code)
     
       `$ conda create --name env_name python=2.7`
       
     - Activate the environment
     
        `$ source activate env_name`
        
      - Install the following libraries
        - cv2: `$ conda install -c conda-forge opencv`
        - matplotlib: `$ conda install matplotlib`
        - scipy: `$ conda install -c anaconda scipy`
        - tensorflow: `$ conda install -c anaconda tensorflow-gpu`
        - pillow: `$ conda install -c anaconda pillow`
        - tf_object_detection: `$ conda install -c conda-forge tf_object_detection`
  
4) Install opencv with version 4.2.0.32 to avoid any warning or error when reconstructing the video.

`$ pip install opencv-python==4.2.0.32`

5) Once you have the environment activated, create the project by executing the makefile as follows:

`$ make`

6) Once the project was created you have to modify the PATH and LD\_LIBRARY\_PATH variables of the develoment environment:

`$ export PATH=/usr/local/cuda-10.1/bin${PATH:+:${PATH}}`

`$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64`

`$ export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/cuda-10.1/lib64`

7) Then download weights and tiny weights

`$ wget https://pjreddie.com/media/files/yolo.weights`

`$ wget https://pjreddie.com/media/files/yolo-tiny.weights`

8) Place an avi format video in the folder /seq_nms/video

9) Access that folder and execute the following commands to convert the video to frames.

`$ cd video`

`$ python video2img.py -i example_video.avi`

`$ python get_pkllist.py`

10) Go back to the /seq_nms folder and run the 'yolo_seqnms.py' script in charge of detecting the objects in each frame.

`$ cd ..`

`$ python yolo_seqnms.py`

11) Go back to the video folder and run the following script to reconstruct the video with the detected objects.

`$ cd video`

`$ python img2video.py -i output`

The result will be found in video/output

## Reference

This project copies lots of code from [darknet](https://github.com/pjreddie/darknet) , [Seq-NMS](https://github.com/lrghust/Seq-NMS) and  [models](https://github.com/tensorflow/models).

Some instructions were extracted from: https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html and 
https://github.com/sergiomcgd/seq_nms.git

