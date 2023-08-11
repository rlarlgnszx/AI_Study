# NN Basic

# 순차 데이터

- 순차적 영상데이터 , 순차적 오디오 데이터
- 순차모델이 필요한 이유?
    - 기존의 신경망이 처리하지 못하는 이유
- CNN , Fully connected , RNN ,Transformer등이 있다.
    - RNN
        - GRU
        - LSTM
    - Transformer
        - Encoder
        - Decoder

### 해결할수 있는 문제

- One to  One
- One to Many
- Many to One
- Many to Many
    - 기계번역 ,언어번역등

# Feed Forward NN

- feed forward NN이란?
    - 최초로 도입된 신경망
    - 순환을 형성하지 않는 신경망
    - 따라서 루프가 없음
    - 반대는 순환 신경망 RNN
- 사용성 :
    - 데이터의 독립변수간의 관계 학습 가능
    - A의 변수 B에 영향을 미치는 경우
    - “변수간의 관계”
    - 순차적 X이고 시간에 종속되지 않는 경우에 피드포워드 # 지도학습
        - 단방향 신호 송신 등
        - NO loop!!!!!
    - 컴퓨터 비젼에서도 사용
    - NLP는 피드포워드 퍼포먼스 나쁨
    - 

    ![image](https://crystalline-paper-4ea.notion.site/image/https://s3-us-west-2.amazonaws.com/secure.notion-static.com/329da6e3-aa73-4ecb-a5f7-ea3b55bf8c20/Untitled.png)
- 단층 퍼셉트론과 다층 퍼셉트론
    
    ![image](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/652ede24-e649-4db7-a54a-3bec40f9900c/Untitled.png)
    
- **한계 :**
    - 순차데이터와 관련해서 퍼포먼스 정말 나쁨
    - 시계열 Data NLP에 대해서 나쁨
    - 거대한 아키텍쳐 덕분에
        - Lots of 파라미터와 너무 많은 데이터필요함
        - vanishing gradient 존재
    - CNN은 귀납적 편향을 가지기 때문에 작은 데이터로 효율적으로 사용 가능 그러나 피드포워드는 불가
    

# Numpy 로 FFN 구현 # code

- 기본 퍼셉트론
- 이진 분류 일때
- sigmoid #
    - 출력을 0또는 1로 제한
    - 따라서 이진 분류에서 활용

# CNN

# CNN?

- 이미지 분류에 주로 사용
- 합성곱 신경망
- 이미지 분류에 처음 사용

### Object Detection

### Object Segmentation

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1b22be5b-852b-4527-9236-d8a27b5eb01b/Untitled.png)

- 객체 탐지와 비슷하지만 객체 탐지에는 경계 상자가 필요
- 객체 분할에서는 정확한 픽셀 필요
    - Mask R-CNN이 있음
- ResNet , U-Net
- 객체 분할의 2가지 종류
    - 인스턴스 분할
    - 시맨틱 분할

### Face Recognition

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57b64dac-9c7f-40d5-a93f-31bd33a72f6d/Untitled.png)

### Image Synthesis

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9dd40fda-a779-4dd4-95a8-faf1c18720e0/Untitled.png)

- 이미지 합성은 데이터가 충분하지 않은 경우에 선택됩니다.
- 데이터를 사용하여 더 많은 데이터를 생성할때 사용
- 대부분 GANs # 생성적 적대 네트워크 라고 부릅니다.
- 합성곱신경망에 텍스트나 이미지 제공
    - 특정 이미지와 반대되는것 혹은 이미지와 같은 것

### 왜 Computer vision이 어려운가?

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc5368ac-6b85-4b5d-afb1-d62ca6a62a63/Untitled.png)

- 이러한 다양성이 있어야 한다.
    - 조명변화 , 대비변화 ,시점변화 등

## 이전에는 다양한 feature 정의해서 approaches

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0229c0f4-011a-4bc1-b3d1-400557d22a2f/Untitled.png)

- 전통 접근방식

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a3cd2719-7184-4a21-8015-2a3c5a95b50b/Untitled.png)

- facial keypoint feature

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/152810e3-00b3-4933-a0b8-fbeaa6da5563/Untitled.png)

- 센터링 엔 pixel 추출

### 위에 공통적인 방식은 손으로 추출한 feature

### CNN에서는 사람이 필요하지 않음

- 자체적으로 feature를 찾음
- 귀납적 편향 존재

### CNN

- 사람손글씨 판별가능
- 역전파 사용 #1989년에 사용
    - loss 계산 가능
    - 가중치 update 가능

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9c6c4ca6-137d-41ff-b2e0-426e057ec850/Untitled.png)

- 특징 자동 추출 지역 CNN
    - feature 자동적으로 추출
- regular classifier
    - feature를 가지고 분류하는 것
- 위 아래 그림은 fully connected layer 계산
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d45f16f8-4773-461a-bfc5-5c79524d5381/Untitled.png)
    
- 
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fb619773-434a-454e-8246-a4f2bd5a3190/Untitled.png)
    
    - 첫번째로 32*32 그림이 들어온다
        - 6@ → 6*6 filter를 써서 28*28
        - 다시 6*6 filter를 적용하면 14*14 가 된다.
    
    ### CNN의 Main Concepts
    
    - 피쳐맵의 단일 요소가 작은 픽셀 패치에 연결되는 Sparse-connectivity
    - Parameter-sharing
        - 6*6 → 6개의 feature특징
    
    ### Weight Sharing
    
    - 가중치 공유는 변환 크기를 사용하여 마지막 이미지에서 정보 혹은 픽셀 정보를 추출하는 것
    - 그 특젖ㅇ 가중치는 다른 특징의 임베딩
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f31b2407-ea6d-4a4a-899e-6d8c92e2cafd/Untitled.png)
    
    - oupsize의 convolutioin map을 알기위한 식
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f5148cab-4f59-48d0-be02-d3085ae4cdc2/Untitled.png)
    
    - 패딩 stride중요
    
    ### 그러나 CNN 은 Translation/Rotation/Scale Invariance에 대해서 예측 어렵다.
    
    ## Pooling Layers 은 Local Invariance에 좋음
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/01e2ca63-e077-4597-af7f-8d08d7944f5b/Untitled.png)
    
    - feature 특징 추출해서 max값을 찾거나 mean값을 찾거나
    
    ## Backpropagation
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b8e0fb1d-63ec-405f-a3ee-0db70a3cc570/Untitled.png)
    
    - 수학에서의 multivariable chain rule
    - 손실 계산하는 방법
    

# Numpy로 RNN 구현

[numpy_rnn.ipynb](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bb358528-7701-4318-b0d8-dcdfa7eb73e6/numpy_rnn.ipynb)

- 위 코드로 구현

# LSTM

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eded4b7a-b7aa-4998-b900-ad9b6995116e/Untitled.png)

- 위와 비슷한 구조
- 원래는 hiddenstate가 다음 상태의 x의 입력과 함께 입력으로 들어감
- 마지막 단어를 기반으로 다음 단어를 예측하려고 함
- 긴 시퀀스를 제공하면 vanishing gradient문제
    - 학습 저해

## Long Term Memory = > LSTM

- 어떻게? standard RNN

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9595808-0870-4e68-9575-3f4e3afcf8e3/Untitled.png)

- 다음과 같은 방식으로 메모리 저장

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3aefc6c0-eecf-4389-b971-d258066d9e9c/Untitled.png)

- 특정 데이터가 있다고 가정
    - 새로 가져와야 하는 데이터가 있음
    - Gate 메카니즘 사용
- forget gate
    - 우리에게 필요하지 않은 정보를 잊어버리게함
    - 2가지 활성화 함수 존재
    - sigmod , tanh
- forget gate후에 oupgate와 memory cell ouput에 2가지로 전달

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0ef0e950-6355-4549-8f64-a9ece3cc01ed/Untitled.png)

1. keep과 write에 들어온정보를 memory에 저장하는데 이때 memory에는 forget gate로써 필요하지 않은 정보 forget

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eb1db38d-3816-491e-927c-a46d7484eaf8/Untitled.png)

- xt : 지금의 입력
- ht-1 : 이전 cell의 hidden state
- cell state? :
    - ht1 ht-1 ,ht+1
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f2d6ba65-7707-4212-aa5f-cffd37c56767/Untitled.png)
        
- Gates?
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fb867489-82a6-493c-bfed-9efa817bf91d/Untitled.png)
    
    - 활성화 함수 또는 시그모이드 레이어 함수
        - LSTM에서는 대부분 시그모이드로 사용

## Forget Gate Layers

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e4c58ff-fc82-4404-b0f2-d20e8d052d46/Untitled.png)

- 마지막 셀의 hiddenstate에서온 local context와 현재의 입력단어 xt를 갖게 됌
    - 둘이 bias추가 해서 sigmoid로 계산한다면 마지막 셀과 현재 있는 cell의 중요하지 않은 정보를 잊어버림

## Input Gate Layers

![Image](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0dad5415-b03f-4fd6-98f7-bcb78bb0b771/Untitled.png)

- it : Input state
    - sigmoid 사용
- Ct : Cell state
    - tanh 사용
- forget gate와 전체적인 과정은 같음

## Current state

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b0b1a19d-e2df-469f-9ede-0dd8e612c7a1/Untitled.png)

- 여기서는 ct 는 globle context 유지
    - 무슨말일까?
- ht 는 local context 정보

## Ouput Layers

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd514bdf-44bb-4a36-95c0-136c08562ad1/Untitled.png)

- outlayer에는 local context 정보 존재 : ht
    - local context는 이 셀의 Xt에서 처리된 모든 정보
- xt의 입력과 ht-1의 입력을 정리하고 얻은 정보는 Ct에 저장

# Transformers
