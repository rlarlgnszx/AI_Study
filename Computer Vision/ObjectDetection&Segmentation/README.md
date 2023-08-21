# Object Detection & Segmentation

# Faster R-CNN

# Fast R-CNN inform

- RCNN 계열의 object detection

## obj det

- 이미지와 비디오에 대해 시맨틱 객체  시맨틱 객체 인스턴스를 감지하는 일을 다룬다.

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled.png)

- 바운딩 box 색깔 → class
- boudning box : instance 객체
- segmentation →

### 어떻게 bounding box를 localize?

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%201.png)

## SS 기법 Selective Search

- 딥러닝 이전까지 많이 사용되던 방법

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%202.png)

- bottom up 방식으로 주로 사용
1. pixel의 정보들을 서로 비교
2. pixel → super pixel? → super pixel 
    1. 즉 pixel들을 계속 서로 합침
3. 최종에 대한 segment box를 그림

# R-CNN

- SS 사용

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%203.png)

- ss를 사용해서 region proposal을 수행 → 특정한사이즈로 resize
- cnn 통과 → feature extractor → classification
- background의 label 도 추가해줘야한다.
- ground truth : 모델이 맞추길 바라는 정답
    - Ground truth label augmenation을 IoU 사용해서 적용
- IoU : Overlapping region / combined region
    - 2box
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%204.png)
    

### 나의 정의 : 그래서 faster rcnn?

1. ss로 region proposal수행 → 2000개정도의 box지역 patch? 어쩃든 무수한 box가 나오는데 이를 전부 cnn을 돌림
2. cnn계열 통과
3. feature extractor하고 그것으로 classification

---

# Fast R-CNN

- 어떻게 rcnn을 효과적으로 개선햇을까?
    - region ? cnn ? classification?

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%205.png)

- fast inference
    - 속도를 빠르게 하기위해 사진을 cnn을 한번만 통과시킴
    - 무슨말이냐 하면 이전 rcnn에서 patch마다 각 cnn을 통과시킨것과 달리 일단 사진을 넣고 cnn을 한번만 수행
    - 대신 cnn으로부터 나온 feature를 재사용해서 cost 줄임
- end-to-end training
    - svm을 지우고
- multitask learning
    - classifcation and bounding box  regression
    - bbox regresor → box에 대한 위치를 어느정도 조정
- ROI pooling layer ? → region proposal 과 비슷
    - 서로다른 patch size를 전부 맞춰

### Region of Interest Pooling layer

- Extracting Roi using SS
- Selecting sub-window for pooling
- performing maxpooling for each sub-window

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%206.png)

# Faster R-CNN method and Result

## RPN>>>> Region Proposal Network

![                                         **faster** rcnn](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%207.png)

                                         **faster** rcnn

![                                                    fast rcnn](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%208.png)

                                                    fast rcnn

- boudning box를 출력해주는 network → RPN
- fast rcnn은 아직 ss기법 사용
- faster rcnn은 rpn을 사용해서 box 찾기

### 어떻게 RPN이 region proposal을 찾을수있는가?

- boudning box를 찾을수 있는가?
    - hint : regression
    - 어떻게 ??regression으로 풀지?
    - bounding box를 찾는법? → 미리정의된 bounding box를 두고 회귀?
    - ?어떻게했지?
- Remove All randomness
    - 모든 랜덤요소 제거
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%209.png)
    
- anchor box개념 도입
    - 위사진은 5*5로나누어졌음
    - 이때 1개를 각 box당 anchor박스 여러개 적용
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2010.png)
    
- box regression을 통해 물체를 잘 나타내는 box를 찾게됌
- 또한 이것을 통해서 multiple scale과 size를 다른 scheme에 적용가능
- 어떻게 ? 3가지 방법
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2011.png)
    
    - 첫번째 :
        - 이미지의 scale을 multiple하게
        - ex) 말이 100 크기라면 이미지 사이즈를 줄였을때 10의 크기의 box에 적합해지는 이미지가 있을것이다ㅏ.
    - 두번쨰 :
        - filter의 크기를 mutiple하게 적용하여 큰물체 작은물체 검출되게 한다.
    - 세번째 :
        - muptipler references를 사용한다 0> anchor box를 여러개 사용한다.

# RPN : Region Proposal Network

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2012.png)

- sliding window 생성
    - 2k socres :
        - class layer로 가는 결과
        - 해당 sliding window에 object가 있는지 없는지 판단하는 score
    - 4k coordinates  : x,y,w,h
        - slliding window안에 있는 bounding box에 대해 regresison
- anchor box가 여러개있으면 → 위 고양이사진에서도 어떻게 최적의 box?
    
    ### NMS 사용 : Non -Maximum Suppresion
    
    - box하나만 남기는 방법
    - confidence score : 물체가 있다고 확신하는 score
    - IoU score : 박스와 주변박스들간의 ioU
        - 겹치는 박스 다 제거
    - 즉 confidence가 높은 box 하나만 남게됌

## Training 방법

- Loss
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2013.png)
    
    - classifcation loss와 boundingbox regression loss 함꼐 사용
- 4단계
    - imagenet pretrained model을 end-to-end 로 RPN을 학습진행
    - fast rcnn을 trainining (대신 여기선 ss가 아니라 RPN으로부터나온 region)
    - 위 두모델의 파라미터 shrare 하고 RPN training
    - 위 두모델으 파라미터 fast rcnn 훈련

## Performance measure?

- mAP : mean Average Precision
- Precision and Recall
    - Precision  : 정밀도 : 양성이라고 예측한것중 정답이 양성인 것의 비율
        - (정답)/(모델)
    - Recall  : 양성인것중 양성이라고 예측한 것의 비율
        - (모델) / (정답)
- F1 score : 정밀도와 재현도의 조합평균

### mAP

- AP
    - precision-recall그래프를 단조감조함수로 변경후 면적 계산
- mAP
    - 복수의 class에 대한 AP의 평균값

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2014.png)

- SS: Selective Search, EB : Edge Box ,ZF ?
    - 위에서 보면 proposal을 300개만 사용해도 2000개 사용한 다른 모델보다 높은 결과
- trainig → test
- 아래 그림은 trainig data의 종류와 rpn의 cnv와 faster rcnn의 share여부에 따라 나오는 결과

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2015.png)

- feature sharing ? → 데이터가 낮을때 성능을 끌어올리는 것
- fast rcnn의 rpn을 사용하면 fps에 크게 증가

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2016.png)

[Faster_RCNN_pytorch_notebook_demo.ipynb](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Faster_RCNN_pytorch_notebook_demo.ipynb)

# SSD ?

# Single Shot Multibox Detector

### faster r-cnn의 한계

- 앵커박스 고정적
- 3 network : feature extraction ,  region proposal , classification/bbox regresison
    - 3개가 유기적으로 잘동작하는가?

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2017.png)

- 이러한 한계?

## Feature Pyramid with Default anchors

- 같은 사이즈의 anchor box를 가지고 defalut anchor box로 8*8 feature map과 4*4의 feature map에서는 더 큰 크기의 객체 탐지 가능
    - 이해? → 이러한 컨셈으로 ob detection

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2018.png)

### feature pyramid는 어떻게 만들었는가?

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2019.png)

- 기존의 CNN참조
- Multi scale feature map for detection

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2020.png)

- VGG를 통과해 33*33 feature map 생성
- 중간 feature map들을 연결해서 바로 prediction 수행
    - 앞 layer에서는 4개의 anchor box사용
    - 뒤 layer에서는 6개의 anchor box 사용
- 이 값을 detection per class layer 수행후 NMS 사용해서 mAP 점수 나옴
    - NMS ? Non Maximum Suppersion
        - confidence랑 ioU사용해서 box하나만 남기는 방법
    - mAP: precision -recall의 클래스의 평균점수
- 기존의 faster-rcnn보다 anchorbox보다 더 많은 anchor box 사용 : 300→8732

### Training

- loss f
    - classifcation 과 anchor box의 location 값으로 loss
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2021.png)
    
    - location Loss
        - anchorbox의 중심점 , 넓이 높이의 regreesion 방법 사용
        
        ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2022.png)
        
    - classifcation loss
        - softmax 사용
        
        ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2023.png)
        
- Scale of default boxes
    - 0.2~0.9 사용
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2024.png)
    
    - m은 anchor box의 개수
- default box의 aspect ratio
    - 1,2,3,1/2,1/3
- Hard negative mining
    - background 할때 ground truth label augmenation 이 적음
    - 사람이 쳐놓은 box와 iou가 많이 겹치면 다 ground truth로 봄
    - 따라서 confidence가 굉장히 높은 것만 negative sample로 보기로함
- Data augmentation
    - 0.1 ? patch에 object가 살짝 겹치는것
    - 이러한 것들도 trainig patch로 사용했음

### result

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2025.png)

- 300 vs 512 → 입력사이즈 300*300 , 512 *512

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2026.png)

- 갈수록 줄어드는 feature map
- boundary boxes를 ground truth로 사용했는가?
    - 0.1까지 포함하는 box들을 → 사용했을때 보통 더 좋지만
        - 작은 boundary box를 사용하지만 작은 scale의 이미지일때는 오히려 성능이 떨어지는 결과
- 

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2027.png)

- 300→400으로 올렸을때 small object를 더 잘 detect

# YOLO :You only Look Once

# YOLO inform

# Obj Detection

- Unified ,simple ,,realtime object detection

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2028.png)

- 3단계
    - Resize image
    - Conv
    - Non maxium suppression : NMS → confidence와 ioU을 통해 박스제거

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2029.png)

- 하나의 grid 마다 boudning box2개씩 예측
- class probability map을 생성
- network는 object 전체가 아니라 object part에 대한 분류

## Single Ssscale feature map for detection

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2030.png)

- 입력 고정 → 7*7 feature resolution
- 마지막 7*7이 위 그림에서 보이는 grid가 되는것임
- 마지막의 30d는 ? cordinate : bounding box :4 + classl 예측점수 1

## Training

- Loss
    - object가 있는 greed와 없는 greed loss 두개 나눵서 진행
    
    ![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2031.png)
    
- C : confidence score

### result

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2032.png)

- Real time 알고리즘이 좋다

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2033.png)

- SSD와 Yolo의 싸움

## Yolo v2

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2034.png)

- anchor box를 쓰지 않으면서 성능이 좋다

### error rate

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2035.png)

- grid base가 background 에 대해서 오류를 줄여준다.

# UNet

### Unet - > MiCCAI 2015년 발표

- image segementation in an end-to-end setting
- 적은 annotated image
- semantic ? segmentation

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2036.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2037.png)

- image resolution 줄여가면서 conv수행
- 같은 resolution feature을 upsampling시 concat 수행
- 영상의 바깥부분 padding을 수행하지 않았음
- 주위로 padding을 해주지 않앙 이렇게 됌

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2038.png)

- padding을 사용하지 않았음 → 따라서 2pix씩 줄어듬

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2039.png)

### upcov

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2040.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2041.png)

- 가장자리는 mirroring padding 사용

### 데이터 augmentation

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2042.png)

- 그리드의 위치를 랜덤하게 바꿈

### 논문에서의 방법

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2043.png)

- edge를 강조하도록 mask 생성

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2044.png)

## Warping Error?

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2045.png)

## 세포 트래킹

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2046.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2047.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2048.png)

[UNET_pytorch_Notebook.ipynb](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/UNET_pytorch_Notebook.ipynb)

# DeepLab V3+

### 일반적인 segmentation

- 예전에 나왔지만 아직까지 성능이 좋

### Encoder-Decoder With atrous Separable Conv For Segmentic Image Segmentation

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2049.png)

- background와 사람 구분
- semantic segmentation

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2050.png)

- 오래된 것이지만 아직 좋음

### Network archtitecure imporvments

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2051.png)

- 이게 너무 계산이 너무많당

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2052.png)

- 격자무늬 사이에 빈공간 →
- Point wise conv → 3*3 → 1*1로 바꾸는 conv
- Depthwise conv → 하나의 채널에 대해서 하나의 feature 생성
    - 채널마다 다른 feature 생성하고 넓혀서 생성
- 네트워크 구조
- B가 unet

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2053.png)

- 여기서는 c번 사용

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2054.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2055.png)

# EfficientDet

[effiecientDet_pytorch.ipynb](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/effiecientDet_pytorch.ipynb)

- Scalable and Efficient Object Detection

### detection 과정의 심화과정

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2056.png)

### NAS # nerual arcitecture search

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2057.png)

- 사람이 정해놓은 searcch space . : → performance 측정 → 다시 estimate

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2058.png)

- 네트워크를 이렇게 NAS를 찾는것으로 하면 네트워크가 너무 커짐
- 네트워크를 빨리 찾기위한 network 구성

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2059.png)

- 전체 다하고 최적의 경로만 남김
- 지금까지의 이런방법들을 많이 사용해옴

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2060.png)

- 나스는 사용하기 어려움 .
    - 각 노드를연결하고 pruning 방법도 다 설정해줘야함

### MnasNet

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2061.png)

- 모바일넷에서 발전된 형태

### EfficientNet

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2062.png)

- 5가지 구성으로 이루어짐

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2063.png)

- effiecient net을 detection용으로 구성한것
- cross-scale connetcion
- weighted feature fusion
- compound scaling

### cross-scale connetcion

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2064.png)

- 각 feature resolution들을 어떻게 활용하는지 보여주는 방법

### weighted feature fusion

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2065.png)

- 각 feature를 weight를 줘서 sum을함
- softmax based fusion을 사용함

### Compound Scaling

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2066.png)

- feature resuoltuion을 줄이고 중간의 feature 를 뽑아 BiFPN Layer를 여러번 통과시킴
- 다음 class predction , box prediction을함

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2067.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2068.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2069.png)

### semantic segmentation도 더 좋음

# Focal Loss (RetinaNet , 2017)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2070.png)

- Sampling 하는방법?
- 감마가 커질수록 loss를 패널티를 약하게 줌

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2071.png)

- compound_coef = 위에서 파이, 동그랗게 생긴거. 높게할수록 헤비하면서 좋은 모델을 만드는 것

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2072.png)

- focal loss를 bounding box predictino과 class predictino에 둘다 사용가능

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2073.png)

- compound_coef의 크기에 따라 image size를 다르게 한다.

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2074.png)

- 각기 다른 형태의 fig , 아래 그림을 코드로 나타낸것

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2075.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2076.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2077.png)

- 여기서는 p3, p4, p5 feature값 뽑음
- input에 따라서 앵커박스도 출력

### bifpn?

- 너무기니 코드를 보자
    
    ### code
    
    ```python
    class BiFPN(nn.Module):
        """
        modified by Zylo117
        """
    
        def __init__(self, num_channels, conv_channels, first_time=False, epsilon=1e-4, onnx_export=False, attention=True,
                     use_p8=False):
            """
    
            Args:
                num_channels:
                conv_channels:
                first_time: whether the input comes directly from the efficientnet,
                            if True, downchannel it first, and downsample P5 to generate P6 then P7
                epsilon: epsilon of fast weighted attention sum of BiFPN, not the BN's epsilon
                onnx_export: if True, use Swish instead of MemoryEfficientSwish
            """
            super(BiFPN, self).__init__()
            self.epsilon = epsilon
            self.use_p8 = use_p8
    
            # Conv layers
            self.conv6_up = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            self.conv5_up = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            self.conv4_up = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            self.conv3_up = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            self.conv4_down = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            self.conv5_down = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            self.conv6_down = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            self.conv7_down = SeparableConvBlock(num_channels, onnx_export=onnx_export)
            if use_p8:
                self.conv7_up = SeparableConvBlock(num_channels, onnx_export=onnx_export)
                self.conv8_down = SeparableConvBlock(num_channels, onnx_export=onnx_export)
    
            # Feature scaling layers
            self.p6_upsample = nn.Upsample(scale_factor=2, mode='nearest')
            self.p5_upsample = nn.Upsample(scale_factor=2, mode='nearest')
            self.p4_upsample = nn.Upsample(scale_factor=2, mode='nearest')
            self.p3_upsample = nn.Upsample(scale_factor=2, mode='nearest')
    
            self.p4_downsample = MaxPool2dStaticSamePadding(3, 2)
            self.p5_downsample = MaxPool2dStaticSamePadding(3, 2)
            self.p6_downsample = MaxPool2dStaticSamePadding(3, 2)
            self.p7_downsample = MaxPool2dStaticSamePadding(3, 2)
            if use_p8:
                self.p7_upsample = nn.Upsample(scale_factor=2, mode='nearest')
                self.p8_downsample = MaxPool2dStaticSamePadding(3, 2)
    
            self.swish = MemoryEfficientSwish() if not onnx_export else Swish()
    
            self.first_time = first_time
            if self.first_time:
                self.p5_down_channel = nn.Sequential(
                    Conv2dStaticSamePadding(conv_channels[2], num_channels, 1),
                    nn.BatchNorm2d(num_channels, momentum=0.01, eps=1e-3),
                )
                self.p4_down_channel = nn.Sequential(
                    Conv2dStaticSamePadding(conv_channels[1], num_channels, 1),
                    nn.BatchNorm2d(num_channels, momentum=0.01, eps=1e-3),
                )
                self.p3_down_channel = nn.Sequential(
                    Conv2dStaticSamePadding(conv_channels[0], num_channels, 1),
                    nn.BatchNorm2d(num_channels, momentum=0.01, eps=1e-3),
                )
    
                self.p5_to_p6 = nn.Sequential(
                    Conv2dStaticSamePadding(conv_channels[2], num_channels, 1),
                    nn.BatchNorm2d(num_channels, momentum=0.01, eps=1e-3),
                    MaxPool2dStaticSamePadding(3, 2)
                )
                self.p6_to_p7 = nn.Sequential(
                    MaxPool2dStaticSamePadding(3, 2)
                )
                if use_p8:
                    self.p7_to_p8 = nn.Sequential(
                        MaxPool2dStaticSamePadding(3, 2)
                    )
    
                self.p4_down_channel_2 = nn.Sequential(
                    Conv2dStaticSamePadding(conv_channels[1], num_channels, 1),
                    nn.BatchNorm2d(num_channels, momentum=0.01, eps=1e-3),
                )
                self.p5_down_channel_2 = nn.Sequential(
                    Conv2dStaticSamePadding(conv_channels[2], num_channels, 1),
                    nn.BatchNorm2d(num_channels, momentum=0.01, eps=1e-3),
                )
    
            # Weight
            self.p6_w1 = nn.Parameter(torch.ones(2, dtype=torch.float32), requires_grad=True)
            self.p6_w1_relu = nn.ReLU()
            self.p5_w1 = nn.Parameter(torch.ones(2, dtype=torch.float32), requires_grad=True)
            self.p5_w1_relu = nn.ReLU()
            self.p4_w1 = nn.Parameter(torch.ones(2, dtype=torch.float32), requires_grad=True)
            self.p4_w1_relu = nn.ReLU()
            self.p3_w1 = nn.Parameter(torch.ones(2, dtype=torch.float32), requires_grad=True)
            self.p3_w1_relu = nn.ReLU()
    
            self.p4_w2 = nn.Parameter(torch.ones(3, dtype=torch.float32), requires_grad=True)
            self.p4_w2_relu = nn.ReLU()
            self.p5_w2 = nn.Parameter(torch.ones(3, dtype=torch.float32), requires_grad=True)
            self.p5_w2_relu = nn.ReLU()
            self.p6_w2 = nn.Parameter(torch.ones(3, dtype=torch.float32), requires_grad=True)
            self.p6_w2_relu = nn.ReLU()
            self.p7_w2 = nn.Parameter(torch.ones(2, dtype=torch.float32), requires_grad=True)
            self.p7_w2_relu = nn.ReLU()
    
            self.attention = attention
    
        def forward(self, inputs):
            """
            illustration of a minimal bifpn unit
                P7_0 -------------------------> P7_2 -------->
                   |-------------|                ↑
                                 ↓                |
                P6_0 ---------> P6_1 ---------> P6_2 -------->
                   |-------------|--------------↑ ↑
                                 ↓                |
                P5_0 ---------> P5_1 ---------> P5_2 -------->
                   |-------------|--------------↑ ↑
                                 ↓                |
                P4_0 ---------> P4_1 ---------> P4_2 -------->
                   |-------------|--------------↑ ↑
                                 |--------------↓ |
                P3_0 -------------------------> P3_2 -------->
            """
    
            # downsample channels using same-padding conv2d to target phase's if not the same
            # judge: same phase as target,
            # if same, pass;
            # elif earlier phase, downsample to target phase's by pooling
            # elif later phase, upsample to target phase's by nearest interpolation
    
            if self.attention:
                outs = self._forward_fast_attention(inputs)
            else:
                outs = self._forward(inputs)
    
            return outs
    
        def _forward_fast_attention(self, inputs):
            if self.first_time:
                p3, p4, p5 = inputs
    
                p6_in = self.p5_to_p6(p5)
                p7_in = self.p6_to_p7(p6_in)
    
                p3_in = self.p3_down_channel(p3)
                p4_in = self.p4_down_channel(p4)
                p5_in = self.p5_down_channel(p5)
    
            else:
                # P3_0, P4_0, P5_0, P6_0 and P7_0
                p3_in, p4_in, p5_in, p6_in, p7_in = inputs
    
            # P7_0 to P7_2
    
            # Weights for P6_0 and P7_0 to P6_1
            p6_w1 = self.p6_w1_relu(self.p6_w1)
            weight = p6_w1 / (torch.sum(p6_w1, dim=0) + self.epsilon)
            # Connections for P6_0 and P7_0 to P6_1 respectively
            p6_up = self.conv6_up(self.swish(weight[0] * p6_in + weight[1] * self.p6_upsample(p7_in)))
    
            # Weights for P5_0 and P6_1 to P5_1
            p5_w1 = self.p5_w1_relu(self.p5_w1)
            weight = p5_w1 / (torch.sum(p5_w1, dim=0) + self.epsilon)
            # Connections for P5_0 and P6_1 to P5_1 respectively
            p5_up = self.conv5_up(self.swish(weight[0] * p5_in + weight[1] * self.p5_upsample(p6_up)))
    
            # Weights for P4_0 and P5_1 to P4_1
            p4_w1 = self.p4_w1_relu(self.p4_w1)
            weight = p4_w1 / (torch.sum(p4_w1, dim=0) + self.epsilon)
            # Connections for P4_0 and P5_1 to P4_1 respectively
            p4_up = self.conv4_up(self.swish(weight[0] * p4_in + weight[1] * self.p4_upsample(p5_up)))
    
            # Weights for P3_0 and P4_1 to P3_2
            p3_w1 = self.p3_w1_relu(self.p3_w1)
            weight = p3_w1 / (torch.sum(p3_w1, dim=0) + self.epsilon)
            # Connections for P3_0 and P4_1 to P3_2 respectively
            p3_out = self.conv3_up(self.swish(weight[0] * p3_in + weight[1] * self.p3_upsample(p4_up)))
    
            if self.first_time:
                p4_in = self.p4_down_channel_2(p4)
                p5_in = self.p5_down_channel_2(p5)
    
            # Weights for P4_0, P4_1 and P3_2 to P4_2
            p4_w2 = self.p4_w2_relu(self.p4_w2)
            weight = p4_w2 / (torch.sum(p4_w2, dim=0) + self.epsilon)
            # Connections for P4_0, P4_1 and P3_2 to P4_2 respectively
            p4_out = self.conv4_down(
                self.swish(weight[0] * p4_in + weight[1] * p4_up + weight[2] * self.p4_downsample(p3_out)))
    
            # Weights for P5_0, P5_1 and P4_2 to P5_2
            p5_w2 = self.p5_w2_relu(self.p5_w2)
            weight = p5_w2 / (torch.sum(p5_w2, dim=0) + self.epsilon)
            # Connections for P5_0, P5_1 and P4_2 to P5_2 respectively
            p5_out = self.conv5_down(
                self.swish(weight[0] * p5_in + weight[1] * p5_up + weight[2] * self.p5_downsample(p4_out)))
    
            # Weights for P6_0, P6_1 and P5_2 to P6_2
            p6_w2 = self.p6_w2_relu(self.p6_w2)
            weight = p6_w2 / (torch.sum(p6_w2, dim=0) + self.epsilon)
            # Connections for P6_0, P6_1 and P5_2 to P6_2 respectively
            p6_out = self.conv6_down(
                self.swish(weight[0] * p6_in + weight[1] * p6_up + weight[2] * self.p6_downsample(p5_out)))
    
            # Weights for P7_0 and P6_2 to P7_2
            p7_w2 = self.p7_w2_relu(self.p7_w2)
            weight = p7_w2 / (torch.sum(p7_w2, dim=0) + self.epsilon)
            # Connections for P7_0 and P6_2 to P7_2
            p7_out = self.conv7_down(self.swish(weight[0] * p7_in + weight[1] * self.p7_downsample(p6_out)))
    
            return p3_out, p4_out, p5_out, p6_out, p7_out
    
        def _forward(self, inputs):
            if self.first_time:
                p3, p4, p5 = inputs
    
                p6_in = self.p5_to_p6(p5)
                p7_in = self.p6_to_p7(p6_in)
                if self.use_p8:
                    p8_in = self.p7_to_p8(p7_in)
    
                p3_in = self.p3_down_channel(p3)
                p4_in = self.p4_down_channel(p4)
                p5_in = self.p5_down_channel(p5)
    
            else:
                if self.use_p8:
                    # P3_0, P4_0, P5_0, P6_0, P7_0 and P8_0
                    p3_in, p4_in, p5_in, p6_in, p7_in, p8_in = inputs
                else:
                    # P3_0, P4_0, P5_0, P6_0 and P7_0
                    p3_in, p4_in, p5_in, p6_in, p7_in = inputs
    
            if self.use_p8:
                # P8_0 to P8_2
    
                # Connections for P7_0 and P8_0 to P7_1 respectively
                p7_up = self.conv7_up(self.swish(p7_in + self.p7_upsample(p8_in)))
    
                # Connections for P6_0 and P7_0 to P6_1 respectively
                p6_up = self.conv6_up(self.swish(p6_in + self.p6_upsample(p7_up)))
            else:
                # P7_0 to P7_2
    
                # Connections for P6_0 and P7_0 to P6_1 respectively
                p6_up = self.conv6_up(self.swish(p6_in + self.p6_upsample(p7_in)))
    
            # Connections for P5_0 and P6_1 to P5_1 respectively
            p5_up = self.conv5_up(self.swish(p5_in + self.p5_upsample(p6_up)))
    
            # Connections for P4_0 and P5_1 to P4_1 respectively
            p4_up = self.conv4_up(self.swish(p4_in + self.p4_upsample(p5_up)))
    
            # Connections for P3_0 and P4_1 to P3_2 respectively
            p3_out = self.conv3_up(self.swish(p3_in + self.p3_upsample(p4_up)))
    
            if self.first_time:
                p4_in = self.p4_down_channel_2(p4)
                p5_in = self.p5_down_channel_2(p5)
    
            # Connections for P4_0, P4_1 and P3_2 to P4_2 respectively
            p4_out = self.conv4_down(
                self.swish(p4_in + p4_up + self.p4_downsample(p3_out)))
    
            # Connections for P5_0, P5_1 and P4_2 to P5_2 respectively
            p5_out = self.conv5_down(
                self.swish(p5_in + p5_up + self.p5_downsample(p4_out)))
    
            # Connections for P6_0, P6_1 and P5_2 to P6_2 respectively
            p6_out = self.conv6_down(
                self.swish(p6_in + p6_up + self.p6_downsample(p5_out)))
    
            if self.use_p8:
                # Connections for P7_0, P7_1 and P6_2 to P7_2 respectively
                p7_out = self.conv7_down(
                    self.swish(p7_in + p7_up + self.p7_downsample(p6_out)))
    
                # Connections for P8_0 and P7_2 to P8_2
                p8_out = self.conv8_down(self.swish(p8_in + self.p8_downsample(p7_out)))
    
                return p3_out, p4_out, p5_out, p6_out, p7_out, p8_out
            else:
                # Connections for P7_0 and P6_2 to P7_2
                p7_out = self.conv7_down(self.swish(p7_in + self.p7_downsample(p6_out)))
    
                return p3_out, p4_out, p5_out, p6_out, p7_out
    ```
    

# Swin Transformer : 70%

- 트랜스포머 기반의 논문들은 CNN,등을 사용하지 않아 방법이 다름
- NLP의 task

[swin_TF_Notebook.ipynb](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/swin_TF_Notebook.ipynb)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2078.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2079.png)

- transformer

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2080.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2081.png)

- vit의 성능

## vIT이란?

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2082.png)

- 영상을 patch로 쪼갬
- 쪼개서 vector를 만들고 이미지 patch에 따라서 position encoding 해준후
- feature 생성
- 어떻게 영상의 spacital 정보를 고려할수있는가>??

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2083.png)

- VIT에서는 patch에서의 관계를
- Swin에서는 잘게쪼개고 , local 과 global의 feature를 다 연관성을 지음
- 2번째 window shiffting

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2084.png)

- patch의합 → local window 를 바꿔가면서 feature를 다양하게 추출?

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2085.png)

- LN : layer normalization
- W-MSA : Window Multihead Self-Attention
- SW-MSA : Shifted Window MSA

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2086.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2087.png)

# Tiny Face Methods and Result

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2088.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2089.png)

- 5가지 face detection 방법

## Context information to find small faces

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2090.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2091.png)

# MaskRCNN [ ROI pooling ]

## History

## RCNN : Region-based Conv Network

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2092.png)

- 2번 → 고전적인 방법
- wrap size= > fix size로 구분하고 cnn

## Fast R-CNN

- 방법 : network를 딥러닝으로 바꿈
- bounding box를 regressor하는 방식 사용
- ROI를 위방법으로 보정
- SS 기법사용
- ROI Pooling layer

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2093.png)

## Faster R-CNN

- SS를 대체하는 Region proposal network with anchor box
- 이 박스들을 뒷단에서 regressor

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2094.png)

## Mask R-CNN :2017

- 방법 : insstance segmentation
- Proposed Method 기법
    - Segmentation mask prediction
    - ROI Align

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2095.png)

1. mask 예측 
2. Conv 중간에서 cls 예측하는 box 뽑을수있음

## 각기 다른 모델로 ResNet/FPN

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2096.png)

- 아래 흰부분은 각 클래스에 대한 마스크를 예측
- 오른쪽은 ROI따는 부분을 미리 먼저 따고 수행

## ROI Align :****Region of interest****

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2097.png)

- ROI 영역의 한 픽셀값을 새롭게 정의
- 위그림의 ROI와 다르다. 해당 Postion 의 위치좌표를 사용해서 주변의 pixel
- [ ]  왜 ROI를 쓰는지 더 잘알아보기

## Mask RCNN 성능이좋아 유명해짐

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2098.png)

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%2099.png)

- object detection

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%20100.png)

- key point detection : 사람의 key point

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%20101.png)

- Multitask learning

![Untitled](Object%20Detection%20&%20Segmentation%202035c9ad32d7428798123567ba9573ed/Untitled%20102.png)

- mask only가 오히려 좋다
- 멀티테스크 진행시켰을시 더 안좋알수도 있음