# Data-Handling-for-segmentation
### Object
* Data Handling for Kaggle competition HuBMAP + HPA : Hacking human body
### Introduction
* rle to mask -> Create binary, multi dataset
* Class 별로 데이터 편향 줄이기
* Background 비율 조절
* Resize
* Convert, Convert with stride
* Delete non-mask image
* Create COCOformat
* augmentation - Mosaic, Laplacian pyramid blending
### Env and Requirements
* Google Colab
* Pandas, Pillow, cv2, imageio, matplotlib, pycocotools, skimage, rasterio
### Reference
* https://github.com/twyunting/Laplacian-Pyramids
* https://www.kaggle.com/code/nghihuynh/data-augmentation-laplacian-pyramid-blending
* https://www.kaggle.com/code/alejopaullier/how-to-create-a-coco-dataset
* https://github.com/Mr-TalhaIlyas/Mosaic-Augmentation-for-Segmentation
* https://www.kaggle.com/code/thedevastator/converting-to-256x256
* https://www.kaggle.com/code/e0xextazy/multiclass-dataset-768x768-with-stride-for-mmseg
