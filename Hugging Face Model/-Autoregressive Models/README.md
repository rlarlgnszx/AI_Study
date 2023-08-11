# Autoregressive Models

## AutoRegressive 자기 회귀 모델

- 사용성
    - 시계열 데이터가 정상성을 가지는 경우
        - adf test, kpss test
    - 현재 데이터가 과거와 독립이 아닌경우,
        - acf,pacf 그려서 확인
        
hugging face로 GPT-2 text 생성

- gpt2 자체는 비지도 다중학습기
- ‘Laguage Models are Unsupervised Multitask Learners 논문
- gpt2의 학습방법을 알수있음
https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Autoregressive%20Models/2_2_Transformer_XL.ipynb
[2_1_GPT2.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Autoregressive%20Models/2_1_GPT2.ipynb)

## Transformer_XL을 사용한 label 분류

- 이전 gpt2 ,bert등 트랜스포머기반 모델들의 문제점
    - 고정된 길이의 context 가 있다.
- 1억개의 토큰을 처리하기 위해 설계된 최초의 모델
    - 최대 1000개의 토큰 생성가능
- 이모델은 텍스트 생성 및 분류에 사용 가능

[2_2_Transformer_XL.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Autoregressive%20Models/2_2_Transformer_XL.ipynb)

## Reformer를 활용한 대량텍스트 QnA

- 장점 : 일반적인 트랜스포머보다 시간복잡도 개선
- 무작위 어텐션 사용
- $O(L^2) → O(L log L)$
- 

[2_3_Reformer.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Autoregressive%20Models/2_3_Reformer.ipynb)

## XLNet을 활용한 시퀀스 분류

- google ai brain 팀 논문
- 마스크드 어텐션 사용
- 

[2_4_XLNET.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Autoregressive%20Models/2_4_XLNET.ipynb)