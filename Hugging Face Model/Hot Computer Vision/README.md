# HOT Computer Vision

# GLPN - Depth Estimation

- 이미지의 다양한 객체의 깊이를 찾아냄
- 방식
    - 이미지와 rgb입력
    - Encoder block → 하나의 Unet으로 볼수있음
    - 출력 → 깊이맵
    - 목표 : rgb를 깊이맵으로 변환하는것
- 파인튜닝 → NYU Depth Dataset V2
    - 오픈소스 무료제공
    
    [6_1_GLPN_Depth_Estimation (1).ipynb](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/6_1_GLPN_Depth_Estimation_(1).ipynb)
    

# Vit_Large - Image Classification

- 구글에서 제안
- Hugging face에서 가중치 제공
- vit-large-patch32-384 사용
    - 384*384 image
    - 100만개의 이미지 , 1000개의 클래스
- CLS 토큰을 사용 → 시퀀스의 시작 혹은 끝을 트랜스포머에 알려주는 역할
    - 분류에서는 시퀀스의 시작을 알리기 위해 사용
- ImageNet에서 파인튜닝된 모델
- 따라서 cifar10 → 추가 finetuning
- datasets에서 사용가능
    - 5만개의 데이터, 테스트 1만

[6_2_vit_large.ipynb](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/6_2_vit_large.ipynb)

# DETR - Object Detction

## Resnet Backbone

- end to end object detction
- 객체 감지위해 매우 작은 coco_lp_preivew 사용

## object detection

- 차량번호판 감지 finetuning

[6_3_detr_Object_Detection.ipynb](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/6_3_detr_Object_Detection.ipynb)

# CLIPSeg -Segmentatio -Zero shot Image

- zero shot이란?
    - 이전에 본적없는 것들 예측
    - CLipSeg
- 텍스트를 전달하고 임베딩 + 이미지 전달하고 이미징

![Untitled](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/Untitled.png)

[6_4_ClipSeg.ipynb](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/6_4_ClipSeg.ipynb)

# Stable Diffusipn - Image to Image

- stable diffusion 이전에 이미지 합성이라 불린 모델이 많아 image2 image라고 불림
- 이후 text2 image , image2image 많아짐
- Huggingface
- StableDiffusion2ImgPipline
- 왜  Pipeline이 필욯ㄴ가?
    - Unet과 Variation AutoEncoder
- Text enocder 존재
- 이미지 문맥 가져와 text 문맥과손실 계산
- instruct-pix2pix

[6_5_Image_to_Image_Stable_Diffusion_Image_Variations (1).ipynb](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/6_5_Image_to_Image_Stable_Diffusion_Image_Variations_(1).ipynb)

# Maxim TF - Denoising Image

![Untitled](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/Untitled%201.png)

- image에 적용
- down sampling up sampling
- 이미지 크기줄이고 키우는 것
- 세그멘테이션에 사용되는 주요과정
- 허깅페이스에 2가지만 있음
    
    ![Untitled](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/Untitled%202.png)
    
- 여기서는 tensorflow 사용

[6_6_DDPM_image_denoising.ipynb](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/6_6_DDPM_image_denoising.ipynb)

# VideoMAE base-sized model - Video Classification

- 파인튜닝~
- Video에 대한 classifcaiton 을 만드는듯
- MAE : masked Auto Encoder
- [ ]  특정 Video Masking 적용해보기

[6_7_Video_Classification_videoMAE.ipynb](HOT%20Computer%20Vision%20bb412d2f91184401970eeb866d93df2f/6_7_Video_Classification_videoMAE.ipynb)