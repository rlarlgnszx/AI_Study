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
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F329da6e3-aa73-4ecb-a5f7-ea3b55bf8c20%2FUntitled.png?table=block&id=e18f7593-d60f-4138-b73f-3d95705a85da&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=770&userId=&cache=v2)
    
- 단층 퍼셉트론과 다층 퍼셉트론
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F652ede24-e649-4db7-a54a-3bec40f9900c%2FUntitled.png?table=block&id=b466e1a5-0202-43b1-b9d4-7559bf2b146e&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1060&userId=&cache=v2)
    
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

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1b22be5b-852b-4527-9236-d8a27b5eb01b%2FUntitled.png?table=block&id=412ceb57-0d92-4f98-9ad5-6054d6e10725&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1370&userId=&cache=v2)

- 객체 탐지와 비슷하지만 객체 탐지에는 경계 상자가 필요
- 객체 분할에서는 정확한 픽셀 필요
    - Mask R-CNN이 있음
- ResNet , U-Net
- 객체 분할의 2가지 종류
    - 인스턴스 분할
    - 시맨틱 분할

### Face Recognition

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F57b64dac-9c7f-40d5-a93f-31bd33a72f6d%2FUntitled.png?table=block&id=2d954660-749b-48f4-86dc-4e8aa6c6db42&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1460&userId=&cache=v2)

### Image Synthesis

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9dd40fda-a779-4dd4-95a8-faf1c18720e0%2FUntitled.png?table=block&id=65f1adf4-1eaa-4f61-9ea8-40daa5e289ec&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- 이미지 합성은 데이터가 충분하지 않은 경우에 선택됩니다.
- 데이터를 사용하여 더 많은 데이터를 생성할때 사용
- 대부분 GANs # 생성적 적대 네트워크 라고 부릅니다.
- 합성곱신경망에 텍스트나 이미지 제공
    - 특정 이미지와 반대되는것 혹은 이미지와 같은 것

### 왜 Computer vision이 어려운가?

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffc5368ac-6b85-4b5d-afb1-d62ca6a62a63%2FUntitled.png?table=block&id=7a90dfe8-e341-4052-b649-28b4495805b4&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1620&userId=&cache=v2)

- 이러한 다양성이 있어야 한다.
    - 조명변화 , 대비변화 ,시점변화 등

## 이전에는 다양한 feature 정의해서 approaches

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0229c0f4-011a-4bc1-b3d1-400557d22a2f%2FUntitled.png?table=block&id=ad2f90fe-0962-46c9-bb7e-77b5fe5de054&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=960&userId=&cache=v2)

- 전통 접근방식

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa3cd2719-7184-4a21-8015-2a3c5a95b50b%2FUntitled.png?table=block&id=9a7582a4-a7ab-4cde-9a30-bd2e2ada3729&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1360&userId=&cache=v2)

- facial keypoint feature

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F152810e3-00b3-4933-a0b8-fbeaa6da5563%2FUntitled.png?table=block&id=c137cfeb-c51c-46a0-a1fe-8eda781921a5&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1650&userId=&cache=v2)

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

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9c6c4ca6-137d-41ff-b2e0-426e057ec850%2FUntitled.png?table=block&id=c40c5bbb-cf67-4e33-b41b-fb8f21d89184&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- 특징 자동 추출 지역 CNN
    - feature 자동적으로 추출
- regular classifier
    - feature를 가지고 분류하는 것
- 위 아래 그림은 fully connected layer 계산
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd45f16f8-4773-461a-bfc5-5c79524d5381%2FUntitled.png?table=block&id=f3202e4b-e957-4c7e-ad74-5a7e47fbed52&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1600&userId=&cache=v2)
    
- 
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffb619773-434a-454e-8246-a4f2bd5a3190%2FUntitled.png?table=block&id=f98e54c1-1fdd-4887-9bf6-1401434a0a36&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
    
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
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff31b2407-ea6d-4a4a-899e-6d8c92e2cafd%2FUntitled.png?table=block&id=d8ef466e-0448-43bc-bc5c-0f0340dd0a70&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
    
    - oupsize의 convolutioin map을 알기위한 식
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff5148cab-4f59-48d0-be02-d3085ae4cdc2%2FUntitled.png?table=block&id=b82247ef-0fd0-4501-b1cc-0a6837bfcd3b&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1470&userId=&cache=v2)
    
    - 패딩 stride중요
    
    ### 그러나 CNN 은 Translation/Rotation/Scale Invariance에 대해서 예측 어렵다.
    
    ## Pooling Layers 은 Local Invariance에 좋음
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F01e2ca63-e077-4597-af7f-8d08d7944f5b%2FUntitled.png?table=block&id=da3a103a-6f4d-4a6e-aa74-1e179b0dbe9c&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
    
    - feature 특징 추출해서 max값을 찾거나 mean값을 찾거나
    
    ## Backpropagation
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb8e0fb1d-63ec-405f-a3ee-0db70a3cc570%2FUntitled.png?table=block&id=39cb2070-c658-4f19-bf98-630c22b93969&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
    
    - 수학에서의 multivariable chain rule
    - 손실 계산하는 방법
    

# Numpy로 RNN 구현

[numpy_rnn.ipynb](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bb358528-7701-4318-b0d8-dcdfa7eb73e6/numpy_rnn.ipynb)

- 위 코드로 구현

# LSTM

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Feded4b7a-b7aa-4998-b900-ad9b6995116e%2FUntitled.png?table=block&id=e1377a6e-7fb0-4da3-9fe7-afd1854fc98d&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- 위와 비슷한 구조
- 원래는 hiddenstate가 다음 상태의 x의 입력과 함께 입력으로 들어감
- 마지막 단어를 기반으로 다음 단어를 예측하려고 함
- 긴 시퀀스를 제공하면 vanishing gradient문제
    - 학습 저해

## Long Term Memory = > LSTM

- 어떻게? standard RNN

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff9595808-0870-4e68-9575-3f4e3afcf8e3%2FUntitled.png?table=block&id=d7cb3aa8-2ee0-47dd-97f7-cc147f3f9b51&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- 다음과 같은 방식으로 메모리 저장

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3aefc6c0-eecf-4389-b971-d258066d9e9c%2FUntitled.png?table=block&id=44c7b427-2173-4864-83f1-0d4f25d24735&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1460&userId=&cache=v2)

- 특정 데이터가 있다고 가정
    - 새로 가져와야 하는 데이터가 있음
    - Gate 메카니즘 사용
- forget gate
    - 우리에게 필요하지 않은 정보를 잊어버리게함
    - 2가지 활성화 함수 존재
    - sigmod , tanh
- forget gate후에 oupgate와 memory cell ouput에 2가지로 전달

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0ef0e950-6355-4549-8f64-a9ece3cc01ed%2FUntitled.png?table=block&id=03b431f9-4d51-41c4-bff9-f421f29e099d&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

1. keep과 write에 들어온정보를 memory에 저장하는데 이때 memory에는 forget gate로써 필요하지 않은 정보 forget

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Feb1db38d-3816-491e-927c-a46d7484eaf8%2FUntitled.png?table=block&id=01c0fd41-791a-4ee9-aaff-a6d10260b239&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=860&userId=&cache=v2)

- xt : 지금의 입력
- ht-1 : 이전 cell의 hidden state
- cell state? :
    - ht1 ht-1 ,ht+1
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff2d6ba65-7707-4212-aa5f-cffd37c56767%2FUntitled.png?table=block&id=5a605cbd-69b2-46ca-b39d-9cb72e92cc08&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=670&userId=&cache=v2)
        
- Gates?
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffb867489-82a6-493c-bfed-9efa817bf91d%2FUntitled.png?table=block&id=e88ad40c-4ec4-483a-b91e-f01e54bed7f9&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=580&userId=&cache=v2)
    
    - 활성화 함수 또는 시그모이드 레이어 함수
        - LSTM에서는 대부분 시그모이드로 사용

## Forget Gate Layers

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7e4c58ff-fc82-4404-b0f2-d20e8d052d46%2FUntitled.png?table=block&id=6e4230a3-499f-48aa-976b-15bf90ca3469&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- 마지막 셀의 hiddenstate에서온 local context와 현재의 입력단어 xt를 갖게 됌
    - 둘이 bias추가 해서 sigmoid로 계산한다면 마지막 셀과 현재 있는 cell의 중요하지 않은 정보를 잊어버림

## Input Gate Layers

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0dad5415-b03f-4fd6-98f7-bcb78bb0b771%2FUntitled.png?table=block&id=313eca37-2422-4583-a3dc-8f5a03de317c&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- it : Input state
    - sigmoid 사용
- Ct : Cell state
    - tanh 사용
- forget gate와 전체적인 과정은 같음

## Current state

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb0b1a19d-e2df-469f-9ede-0dd8e612c7a1%2FUntitled.png?table=block&id=fe9fa7cd-77af-4895-9708-bd68b28384b4&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- 여기서는 ct 는 globle context 유지
    - 무슨말일까?
- ht 는 local context 정보

## Ouput Layers

![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffd514bdf-44bb-4a36-95c0-136c08562ad1%2FUntitled.png?table=block&id=56e298bf-d33e-4756-bd61-23b2b1d30738&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)

- outlayer에는 local context 정보 존재 : ht
    - local context는 이 셀의 Xt에서 처리된 모든 정보
- xt의 입력과 ht-1의 입력을 정리하고 얻은 정보는 Ct에 저장

# Transformers

- Attention
- Encoder Decoder
- Transformer

## RNN의 문제점

- 병렬처리하기 어렵다
- 베니싱 문제
- 1d CNN으로 해결 할수 있다
    - CNN은 귀납편향 존재
    - 적은 데이터셋이 있을때 잘 동작
    - 하지만 복잡한 작업일때 좋은 결과 X
    - 1차 CNN으로는 어렵다

## Self Attention # multihead attetion

- self attention?
    - 각 단어를 처리하는 동안 입력 시퀀스의 다른 위치를 볼수 있다
    - 특정 단어에 대해 나은 encoding 값 가능
    
    ### step 1
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6dd45526-92fb-4964-8593-7d60f9d4ae72%2FUntitled.png?table=block&id=c5c60345-b82c-48ac-b24b-2cf3f931fe7a&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1120&userId=&cache=v2)
    
    - 쿼리,키,value 벡터 만들기
    - 입력에 대한 쿼리 키 벨류
    - 쿼리?
        - 우리가 찾고있는 단어에 관한 것
        - 주가 되는 단어 , query가 key의 단어들고 ㅏ어떤 연관성이 있는지 모두 비교하게 되는 단어
        - 특정 검색을 쿼리라고 한다.
            - 구글검색은 검색에 대한 여러 링크들을 보여줌
    - 키
        - 특정 검색에 대한 키가 있고 키에는 해당 링크가 존재
        - 링크들의 집합 즉 정보를 제공하는 단어들의 집
    - value
    
    ### step 2
    
    - Score 계산
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb32a7f05-ecf4-4882-afb9-a3413ee7be10%2FUntitled.png?table=block&id=1b4eb71b-d230-42e0-91e9-5a74a24054a7&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1050&userId=&cache=v2)
    
    - 특정 위치에 단어를 인코딩할때 특정 문장 입력의 다른 부분에 얼마나 많은 초점이 맞춰지는지 나타낸 점수
        - 키와 커리의 내적곱을 해서 score 얻는다.
    
    ### step 3
    
    - score를 키벡터 차원의 제곱근으로 나누어 안정적인 gradient 얻음
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F55940f10-442b-498a-97d8-551d4e6e9089%2FUntitled.png?table=block&id=1b943c48-a7b5-4f0d-9705-5d5ef14320b9&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1050&userId=&cache=v2)
    
    - 위에서 스코어는 112였는데 쿼리차원이 8이라고 한다면 8로 나누고 제곱근 취하고 softmax취하면 ?
        - 각 단어의 확률이 나온다.
        - 위 확률 0.88~0.12에서 나온 값은 0.88 높은 값이 output sequence에 속하고 출력으로 내보낸다
    
    ### step 6
    
    - 소프트맥스 계산하고 나온 후 가중치 벡터의 합의 관한 것
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2a8ff433-1e4a-47a0-9ec8-e4f58581ff99%2FUntitled.png?table=block&id=ed994ba8-d6d2-4c07-a9a3-941c08be6587&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=920&userId=&cache=v2)
    
    - 가중치의 합계가 있다.
        - softmax의 값이 높은것, output sequence와  연결되는 단어를 value곱합
        - 즉 그림과 같이 softmax * value를 곱하고 나온 vector의 합 계산
        
        [**그림 링크**](https://jalammar.github.io)
        
        [***`transfomer 그림 설명 site`***](https://jalammar.github.io/illustrated-transformer/)
        
    
    ## Self-attention
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0f2cc3ce-d535-4958-8bfc-2dba10c4abe2%2FUntitled.png?table=block&id=92ff966b-b2a6-4902-bc14-b46a8a80f6ec&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
    
    - b는 편향이다.
        - 병렬적으로 계산된다.
        - 병렬 시퀀스
    - 맨처음 a를 구한다.
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb2834c99-934b-4620-8b4a-9f01ab48ef41%2FUntitled.png?table=block&id=2dd07dc7-dcbe-4c03-ade9-281f68bc422c&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1460&userId=&cache=v2)
        
        - a는 W가중치와 x1(특정단어)의 곱으로 계산된다.
            - w는 가중치합
            - x는 특정단어를 포함하는 행렬?
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7b571f84-21c6-4f98-b226-a93360c3625f%2FUntitled.png?table=block&id=ca488d11-51f3-41a4-a2cc-7bf8749491e0&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1670&userId=&cache=v2)
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7cf7a7ac-3591-49d3-96c0-60082c8724b3%2FUntitled.png?table=block&id=6dd54a86-8406-4fbe-8d45-416b74b566f0&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=480&userId=&cache=v2)
        
        - 가중치합에 ai를 곱해서 query,key,value vector 생성
        
        ### 예시
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F80c9c4d3-b666-4b93-b52e-0ccfcd18790e%2FUntitled.png?table=block&id=50403d65-3305-4a9b-95c4-297b1810fc8d&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
        
        - a1,i 에 대해서 dot-product값 구하고 dimention값으로 나누고
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2f29e5e5-1700-4014-a7d3-72439bf51f65%2FUntitled.png?table=block&id=bad6c8e3-30f0-4628-b520-2f257da0d567&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1670&userId=&cache=v2)
        
        - softmax 취하고
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd6ae0fdb-9b4b-454c-b7be-5dcea94bf78f%2FUntitled.png?table=block&id=ef589288-b413-4a88-8542-7b28b9f68b64&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc5e3035d-3e40-448a-8023-c5416b199776%2FUntitled.png?table=block&id=10e27b4b-1927-4307-85fa-008dba5d3c34&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=520&userId=&cache=v2)
        
        - value값 가져온다.
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6c3b8997-1412-4262-900a-b1b9d9fad3bf%2FUntitled.png?table=block&id=747279fc-fb51-4289-8d0a-5cf8a87d461b&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1660&userId=&cache=v2)
        
        - 이렇게 나온 값으로 b1 출력
            - b1은 단어일수도 있고 sequence 일수도 있다.
            
            ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0f2cc3ce-d535-4958-8bfc-2dba10c4abe2%2FUntitled.png?table=block&id=f9433d3d-155c-437d-8c22-0bda1fff3059&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1700&userId=&cache=v2)
            
        - 이렇게 그러면 순서대로 b1,b2구할수있다.
        
        ### 요약
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3b6883de-52a8-4209-9d09-b7aa8cb0b84c%2FUntitled.png?table=block&id=2dee42c3-89d2-4a98-9a83-c4da1c245e25&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1650&userId=&cache=v2)
        
        ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8ca8367c-af55-450e-bc08-b2fabe07cd36%2FUntitled.png?table=block&id=f7aa9259-7419-47b1-86c2-9ce97a2a27e9&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1620&userId=&cache=v2)
        
    
    ## Multi-head Self-attention
    
    - 차이점은 qi를 삽입하는 것
    - 그러나 qi에서 n가지 행렬이 더생김
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffeef8240-dc6c-43ea-8d22-d17b1f7bf09d%2FUntitled.png?table=block&id=763499bc-b19e-4103-a32d-faa3e41be402&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1620&userId=&cache=v2)
    
    - 이 예시는 2 head example
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F4d5d18b9-eb66-420f-8315-17f62e7b496b%2FUntitled.png?table=block&id=618f2cdc-7bc4-4d92-a0a4-55036cff106c&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1610&userId=&cache=v2)
    
    - 위처럼 bi가 아니라 bi1,bi2를 얻을수있음
    - 나머지는 동일
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F65c18d9f-a6f0-4b70-966e-8234a4885d7c%2FUntitled.png?table=block&id=16ec91e5-a0b3-49bd-9a3a-6bd259746d29&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1330&userId=&cache=v2)
    
    ## Positinal Encoding
    
    - attention에는 위치정보가 없다.
    - 특정한 시퀀스 혹은 단어가 timestamp 어디의 위치하는지 모름
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa91aa0ac-da06-4c2a-ad06-af12dad718c1%2FUntitled.png?table=block&id=bdb8c312-bed2-4ac5-a458-29a280419de9&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=510&userId=&cache=v2)
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F76ea2edc-94e1-4a98-b39e-4b81377b4786%2FUntitled.png?table=block&id=da050c79-12e6-455b-87c0-bf64ce48ed74&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1300&userId=&cache=v2)
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F08c82dbc-de15-428f-8c85-7da8355fd161%2FUntitled.png?table=block&id=768c85bf-38b1-434b-bc20-88c9e33463eb&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1170&userId=&cache=v2)
    
    - 특정 단어가 처음의 위치에 오는지!
    
    ## Seq2Seq with Attention
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2741602d-15da-456b-82c8-480872b688ba%2FUntitled.png?table=block&id=6a43e857-0709-4fc1-9bd2-869005073d5b&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1570&userId=&cache=v2)
    
    - encoder :  self 나 multi-head attention 가능
    - encoder 의 output값이 decoder의 값으로 들어감
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F76dfe548-55d2-4084-b13a-54dcb15b60d4%2FUntitled.png?table=block&id=16e424fc-091c-4620-852c-ba2bf535ca88&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1490&userId=&cache=v2)
    
    ## self attention Visualization
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fec7b3931-1eb2-4ad0-a935-dfb17630c073%2FUntitled.png?table=block&id=e9f2634d-d28b-4250-81cf-dffab0ce2bc0&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1640&userId=&cache=v2)
    
    - 각 단어가 연관된 확률
    - 
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F4a980f87-bd0b-4719-b505-7f509b11527d%2FUntitled.png?table=block&id=4f3b6f03-fb4b-4531-8ab1-aadbdac443d9&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1660&userId=&cache=v2)
    
    ## Multi-head attention visualization
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F28d518d4-1d87-4751-9d90-5f2aac9d5af5%2FUntitled.png?table=block&id=924b618e-df8c-4503-9b67-16c208b0f4ff&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=1260&userId=&cache=v2)
    
    ![Untitled](https://crystalline-paper-4ea.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa641b089-f004-40d9-a90d-d8cb0737f3a6%2FUntitled.png?table=block&id=54b7fc41-ec47-41b6-84cd-91c7afc16fcc&spaceId=e84306da-ad8a-4e53-9a55-417e8babd537&width=760&userId=&cache=v2)

