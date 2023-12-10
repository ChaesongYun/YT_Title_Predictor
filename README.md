# YT_Title_Predictor
BERT를 사용한 인공지능 웹서비스<br>
유튜브에 어떤 제목으로 영상을 업로드해야 조회수가 많이 나올 수 있을지를 예측해주는 추천 서비스<br>

<img src=
https://i.namu.wiki/i/OqsdKhO__CiPCMQ-9ur2bS7Vipp6uyQRjpGycOUVX7-hTqHcIam4MdsgeW0qZMaWQxZvHbN2PeguljjKjyef0ZZ3VrlVGiHVe6kJcYOCoZDJ0PGZU1NktyKh0FeNY-_PUu537hsjfGKZ5FYavPESmA.webp>
(출처: 유튜브 모카우유)
<br>
<br>

## Data
방법: Youtube API<br>
키워드: <br>
['강아지', '보더콜리', '리트리버', '시츄', '사모예드', '시고르자브종', '강형욱', '요크셔', '개', '비숑', '말티즈', '골든리트리버', '허스키', '대형견', '소형견', '중형견', '진돗개', '푸들', '유기견', '웰시코기']<br>
가져온 데이터: 제목, channelID, videoID, 조회수, 구독자수
<br>
<br>

## Data Cleaning
- videoID가 null인 영상은 임의로 a_k-dCgubFo란 ID를 입력했으므로 videoID가 a_k-dCgubFo인 데이터들을 지워준다
- 중복된 영상이 있다면 지운다
- 구독자 수가 0인 데이터를 지운다(구독자수 대비 조회수를 계산할 거니까!)
<br>
<br>

## Data Processing
- metric 계산
  - 조회수/ 구독자수
  - 중앙값보다 크면 1, 작으면 0
  - 조회수가 가장 많은 영상과 가장 작은 영상은 차이가 너무 크기 때문에 중앙값으로 구하기로 한다
- 제목에 이모티콘(😍👍💢등)이 들어간다면 지운다
- 데이터 추출
<br>
<br>

---
<br>
<br>


## Model FineTuning 
클리닝 끝난 데이터를 BERT라는 자연어처리 인공지능 모델을 이용해서 fine tuning 작업을 해준다<br>

- Pre-trained tokenizer 다운 받기
- Data sampling 데이터를 섞는다
- dataset을 training용과 validation용으로 나눈다
- input data 만들기
- 학습모델 모델링
- 모델 compile
- 모델 fit
- 모델 평가하기
- 모델 다운로드

<br>
<br>

---

## Tools
![image](https://github.com/ChaesongYun/YT_Title_Predictor/assets/139418987/a44db2be-8131-49e3-8397-88ca886bc691)
