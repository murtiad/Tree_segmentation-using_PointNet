# Tree segmentation using PointNet ++

This final study project use the neural network PointNet ++ to segment automaticaly the trees on urban area.

## Introduction 
The objective of this end of study project is to use a neural network for the automatic segmentation of urban trees.
For this, the PointNet ++ network is used. The code is retrieved from user Yanx27.

## Installation  
To use the implemantation, you must have version 2.7 of Python or higher and pytorch version 1.7 on Windows 10. 
In addition, the CUDA 10.2 Toolkit is used with the Cudnn version adapted to this version of CUDA.

## Model and modifications
The model used is PointNet ++ in MSG mode. With the following levels of abstractions: 
| Level | Points | Radius | Point per radius | MLP radius 1 | MLP Radius 2 |
|--|--|--|--|--|--| 
| 1 |  1024 | 0.3 - 2 | 32 - 64 | 16 - 16 -32 | 32 - 32 - 64|
| 2 |  512 | 1 - 3 | 32 - 64 | 64 - 64 128 | 64 - 96 - 128|
| 3 |  256 | 2 - 5 | 32 - 64 | 128 - 196 -256 | 128 - 196 - 256|
| 4 |  128 | 4 -7  | 32 - 64 | 256 - 256 - 512 | 256 - 384 -512|

## Usage 
### Segmentation 
To train a PointNet ++ model to segment : 

    Train-test_sem-seg.py
  
The form of the training, validation and test data should be as follows:
- Three folders are created in the data directory at the root
    - The training folder contains the data that will be used to train the network 
    - The test folder contains the validation data that allows the live training to be validated 
    - The Indiv folder contains the point clouds to be segmented using a trained model. 

![Dossier](https://github.com/VictorAlteirac/PFE_Tree_segmentation-using_PointNet2/blob/main/Image/Data.PNG)

The point cloud files in each of these folders should be with particulary form. 
- In .txt format with the following organisation

![Format](https://github.com/VictorAlteirac/PFE_Tree_segmentation-using_PointNet2/blob/main/Image/TXT.PNG)

The additional features can be any of them. 
In this case, in order, Roughness, radius of curvature, colours (RGB) and normals. 

## Results on databases
### DublinCity 3D
Les performances suivantes sont atteintes : 
| Perf | Accuracy |
|--|--|
| Training Accuracy |  92.5 %|
| Training Loss) | 0.255 |
| Eval Accuracy |  81.4 %|
| Eval Loss |  0.602|
| IoU Bati |  50.4 %|
| IoU Ground |  83.8 %|
| IoU Vegetation |  77.0 %|
| IoU Other | 20.0 %|
| mIoU |  **63.6 %**|

