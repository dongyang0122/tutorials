# MSD Dataset Task02 Heart

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
| SegResNet   | 3 | 2 | 2 | 0.03122 | 0.89439 | 0.93661 | 0.92515 | 0.92811 | 0.74310
| SegResNet2D   | 3 | 4 | 2 | 0.88477 | 0.88727 | 0.92044 | 0.85718 | 0.91098 | 0.89213
| DiNTS   | 3 | 4 | 2 | 0.91935 | 0.92041 | 0.93708 | 0.92753 | 0.93118 | 0.92711
| SwinUNETR   | 3 | 2 | 2 | 0.91754 | 0.91581 | 0.93585 | 0.92423 | 0.92002 | 0.92269
