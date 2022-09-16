# Data-Handling-for-Competition
### Team
* 윤소미, 장주찬, 전규원, 한정현, 허권
### Object
* Data Handling for Kaggle Competition : HuBMAP + HPA - Hacking The Human Body
### Introduction
* rle to mask -> Create binary, multi dataset
* Class 별로 데이터 편향 줄이기 : kidney, prostate, lagre intestine, spleen, lung 데이터셋의
비중을 맞추기 위함
* Background 비율 조절 : Background가 학습에 방해요인이라 생각하여 비중을 덜어내기 위함
* Resize : 다운스케일링
* Convert, Convert with stride : 3000x3000 픽셀의 데이터셋을 해상도 손상 없이 다운스케일링 하기위함
* Delete non-mask image : 학습률을 높이기 위한 목적으로 Backgound 뿐인 마스크 이미지 제거
* Create COCOformat : noise 목적으로 Copy & Paste 데이터셋을 만들기 위함
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
