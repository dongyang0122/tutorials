# MSD Dataset Task01 BrainTumour

This repository provides a benmarking guide and recipe to train the template algorithms, validation performance, and is tested and maintained by NVIDIA.


## Task Overview

The task is the volumetric (3D) segmentation of the spleen from CT image. The segmentation of spleen is formulated as the voxel-wise 2-class classification. Each voxel is predicted as either foreground (spleen) or background. And the model is optimized with both Dice loss and Cross Entropy loss between the predicted mask and ground truth segmentation. The dataset is from the 2018 MICCAI challenge [Medical Image Segmentation (MSD)](http://medicaldecathlon.com/).

- Target:
    1. spleen
- Modality: CT
- Size: 3D volumes (40 Training + 20 Testing)
- Challenge: MSD MICCAI Challenge

##### Validation performance: NVIDIA DGX-1 (8x V100 16)

The complete command of **Auto3DSeg** can be found [here](../../README.md#reference-python-apis-for-auto3dseg). And our validation results are obtained on NVIDIA DGX-1 with (4x V100 16GB) GPUs.

| Methods| Dimension | GPUs | Batch size / GPU | Fold 0 | Fold 1 | Fold 2 | Fold 3 | Fold 4 | Avg |
|:------:|:---------:|:----:|:----------------:|:------:|:------:|:------:|:------:|:------:|:---:|
| SegResNet   | 3 | 2 | 2 | 0.72761 | 0.75238 | 0.71169 | 0.72088 | 0.73817 | 0.73015
| SegResNet2D   | 3 | 4 | 2 | 0.71898 | 0.74570 | 0.70627 | 0.70259 | 0.73024 | 0.72076
| DiNTS   | 3 | 4 | 2 | 0.72138 | 0.74566 | 0.71421 | 0.71124 | 0.72569 | 0.72364
| SwinUNETR   | 3 | 2 | 2 | 0.71782 | 0.74581 | 0.70628 | 0.70626 | 0.73491 | 0.72221