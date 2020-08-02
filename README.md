# Face Detection

Fast and reliable face detection with [RetinaFace](https://arxiv.org/abs/1905.00641).

This repo provides the out-of-box RetinaFace detector.

### Requirements

- Python 3.5+ (it may work with other versions too)
- Linux, Windows or macOS
- PyTorch (>=1.0)

While not required, for optimal performance it is highly recommended to run the code using a CUDA enabled GPU.

## Install

The easiest way to install it is using pip:

```bash
pip3 install git+https://github.com/rafale77/face-detection.git@master
```

## Usage
##### Detect face and five landmarks on single image
```python
from skimage import io
from face_detection import RetinaFace

detector = RetinaFace()
img= io.imread('examples/obama.jpg')
faces = detector(img)
box, landmarks, score = faces[0]
```
##### Running on CPU/GPU

In order to specify the device (GPU or CPU) on which the code will run one can explicitly pass the device id.
```python
from face_detection import RetinaFace
# 0 means using GPU with id 0 for inference
# default -1: means using cpu for inference
detector = RetinaFace(gpu_id=0) 
```
|      | GPU(GTX 1080TI,batch size=1) | GPU(GTX 1080TI，batch size=750) | CPU(Intel(R) Core(TM) i7-7800X CPU @ 3.50GHz) |
| ---- | ---------------------------- | ------------------------------- | --------------------------------------------- |
| FPS  | 44.02405810720893            | 96.64058005582535               | 15.452635835550483                            |
| SPF  | 0.022714852809906007         | 0.010347620010375976            | 0.0647138786315918                            |



## Reference

- Network and pretrained model are from [biubug6/Pytorch_Retinaface](https://github.com/biubug6/Pytorch_Retinaface)

```
@inproceedings{deng2019retinaface,
title={RetinaFace: Single-stage Dense Face Localisation in the Wild},
author={Deng, Jiankang and Guo, Jia and Yuxiang, Zhou and Jinke Yu and Irene Kotsia and Zafeiriou, Stefanos},
booktitle={arxiv},
year={2019}
```
