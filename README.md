# DACON_KBO-Batter-OPS-Visualization-Contest

해당 공간은 [DACON 타자 OPS 시각화 대회](https://dacon.io/competitions/official/235546/overview/)에 참여한 코드를 저장하기 위한 공간입니다.

해당 코드에 대한 저작권은 시로앤마로(안지민, [이인섭](https://github.com/insub789), [이형선](https://github.com/traceofpassion), [주은혁](https://github.com/EunHyeok-Ju))에게 있습니다.

주관 : [데이콘](https://dacon.io) / 주최 : KBO

## 대회 설명

[DACON 타자 OPS 예측 대회](https://dacon.io/competitions/official/62540/overview/)의 상위 4 ~ 20등이 참가하는 시각화 대회

역대 KBO 타자들의 정규시즌 등 게임 데이터를 활용하여 미래 선수의 성적을 예측하기 위한 중요한 통찰(Insight)을 발굴하는 목적의 대회


## 데이터 설명

### 제공 데이터
* Regular_Season_Batter.csv : KBO에서 활약한 타자들의 역대 정규시즌 성적을 포함하여 몸무게, 키 ,생년월일 등의 기본정보

### 산출 데이터

* filled.csv : 누락되어있는 선수에 대한 키/몸무게 값 크롤링 데이터

## 데이터 처리 과정

데이터 전처리 - Feature Engineering - PCA - Clustering - Visualization - Verification

## 주제 선정 배경

[맞으면 홈런인데 타율은 1할...MLB 특급 **공갈포**](https://www.chosun.com/site/data/html_dir/2018/08/11/2018081100125.html)
[**똑딱이** 신세 푸념하던 민병헌, 드디어 손맛 보다](http://news.chosun.com/site/data/html_dir/2018/08/11/2018081100125.html)

* [공갈포](https://namu.wiki/w/%EA%B3%B5%EA%B0%88%ED%8F%AC) : 파워는 준수하여 순장타율과 홈런갯수는 볼 만한 수준이나 타율 혹은 출루율이 매우 좋지 못해 실질적인 타석 생산력이 가진 파워에 비해 많이 떨어지는 선수
* [똑딱이](https://namu.wiki/w/%EB%98%91%EB%94%B1%EC%9D%B4) : 야구에서 홈런을 거의 치지 못하고 단타 위주의 타격을 하는 교타자들을 얕잡아 이르는 말

야구계의 은어로 사용되는 단어를 데이터를 통해 확인할 수 있는지에 주목하였습니다.

### Feature Engineering
* 순장타율(Isolated Power) : 장타율(SLG) - 타율(avg)
* 순출루율(IsolatedDiscipline) : 출류율(OBP) - 타율(avg)
* 선구안(BattingEye) = 
## 모델링

* Linear Model : 선형 회귀 모형
* RandomForest : 랜덤 포레스트

## 후기

처음 출전한 공모전으로서, 상반기 야구 경기가 매일 진행되면서 점수가 업데이트되는 점이 흥미로웠음.

야구에 대한 도메인 지식을 쌓을 수 있었고, 머신러닝에 대해 공부하게 된 계기가 되었음.

## 결과

![최종 결과](https://user-images.githubusercontent.com/64209837/107141795-7e3a4880-696e-11eb-94c7-ef1eb47769f3.PNG)

최종 4등으로서 수상을 하지 못하였지만, 이어지는 KBO 타자 OPS 시각화 대회 참가 혜택 받음.

