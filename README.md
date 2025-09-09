# LMSD‐YOLO: A Lightweight YOLO Algorithm for Multi‐Scale SAR Ship Detection

By Yue Guo, Shiqi Chen, Ronghui Zhan *, Wei Wang and Jun Zhang

This repository contains the implementation accompanying our paper LMSD‐YOLO: A Lightweight YOLO Algorithm for Multi‐Scale SAR Ship Detection.

[Paper link] (https://www.mdpi.com/2072-4292/14/19/4801)

If you find it helpful for your research, please consider citing:

```
@article{guo2022lmsd,
  title={LMSD-YOLO: A lightweight YOLO algorithm for multi-scale SAR ship detection},
  author={Guo, Yue and Chen, Shiqi and Zhan, Ronghui and Wang, Wei and Zhang, Jun},
  journal={Remote Sensing},
  volume={14},
  number={19},
  pages={4801},
  year={2022},
  publisher={MDPI}
}

```
## Overall architecture of LMSD
![Overall architecture of LMSD](/imgs/LMSD.png)

## Acknowledgment
This implementation is bulit upon [YOLOv5](https://github.com/ultralytics/yolov5) and [mobilenet](https://github.com/xiaolai-sqlai/mobilenetv3).

## Installation
Please refer to the instructions [here](requirements.txt). We leave our system information for reference.

* OS: Ubuntu 18.04
* Python: 3.8.9
* CUDA: 10.2
* PyTorch: 1.8.0 (The lower versions of Torch can cause some bugs.)

## Dataset Preparation
Please construct the datasets following these steps:

* SSDD:https://github.com/TianwenZhang0825/Official-SSDD
* HRSID:https://github.com/chaozhong2010/HRSID
* GFSDD: private dataset

## Training / Evaluation / Inference
We provide training script as follows.

(1) For the all yaml configuration files:
- all  .yaml configs in /LMSD-YOLO/models/
```
yolov5s_mymobilenetv3_DWasff.yaml
yolov5s_mymobilenetv3_DWasff_bifpn.yaml
yolov5s_mobilenetv3_DWasff.yaml
yolov5s_mobilenetv3_asff.yaml
yolov5s_DWasff.yaml
yolov5s_bifpn.yaml
yolov5s_mymobilenetv3.yaml
```
(2) Train (All training procedures strictly follow the standard YOLOv5 protocol.
)
```
python train.py --weight [weight path] --cfg [yaml path] --data [data path] --epochs 300 --batch-size 16
```
(3) Test
- Test cmd
```
python detect.py --weights [.pt] --source [data folder] --data [data yaml] 
 ```


## improved support-file modules
Location of the improved module: 
```
DWassf : ./models/DWASFFV5 class.
ASFF detection head: DWASFF_Detect.
MobileNet: InvertedResidual blocks.
```
## Pre-trained models
 All models were initialized from the official YOLOv5 pretrained weights released at https://github.com/ultralytics/yolov5. Thank you!


## Reference
[YOLOv5](https://github.com/ultralytics/yolov5) 

[mobilenet](https://github.com/xiaolai-sqlai/mobilenetv3)