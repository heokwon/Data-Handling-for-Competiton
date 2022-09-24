# Data-Handling-for-Competition
### Team
* 윤소미, 장주찬, 전규원, 한정현, 허권
### Object
* Data Handling for Kaggle Competition : HuBMAP + HPA - Hacking The Human Body
### Introduction
* **rle to mask** -> Create binary, multi dataset
* **Class 별로 데이터 편향 줄이기** : kidney, prostate, lagre intestine, spleen, lung 데이터셋의
비중을 맞추기 위함
* **Background 비율 조절** : Background가 학습에 방해요인이라 생각하여 비중을 덜어내기 위함
* **Resize** : 다운스케일링
* **Convert** : 3000x3000 픽셀의 데이터셋을 해상도 손상 없이 다운스케일링 하기위함   
원본 이미지를 리사이징 한 다음 정해준 size로 convert해주는데, 주어지는 reduce값에 따라 convert되는 개수, 패딩 정도가 다름
다양한 reduce값을 준 뒤 패딩값이 제일 적은 값으로만 선정한 후, 같은 input size에 여러 reduce값을 준 데이터셋을 합침   
ex) input-size : 256 -> reduce 4 - 원본이미지/16, reduce 6 - 원본이미지/9 -> 같은 256x256사이즈의 이미지여도 ground truth값은 다 다름   
위와 같이 다양한 reduce값의 이미지를 하나의 데이터셋으로 묶어서 학습시켰을 때 성능이 뛰어남
* **Convert with stride** : 3000x3000 픽셀의 데이터셋을 convert할 때, stride값을 추가   
앞서 말한 다양한 reduce값의 256x256 데이터셋에 stride를 128 ( input size의 절반만큼 ) 주고 데이터셋을 만들었을 때 성능이 가장 좋았음 
* **Delete non-mask image** : 학습률을 높이기 위한 목적으로 Backgound 뿐인 마스크 이미지 제거
* **Create COCOformat** : noise 목적으로 Copy & Paste 데이터셋을 만들기 위함
* **Mosaic augmentation(offline)** : convert dataset 4장을 랜덤하게 mosaic하여 데이터증강, 성능이 좋지 못했음
* **LBP augmentation(offline)** : convert with stride 데이터셋으로 진행 , 성능이 좋지 못했음
* **Binary2Multi** : binary형태의 데이터셋에 label별로 array를 다르게 줌으로써 multi데이터셋으로 변환   
kidney - 1 , prostate - 2 , largeintestine - 3 , spleen - 4 , lung - 5   
mmsegmentation에서 binary 보다 multi dataset으로 학습시킨 결과가 더 좋았음
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
