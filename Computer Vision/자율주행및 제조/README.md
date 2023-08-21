# 자율주행/ 제조

# MAML : Model-Agnostic Meta -Learning for Fast Adaptation of Deep Network

- 어떠한 모델에도 적용할수 있는 메타러닝

## Fast Adaptation → few shot learning

- 샘플의 수가 적은 경우에 어떡할까?
- 학습할수있는 데이터가 적은상태에서 원하는 상태를 학습하는 것
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled.png)
    

## Meta learning : learn to learn

- 어떻게 학습하는지 학습하는 것
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%201.png)
    
- 학습방법이 조금 다름
- 5개의 이미지를 보여주고 test set에서 2개의 data를 보여준다. 이후 2개의 data가 보여준 5개중에 무엇인지 맞춰야하는 학습

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%202.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%203.png)

- 이것을 이해할수 있다면 MAML의 끝임

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%204.png)

## Experiment

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%205.png)

- 데이터 포인트 5 개로 추론을 진행한 것
- 데이터 포인터를 10개로 늘렸을 경우 좀더 멀어지는 영역에서도 잘 맞는것
- 오른쪽은 일반적인 학습방법
    - 데이터 포인터에 대해서는 adaptation은 잘안됌
    - 전반적으로 pretrain은 preatrain 모델의 형태를 따라가려는 경향이 있음
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%206.png)
    
- Omniglot :
    - 50개의 알파벳 , 1623개의 특성
    - 20개의 instance
    - 1200 / 423 : train,test
- MinilmageNet
    - 64개의 클래스 training , 12 validation , 24 testing
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%207.png)
    
- Reinforce learning
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%208.png)
    
- 

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%209.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2010.png)

[notebook_pytorch.ipynb](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/notebook_pytorch.ipynb)

# PS-GAN : Pedestrian-Synthesis-GAN

- 자율주행을 위해선 물체 검출용 대규모 데이터셋 필요
- 하지만 악천우나 밤에 데이터가 어려움
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2011.png)
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2012.png)
    
- 그러면 어떻게 ?
    - 데이터 합성, 데이터 가정, syntatic 영상을만들고 realistic 하게 바꾼후 사용

## 합성 방법

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2013.png)

- 작은 사람을 합성

## Proposed Method

- 보행자 부분 noise로 변환
- noise에 따른 보행자 생성
- 보행자 영역/배경 영역에 대한 adversarial training

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2014.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2015.png)

## Loss Function

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2016.png)

- LSGAN → MSE 사용 : 식 자세히 보면 이해가됌
- GAN은 log 사용
- 사람이 있는 경우 Noise를 주었을떄

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2017.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2018.png)

- 사람이 없는 경우

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2019.png)

## Result

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2020.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2021.png)

- 생성된 영상의 detect 결과

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2022.png)

[PS_GAN.ipynb](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/PS_GAN.ipynb)

# DRAEM : A discriminatively trained reconstruction embedding for surface anomaly detection

[DREAM_pytorch.ipynb](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/DREAM_pytorch.ipynb)

- 드램
- Visual Surface anomaly detection이란?
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2023.png)
    
- train시 발견되지 않은 상태들을 test상태에서 검출해야함
- 1000개중 1 , 10000개중 1개등 아주 드물게 발생하는 데이터를 찾아라!

## 기존 방법과의 차이?

- 기존방법
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2024.png)
    
- DRAME
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2025.png)
    
- boundary 가 조금 더 촘촘해지는 효과가 있음
- 아직 감이 잘안잡힘

## Proposed Method

- detection process

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2026.png)

- Discriminative sub -network
    - skip connection이 포함된 unet
- Reconstructive sub-network
    - auto encoder와 비슷한 형태
- 아래쪽 그림 3
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2027.png)
    
    - 다른이미지 , 원본, 랜덤마스크 → 다른이미지 + 원본 + 마스크 한것으로 학습진행
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2028.png)
    
1. P : noise sampling 
2. Ma : Threshold Mask 
3. Ma : inverse
4. 3개 합 통해서 image 생성
5. image A에 대해서는 augmentation 수행으로 (오른쪽 그림) image 생성
- 마스크의 크기와 모양도 다양하게 augmentation 수행

## Result

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2029.png)

## Surface anomaly detection 의 한계

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2030.png)

- label을 전체로 봐야하는가 부분으로 봐야하는가?
- 부분이오류면 결국에 전체인 오류 아닌가?

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2031.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2032.png)

- heatmap이 번지지 않고 label과 가장 비슷하고 깔끔하게 나옴

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2033.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2034.png)

# MUNIT : Multimodal Unsupervised Image2Image Translation

- image2image translation에대한 초창기 work
- 전 개념은 autoencoder 개념으로 translation진행

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2035.png)

- 해당영상의 컨텐츠와 스타일 저장

## Proposed Method

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2036.png)

- unsupervised로 대부분 해결해야함?
    - 왤까 ? 입력과 output에 대한 pair로 짜여져 있는 학습이 아니기 때문에
    - 입력을 보고 알아서 판단해 image를 생성해줘야함
    - 따라서 loss function을 다양하게 줌
- 각각 이미지에 대한 style과 content 복원 과정
- 하지만 x1,x2에 대해서 무엇이 style이고 무엇이 content인지 알수없음
- 따라서 cross domain translation 수행

### model Architecture

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2037.png)

- encoder part에서 style , content code를 만듬
- 아래 식을 이용해서 Adin Parameter 설정
- 다시 upsampling하여  이미지 생성
    
    ![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2038.png)
    

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2039.png)

- 각각의 loss를 어떻게 설정하는지에 대한 식

## Experiments

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2040.png)

- edges → shoes
- 각 모델에 대한 edge →shoes 결과
- random noise에 sampling에 대해서 나온것인지? style 을 바꿔가면서 나온것인지?
- Bicycle GAN 을 사용해도 좋은데 supervised임

### Quantitative result

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2041.png)

- Diversity > 생성된 이미지의 distance사이의 거리

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2042.png)

- 다양한 결과 생성 가능
- 다양한 도메인 transfer

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2043.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2044.png)

- content를 바꿀순 있지만 , 무늬등,color, 등은 가능하지만 객체의 위치를 바꾸지는 못함

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2045.png)

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2046.png)

- style image를 같이 넣어줫을때의 결과

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2047.png)

## result

![Untitled](%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B2%E1%86%AF%E1%84%8C%E1%85%AE%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8C%E1%85%A6%E1%84%8C%E1%85%A9%20534d9045b3bc4280848398f9dc9fef05/Untitled%2048.png)