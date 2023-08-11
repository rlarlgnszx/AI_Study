# -Encoder Models

## Bert 사용한 마스킹 단어 예측
- 여러개의 인코더 사용함

[3_1_BERT.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Encoder%20Models%20/3_1_BERT.ipynb)

## ALBert를 사용한 마스크 단어 예측

[3_2_ALBERT.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Encoder%20Models%20/3_2_ALBERT.ipynb)

## RoBert를 활용한 마스크 단어 예측

[3_3_Roberta.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Encoder%20Models%20/3_3_Roberta.ipynb)

## DistilBert를 활용한 문장 유사도 측정

### bert와 유사하지만 Bert의 원래 가중치로 훈련된 작은 Bert

- knowledge distilnation → 지식 증류 사용한 작은 모델
- 증류된 bert
- 지식 증류란?
    - 큰 모델의 가중치를 작은 모델로 이동시키는 것을 의미한다.
    - 작은 모델은 작은 가중치를 가지게 됌
    - ex ) Bert 5Gb 1200만개 params라면
        - 증류 Bert : 1G~2G , 500~600만개 정도
- 허깅페이스에서 나온 방법
- Bert 모델의 40%를 줄이고 언어이해능력 97%유지하면서 60%더 빠른 속도 가능

[3_4_DistilBERT.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Encoder%20Models%20/3_4_DistilBERT.ipynb)

## ConvBert를 활용한 다음 단어 예측

## 컨볼루션 Bert

- span 기반 동적 컨볼루션을 통해 bert 개선
- bert에 혼합 어텐션 을 적용함

![Untitled](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Encoder%20Models%20/Untitled.png)

[3_5_ConvBERT.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Encoder%20Models%20/3_5_ConvBERT.ipynb)

## XLM-RoBERTa

- face book 개발
- 다른언어 100개
- 많은 자연어 처리 문제에 사용했음
- 2.5 TB 사용

## XLM-roberta를 파인튜닝

- hugging face imdb 데이터셋 사용
    - 감성분류를 위한 데이터셋

[xlm_roberta.ipynb](https://github.com/rlarlgnszx/AI_Study/blob/main/Hugging%20Face%20Model/-Encoder%20Models%20/xlm_roberta.ipynb)