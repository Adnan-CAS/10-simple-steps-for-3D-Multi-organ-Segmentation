# 10-simple-steps-for-3D-Multi-organ-Segmentation

# UNETR: Transformers for 3D Medical Image Segmentation

3D Multi-organ Segmentation with UNETR  (BTCV Dataset)


This tutorial is highly adopted from the baseline work [1] which demonstrates how to construct a training workflow of UNETR [2] on multi-organ segmentation task using the BTCV challenge dataset.
![image](https://lh3.googleusercontent.com/pw/AM-JKLU2eTW17rYtCmiZP3WWC-U1HCPOHwLe6pxOfJXwv2W-00aHfsNy7jeGV1dwUq0PXFOtkqasQ2Vyhcu6xkKsPzy3wx7O6yGOTJ7ZzA01S6LSh8szbjNLfpbuGgMe6ClpiS61KGvqu71xXFnNcyvJNFjN=w1448-h496-no?authuser=0)

The main features are:
1. Transforms for dictionary format data.
1. Define a new transform according to MONAI transform API.
1. Load Nifti image with metadata, load a list of images and stack them.
1. Randomly adjust intensity for data augmentation.
1. Cache IO and transforms to accelerate training and validation.
1. 3D UNETR model, DiceCE loss function, Mean Dice metric for multi-organ segmentation task.

# BTCV Dataset Intro
The dataset can be dowloaded from https://www.synapse.org/#!Synapse:syn3193805/wiki/217752.  

50 abdomen CT scans were chosen at random under the supervision of the Institutional Review Board (IRB). These scans were obtained during the portal venous contrast phase and were selected from a combination of an ongoing trial for colorectal cancer chemotherapy and a retrospective study for ventral hernias. The volume sizes ranged from 512 x 512 x 85 to 512 x 512 x 198, while the field of views varied from approximately 280 x 280 x 280 mm3 to 500 x 500 x 650 mm3. In-plane resolution varied between 0.54 x 0.54 mm2 and 0.98 x 0.98 mm2, and the slice thickness ranged from 2.5 mm to 5.0 mm.

Target: 13 abdominal organs including 1. Spleen 2. Right Kidney 3. Left Kidney 4.Gallbladder 5.Esophagus 6. Liver 7. Stomach 8.Aorta 9. IVC 10. Portal and Splenic Veins 11. Pancreas 12 Right adrenal gland 13 Left adrenal gland.

Modality: CT
Size: 30 3D volumes (24 Training + 6 Testing)  
Challenge: BTCV MICCAI Challenge

The following figure shows image patches with the organ sub-regions that are annotated in the CT (top left) and the final labels for the whole dataset (right)[3][4].
![image.png](attachment:image.png)

The image patches show anatomies of a subject, including: 
1. large organs: spleen, liver, stomach. 
2. Smaller organs: gallbladder, esophagus, kidneys, pancreas. 
3. Vascular tissues: aorta, IVC, P&S Veins. 
4. Glands: left and right adrenal gland

# References:

[1]: 3D Multi-organ Segmentation with UNETR
(https://github.com/Project-MONAI/tutorials/blob/main/3d_segmentation/unetr_btcv_segmentation_3d.ipynb)

[2]: Hatamizadeh, A., Tang, Y., Nath, V., Yang, D., Myronenko, A., Landman, B., Roth, H.R. and Xu, D., 2022. Unetr: Transformers for 3d medical image segmentation. In Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (pp. 574-584).

[3]: [High-resolution 3D abdominal segmentation with random patch network fusion (MIA)](https://www.sciencedirect.com/science/article/abs/pii/S1361841520302589)

[4]: [Efficient multi-atlas abdominal segmentation on clinically acquired CT with SIMPLE context learning (MIA)](https://www.sciencedirect.com/science/article/abs/pii/S1361841515000766?via%3Dihub)
