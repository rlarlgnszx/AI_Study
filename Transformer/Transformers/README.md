# Transformer

- 자연어 분야에서 소개된 것중 가장 중요한 아키텍쳐
- 이미지 비젼 , 프로세싱에도 사용됌
- 이전에 가지고 있던 vanishing gradient & exploding Gradient 문제 해결

## 기존 RNN
![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled.png?raw=true)

- RNN 응용케이트
    - 기계번역
    - 요약
    - 질문응답, 대화모델링 ,자동완성등
- RNN feedforward

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%201.png?raw=true)

- simple RNN

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%202.png?raw=true)

- 계속 RNN에 대해서 얘기하는데 왜일까?
- 왜 트랜스포머 아키텍쳐로 변환했을까?
- 또한 병렬처리를 할수 없다는 문제
    - 한번에 하나의 입력값만 전달
- 트랜스포머는 전체데이터를 병렬적으로 훈련

### 기계번역을 위한 autoregressive generation

- 이전 time stamp의 예측 (hidden state)는 다음 time stamp의 입력(x)에 포함된다.
- 이것이 autoregressive

### General En,Decoder Network

- decoder는 C(context vector)를 입력으로 받아들이고 hidden state h1:m 길이의 임의 길이 시퀀스를 생성합니다.
- 

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%203.png?raw=true)

## Transformer

## Arichitecture

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%204.png?raw=true)

- multiple encoder와 decoder
- encoder의 마지막 부분 $h_m$은 모든 decoder의 입력으로 들어감
- **모든 encoder의 구조는 같다.**

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%205.png?raw=true)

- 그러나 가중치를 공유하지 않는다!
    - 각 기 다른 가중치를 가짐
- 각 encoder는  두개의 sub-layer로 나뉨
    - self-attention
    - feed-forward nn

### key property of Transformer

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%206.png?raw=true)

- 각기 단어마다 word embedding 존재
- positnal encoding 이후 self attention input으로 들어감
    - **동시에**
- self-attention layer
    - $x_n$이 동시에 들어오는데 이러한 입력간의 관계를 알아냄
    - fnn은 입력관계를 알아내지는 못함

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%207.png?raw=true)

- r1,r2가 출력을 하는데 fnn은 서로 관계나 종속성을 논의하지 않기 때문에 fnn을 사용

### 즉 self -attention

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%208.png?raw=true)

- 각 단어의 query,key,value유지
- Query : 우리가 찾고자 하는 “단어” 에 관한것
- Key : 이러한 Query에 대한 잠재적 솔루션
- Value :  키 뒤에있는 실제 솔루션

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%209.png?raw=true)

- input Embedding
    - 선형 임베딩
    - Word2Vec , Glove, fast text 같은 어느것이든
- Positinal Encoding
    - RNN 처럼 순차적인 위치가 없음
        - 병렬처리를 하기 때문에
    - 데이터 포인트의 위치를 찾기 위해 positinal encoding 추가
- Decoder
    - Positinal Encoding과 출력 임베딩 가짐
    - 

## Positional Encoding

- 단어의 위치 추적
- rnn은 데이터가 순차적으로 들어오기 때문에 데이터포인트의 위치 (ㅅtimestamp 존재)
- 시퀀스에서 **토큰의 상대적 또는 절대적 위치**에 대한 정보 필요

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2010.png?raw=true)

- Positinal encoding이 없다면 이 두문장을 같은 형태로 처리
    - 즉 같은 의미를 같는 문장으로 여김
- **Positnal Encoding Vector + Word Embedding Vector**

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2011.png?raw=true)

- 두벡터의 값을 더하는 것인가?
- 아니요?
- 두 벡터의 연결을 사용하는 것인가?

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2012.png?raw=true)

- 모델은 워드 임베딩으로 부터 독립적인 Positinal Encoding Vector를 확인한다.

## 어떻게 작동하는가?

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2013.png?raw=true)

- 서로 다른 주파수의 sin, cos 함수
- d ⇒ model dimention
- pos : 위치 , i : 치수
- d = 512라면?

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2014.png?raw=true)

- 첫번째 단어의 positinal encoding을 찾기위해 이것을 결합

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2015.png?raw=true)

- 0번째 단어의 positinal → 0,1,0,1…0,1 로 이루어짐

## Transformer Code

## Bert

## Bidirection Encoder representation from transformer

## NLP의 pretrain ?

- 처음부터 모델을 학습시키는 것은 어렵다
- 구조화 되지 않은 데이터 세트로 거대한 모델을 훈련시킨다
- pretraining 된 모델을 사용하여 “임베딩 및 워드 임베딩” 생성
- 다음 pretraining model 미세조정
- 데이터 양 적고 시간 적게 걸림

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2016.png?raw=true)

### bert 가 나오기 전 여러 임베딩 존재

- tf-idf , word2vec, glove등
- word2vec, glove 등은 pretrained 된 text corpus에서

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2017.png?raw=true)

## Contextual Representations

- **문제**
    - 워드 임베딩이 자유 방식의 맥락에서 적용된다는 것
    - 거대한 말뭉치와 하이레벨 차원에서 컨텍스트 정보가 없음을 의미
    - bank, bank 같은 단어지만 다른의미를 가지는데
        - 차원이 높아지면 컨텍스트가 손실된다는 것
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2018.png?raw=true)
    
- **해결책**
    - 텍스트 말뭉치에서 컨텍스트 표현을 훈련하는 것
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2019.png?raw=true)
    
    - 통합된 임베딩을 갖는 대신 각각에 대해 다른 임베딩을 갖도록 하자는 의미
    - 이를 통해 코사인 유사도를 통해 어느정도 동일한지 여부를 확인할수 있음

## Unidirectional vs . Bidirectional Models

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2020.png?raw=true)

- 단방향 vs 양방향
- 단방향
    - GloVe , Word2Vec
    - 점진적으로 표현을 작성
    - ex ) ‘open’ 은 ‘a’ 와 관계를 가질수 있음
        - hidden state로 이어지는 open과는 연관성이 없음
- 양방향
    - Bert
    - ‘open’은 ‘open’자체와 연관성 가질수 있고 ‘a’와 관계도 가질수 있음

### Masked LM # 단어예측

- 입력단어의 k%를 마스킹 한 다음 마스킹한 단어 예측
- k 는 거의 15% 사용

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2021.png?raw=true)

- 마스킹이 적을 경우 : 훈련 비용이 비쌈
- 마스킹이 많은 경우 : context가 충분하지 않음

## Next Sentence Prediction

- 문장간의 **관계를 학습**
- 문장 B가 문장 A를 진행하는 실제 문장인지 임의의 문장인지 예측

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2022.png?raw=true)

# BERT의 입력 표현

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2023.png?raw=true)

- 30000개의 단어 input
- 각 3개의 embedding
    - Positinal : 위치
    - Segment : Bert에서 도입
        - 특정 Segment를 찾는것
        - My dog is cute에서 문장 전체가 하나의 Segment
        - 따라서 Segment EA EA EA EA 를 갖는다
    - Token
        - 사인 코사인과 같은 포지셔널 인코딩 작업에 관한것
- 하나의 시퀀스가 더 효율적

# 모델 아키텍쳐

- 인코더가 여러개 쌓인 형태

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2024.png?raw=true)

- 여러 인코더 아키텍쳐를 서로 연결하는 경우 BERT와 같은 아키텍쳐를 가짐

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2025.png?raw=true)

- self attention ,LSTM ⇒ localitiy bias 없음

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2026.png?raw=true)

- Transformer → 단일 레이어당 곱셈 수행 → GPU, TPU 효과적

## Model Detail

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2027.png?raw=true)

## Fine Tuning Procedure

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2028.png?raw=true)

- 마스크 언어 모델이나 마스킹 문제로 작업하는 경우 마스크를 문장으로 전달

## SQuAD 1.1

- stanford에서 도입한 데이터세트
- 모델 성능 ㅈ볼수 있ㅇ므

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2029.png?raw=true)

## GPT

- transformer 의 decoder를 사용 # stack

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2030.png?raw=true)

- GPT-4 400조개 paramters

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2031.png?raw=true)

## GPT2 Action

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2032.png?raw=true)

- 다음 단어 예측으로 GPT2사용
- bert는 mask attetion 같은 mask 개념 사용
- gpt는 self-attention 사용

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2033.png?raw=true)

## Masked Self-attention

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2034.png?raw=true)

- 오른쪽 BERT : masked self-attention
- 왼쪽 GPT : self-attention

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2035.png?raw=true)

- 즉 masked self attention은 mask에 self attention 방식 적용
- 우리가 가지고 있는 것 :
    - robot must obey
    - 이제 다음 예측을 해야함
    - transformer decoder를 거쳐 orders를 예측함
- transformer decoder에서는 masked self-attention과 ffnn 가지고 stack으로 쌓여있음

## GPT2 fully connected network has two layers

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2036.png?raw=true)

- 작은 모델 -d : 768
- gpt 2 : 2개의 fully connected layer
- gpt 3 : 여러개의 fully connectyed layer

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2037.png?raw=true)

- 맨위 softmax를 통해서 k개의 높은 확률을 가진 k개의 단어 : top k

## Training

- 어떻게 학습했는가?
- gpt2 : 언어 모델을 훈련하는 비지도 학습
- bert는 자신만의 문제로 pretraining  된 모델 fine-tuning 필요
- gpt2는 그럴 필요가 없음

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2038.png?raw=true)

## GPT Prediction

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2039.png?raw=true)

- 예측에서는 디코더 아키텍쳐를 위로 쌓아두는 것만 함
- 이후 각출력에  softmax 를 통해 각 단어의 확률이나옴

## GPT2 App - Translation

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2040.png?raw=true)

## GPT2 App - Translation

- 요약 : 특정기사를 여기에 전달하면 됌

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2041.png?raw=true)

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2042.png?raw=true)

## BLOOM

- 다음 토큰 예측을 위한 auto regressive model
- 46개의 언어로 훈련
- 오픈소스

### 훈련

- 70개의 transformer block이 사용됌
- 거대모델
- 허깅페이스 API에서 무료로 사용가능

### 해결할수있는 문제들

- 텍스트 생성
- 시퀀스 분류
- 토큰 분류
- 토큰 예측
- 질문 응답 및 회귀

### version

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2043.png?raw=true)

## 아키텍쳐

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Transformers/Untitled%2044.png?raw=true)

[Bloom Demo - a Hugging Face Space by huggingface](https://huggingface.co/spaces/huggingface/bloom_demo)