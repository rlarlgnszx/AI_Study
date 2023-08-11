# RNN Model

# One-to-Many

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled.png?raw=true)

- 이미지가 있고 이미지의 대한 캡션
- 감성 분석 결과? → 트윗 예측

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%201.png?raw=true)

## Intuition

- 입력 하나의 시간스텝
- 출력에는 여러시간 스텝

## 어떻게 작동하는가?

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%202.png?raw=true)

- CNN을 처음 쓴다.

1. CNN으로 이미지 읽고 embeding 처리
2. 이 embedding은 RNN에 embdedding

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%203.png?raw=true)

- a0 편향으로 봄
- RNN cell이 입력 sequence를 수신
- 하나 출력하고 recurrent
- 반복
- 양방향 RNN도있음
  - backbone 수행하는 RNN

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%204.png?raw=true)

# Many-to-One

[Music_Recommendation_System.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Music_Recommendation_System.ipynb)

## RNN e다대일 모델

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%205.png?raw=true)

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%206.png?raw=true)

- 트윗 → 감정분석
- 하나의 출력을 만들기 위해 여러 입력이 필요할때
- ex)
  - review text로movie 평가
  - 좋은 플레이리스트를 만드는것 → next song
- 콘텐츠 기반 알고리즘
- 변환 및 전체 파이파린구성

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%207.png?raw=true)

- non-API
- ex) 노래의 손실 시퀀스를 기반으로 다음 노래에 대한 피쳐 벡터를 결정
  - 손실 함수는 노래에서 이상적인 피쳐벡터까지의 거리와 노래 키 전환의 자음 및 템포의 유사성 기반으로 결정
  - ⇒ 노래가 시퀀스 뒷부분에서 목적함수를 더 잘수행할수 있는지 여부 고려 X → 그리디 알고리즘
- 추천시스템 앱 ⇒
  - 시퀀스의 다음항목에 대해 하나의 핫 인코딩 포함하지 않음
- 흐음…. 이해가 잘안되는뎅
- 

# Many-to-Many

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%208.png?raw=true)

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%209.png?raw=true)

- 다대다 하위 프로세스 사용

# Sequence to Sequence

[Machine_Translation.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Machine_Translation.ipynb)

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Transformer/RNN%20Model/Untitled%2010.png?raw=true)

- machine Translation
