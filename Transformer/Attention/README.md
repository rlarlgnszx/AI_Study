# Attention

## Attention Workflow
![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled.png?raw=true)

- 심리학적
    - 다른것은 무시하면서 하나 또는 몇가지에 선택적 집중하는것
    - 주어진 문장에서 어떤 것에 집중하는것
- 2가지에 attention 작용
    - 입력요소 , 출력요소 사이 ⇒ Gerneral attention
    - 입력요소의 중요성 → self attention
- translation 에서 의 attention 그림
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%201.png?raw=true)
    
    - how ~= comment
    - how ≠ journee
    - 각 단어사이의 연관성

## Attention Workflow

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%202.png?raw=true)

- 6번의 decoder는 어떤 decoder든 상관없음

### Workflow 1

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%203.png?raw=true)

- encoder의 hidden state 생성

### Workflow 1.1

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%204.png?raw=true)

- alignment score 계산
- 어떻게 동작하는가?
    - 초록색 부분 ⇒ linear layer # cnn , DNN or anything
    - decoder hidden state와 encoder hidden state ⇒ linear layer로 전달

### workflow 1.2

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%205.png?raw=true)

- 1.1에서 나온 Decoder층 가중치 + Encoder층 가중치 가추가됨
    - tanh 활성화함수에 전달

### workflow 1.3

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%206.png?raw=true)

- 각 encoding 된 출력에 대한 점수를 보유하는 최종 정렬 점수 벡터 얻음
- alignment score를 얻음
- 주목
    - 첫번째 디코더 스텝 → 이전 히든 스테이트 또는 출력 없음
    - 마지막 인코더 히든 스테이트 → 토큰 혹은 히든스테이트 출력이라고 할수있음

### workflow 1.4

- 실제로 중요한 것과 중요하지 않은 것 판단

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%207.png?raw=true)

- 활성화 함수 softmax
    - 즉 출력이 0에 가까우면 이것이 실제로 중요하지 않다는 의미

### workflow 1.5

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%208.png?raw=true)

- context vector에서 가중치에 따라 중요성을 따지고 무효화된다.
- 

## Attention Type

## What is attention?

- 문장이나 토큰에서 좋은 데이터를 만드는 것
- 좋은 쿼리 벨류 쿼리
- 3가지 유명한 attention
    - generalized attention
    - self-attention
    - **multi-head attention**

### Generatlized attention

- sequence에 대한 attention 을 그래프 작업으로 생각해야한다.

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%209.png?raw=true)

- attention 점수를 그래프로 바꾸는 것
    - 삭제된 쿼리 , 키 ,벨류를 찾는닷
- 어떻게 작동?
- 쿼리, 키 , 벨류를 얻고 그래프이론으로 복제
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2010.png?raw=true)
    

### Self attention

- 기본 아이디어
    - 단일 시퀀스의 다른위치를 가지고 동일한 시퀀스의 표현을 계산하는 것
    - 해당 시퀀스에서 상요할수 있는 모든 가능한 토큰에 어텐션 줌
    - 다른 모든 쿼리, 각 토큰에 대해 다른 어텐션 점수 유지
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2011.png?raw=true)
    
- 

### Multi head attention

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2012.png?raw=true)

- self attention 과 다른점
    - 여러개의 head 존재
    - Head는 Sz의 쿼리 시퀀스를 찾는다
        - 각 head는 각 query,key ,value 또는 query,key, value 키 행렬을 찾는 역할 담당
        - 이후 attention score의 전달

### 작동 방식

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2013.png?raw=true)

- 모두 입력 시퀀스를 갖는 것
- head수 n개
    - n개의 행렬이 생김
- 어떻게 n개의 행렬을 연결하는가?

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2014.png?raw=true)

1. output Seq에서 나온 n개의 head를 가진 (행렬을 가진) query,key,value 가 score로 전달
2. softmax활성화 함수를 통해서 query,key,value의 연산에서 중요한 것과 중요하지 않은 것으로 구분
3. 그다음 출력
    1. 트랜스포머 디코더 부분으로 출력으로 나가게됌

## Self attetion 자세히

- rnn의 attention이 작동하는 방식

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2015.png?raw=true)

- rnn은 state vector이전의 state 정보를 메모리로 유지
    - 오래된 정보에 액세스하는게 어려움
        - 시간 종속성의 문제

### 계산복잡도

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2016.png?raw=true)

- Attention Matrix : O(L^2)

## Efficient Attenion

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2017.png?raw=true)

- 이것은? self-attention
- 정확도의 손실없이 quadaratic 에서 linear로 어텐션 메커니즘의 계산 및 메모리 복잡성을 줄이는 방법
- query, key ,value
- M : encoder
- the ? → the attention은 다른 모든 단어에 attention
    - 이것때문에 어텐션 메모리 복잡도가 quadaratic이 되는 단점
    - 작업할 매개변수도 많아짐
- 

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2018.png?raw=true)

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2019.png?raw=true)

- $n*n  => k*c$ 로 교환
- 쿼리는 더이상 키를 사용하여 임베딩되지 않음
- value는 key와 함께 임베딩됌

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2020.png?raw=true)

- **쿼리와 키** 사용하는 대신 **키와 value** 사용
- N 만듬 : 키와 c의 곱셈일 뿐이다.
- 출력 레이어 변경점
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2021.png?raw=true)
    
    - 마지막 레이어에 단어 전달 X
        
        ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2022.png?raw=true)
        
    - efficient attention
        - 이미지 데이터와 관련하여 사용됌 # 이미지 도메인
        - NLP ⇒ Efficient attetnion 사용안됌
            - 토큰이 반복되는 데이터 → 트랜스포머가 더좋음
    

### Attention Mask (코드 포함)

- attention mask : 다양한 크기의 데이터 처리
- 모델이 attention을 주지 않도록 하는 것
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2023.png?raw=true)
    
- 마스크된 token, 마스크 안된 token
- 샘플 1,2,3의 길이 → 5,8,3
- 기능 동작은 ? 어떻게?
    
    ![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2024.png?raw=true)
    
    [Attention_Mask.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Attention_Mask.ipynb)
    

### Multi-head Attention

- head의 수만큼 q,k,v 병렬수행
- 여러 해드로 분리

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2025.png?raw=true)

- q,k,v
- n개의 head만큼 행렬벡터 추가

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2026.png?raw=true)

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2027.png?raw=true)

- 자세히 보자

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2028.png?raw=true)

- ex ) 512-d 임베딩 벡터 존재
- 이러한 embedding vector 가 멀티헤드 어텐션으로 전달
    - 8쌍의 q,k,v 사용하여 멀티헤드 어텐션 계산
- 8쌍 ⇒ head가 8개
- 출력또한 n개 여기서는 8개를 가짐

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2029.png?raw=true)

- 여기서 쿼리를 알아내려면 가중합이 필요하고 그다음 쿼리가 필요
- ex) 특정 쿼리 **Michale**로 작업중
    - 이 특정 쿼리는 모든 단어에 어텐션을 기울이는 데 사용
    - 이때 head는 8이므로 8번 수행
    - 자기 자신이 가장 높은 점수를 얻고 그다음으로 높은 순서대로 살펴봄
    - 그다음 멀티헤드 어텐션에서 모든 벨류를 얻은후 (query, key 전부 계산) 여기서 얻은 모든 value의 가중합계를 사용 → 8개의 행렬
    - Micahle이라는 하나의 쿼리에 대한 하나의 최종행렬 구함

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2030.png?raw=true)

- 중간 그림의 선들의 연결합 → value의 합
    - head의 수에 따라 여러 행렬이 존재
    - 마지막의 이 value의 합들을 또 결합
- 

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/Attention/Attention/Untitled%2031.png?raw=true)

- Scaled Dot-Product Attention?
    - 왼쪽 그림에서 v ⇒ 누적된 value 행렬이고 softmax와 계산된다.
-