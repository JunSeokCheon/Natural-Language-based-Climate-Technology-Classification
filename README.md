### 📋 **자연어 기반 기후기술분류 AI 경진대회** (2021.06 ~ 2021.09)

- 한줄 소개 : 국가 연구개발과제를 '기후기술분류체계'에 맞추어 라벨링하는 알고리즘 개발 프로젝트
- 프로젝트 인원 : Machine Learning : 전체 팀원 참여
- 맡은 파트 : Machine Learning 개발
- 사용 기술 : Python, Keras, Tensorflow
- 특이 사항
    - 필자의 첫 자연어 처리 프로젝트
    - RandomForest, Bert, LGBM, Kobert 사용 경험
- 개발 부분
    - 조사, 특수문자 등 데이터 전처리 / 필요 없다고 판단되는 columns을 삭제
    - okt, mecab 객체를 사용하여 형태소 단위로 분리
    - RandomForest, Bert, LGBM, Kobert  학습 후 모델 생성
    - 결과로 나온 모델을 사용하여 test_label 예측

-------------------------------------------------------------------------------------------------------------------------------------------------------------

### 1. 데이터 전처리
- [ ~ ], < ~ >, ( ~ ), 한글을 제외한 문자 삭제, 2번 이상 반복되는 ','를 하나로 변경, 2번 이상 반복되는 공백문자를 하나로 변경
- 영문키워드는 ','를 공백문자로 변경하고 2번 이상 반복되는 공백문자를 하나로 변경
- 필요 없다고 판단되는 columns을 삭제(유의미하다고 판단되는 columns : 과제명, 한글키워드, 영문키워드)
- okt or mecab 객체를 사용하여 형태소 단위로 분리


### 2. 모델 학습
- Random Forest -> LGBM -> Bert -> Kobert 순으로 학습하되, columns(과제명, 한글키워드, 영문키워드) 섞어서 학습한다. 
- 과제명 -> 과제명&한글키워드 -> 과제명&영문키워드 -> 과제명&한글키워드&영문키워드 -> 한글키워드&영문키워드 -> 영문키워드 순으로 정확도가 낮아진다.
- BERT는 사전 학습을 한국어 전용이 아니라 multilingual로 학습이 된 모델


### 3. 결과 예측
- 학습된 모델을 활용하여 test_data를 예측한다.
