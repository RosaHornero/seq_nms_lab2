# Seq_nms_YOLO
This project is adapted from https://github.com/melodiepupu/seq_nms_yolo to simplify the execution of Seq-NMS and YOLOv2 approaches for video object detection.
#### Membres: Yunyun SUN, Yutong YAN, Sixiang XU, Heng ZHANG
#### Adapted by: Daniel Armengod, Sergio Márquez

---

## Introduction

![](img/index.jpg) 

This project combines **YOLOv2**([reference](https://arxiv.org/abs/1506.02640)) and **seq-nms**([reference](https://arxiv.org/abs/1602.08465)) to realise **real time video detection**.
This tutorial is designed for Linux with Anaconda.

## Steps
1. Open a terminal or Anaconda Prompt.
2. Clone the repository and open the folder: 
   - `git clone https://github.com/sergiomcgd/seq_nms.git`
   - `cd seq_nms`
   
Now we are ready to create an Anaconda environment, to do this you can follow steps 3 and 4 or you can just load the environment from the provided .yml file doing: `conda env create -f Yolo_env.yml`. In case you choose the last option, you should jump to step 5. 

3. Create an environment (manually):
   - `conda create --name Yolo_env python=2.7` (make sure that you install python 2.7 as all the code is implemented using this Python version.)
   - `source activate Yolo_env`
4. Install the following libraries:
   - cv2: `conda install -c conda-forge opencv`
   - matplotlib: `conda install matplotlib`
   - scipy: `conda install -c anaconda scipy`
   - tensorflow: `conda install -c anaconda tensorflow-gpu`
   - pillow: `conda install -c anaconda pillow`
   - tf_object_detection:`conda  install  -c  conda-forge tf_object_detection`
5. Make the project (make sure that the environment is activated, if not, activate it with `source activate Yolo_env`):
   - `make`
   - Set up the development environment by modifying the PATH and LD_LIBRARY_PATH variables:
      - `export PATH=/usr/local/cuda-10.1/bin${PATH:+:${PATH}}`
      - `export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64`
      - `export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/cuda-10.1/lib64`
   
6. Download weights and tiny weights
   - `wget https://pjreddie.com/media/files/yolo.weights`
   - `wget https://pjreddie.com/media/files/yolo-tiny.weights`
7. Copy a video file to the video folder (/seq_nms/video)
8. In the video folder (/seq_nms/video) run video2img.py and get_pkllist.py:
   - `cd video`
   - `python video2img.py -i video.avi`
   - `python get_pkllist.py`
9. Return to root folder and run `python yolo_seqnms.py` to generate output images in `video/output`;
   - `cd ..`
   - `python yolo_seqnms.py`
10. To obtain a video from the resulting output images go to video folder and run `img2video.py`
   - `cd video`
   - `python img2video.py -i output`

The results would be available in the video folder.

## Reference

This project copies lots of code from [darknet](https://github.com/pjreddie/darknet) , [Seq-NMS](https://github.com/lrghust/Seq-NMS) and  [models](https://github.com/tensorflow/models).

Some instructions were extracted from: https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html


