# MSD Dataset Task03 Liver

This repository provides a benmarking guide and recipe to train the template algorithms, validation performance, and is tested and maintained by NVIDIA.


## Task Overview

The task is the volumetric (3D) segmentation of the spleen from CT image. The segmentation of spleen is formulated as the voxel-wise 2-class classification. Each voxel is predicted as either foreground (spleen) or background. And the model is optimized with both Dice loss and Cross Entropy loss between the predicted mask and ground truth segmentation. The dataset is from the 2018 MICCAI challenge [Medical Image Segmentation (MSD)](http://medicaldecathlon.com/).

- Target:
    1. spleen
- Modality: CT
- Size: 128x128x96 3D volumes (40 Training + 20 Testing)
- Challenge: MSD MICCAI Challenge

##### Validation performance: NVIDIA DGX-1 (4x V100 16)

The complete command of **Auto3DSeg** can be found [here](../../README.md#reference-python-apis-for-auto3dseg). And our validation results are obtained on NVIDIA DGX-1 with (4x V100 16GB) GPUs.

| Methods| Dimension | GPUs | Batch size / GPU | Fold 0 | Fold 1 | Fold 2 | Fold 3 | Fold 4 | Avg |
|:------:|:---------:|:----:|:----------------:|:------:|:------:|:------:|:------:|:------:|:---:|
| SegResNet   | 3 | 2 | 2 |  |  |  |  |  | 
| SegResNet2D   | 3 | 4 | 2 | 0.70874 | 0.64704 | 0.57161 | 0.55775 | 0.71749 | 0.64053
| DiNTS   | 3 | 4 | 2 | 0.44999 | 0.66607 | 0.72522 | 0.39628 | 0.65510 | 0.57853
| SwinUNETR   | 3 | 2 | 2 |  |  |  |  |  | 
