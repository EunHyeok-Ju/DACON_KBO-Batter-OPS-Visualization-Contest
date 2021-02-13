# DACON_KBO-Batter-OPS-Visualization-Contest

해당 공간은 [DACON 타자 OPS 시각화 대회](https://dacon.io/competitions/official/235546/overview/)에 참여한 코드를 저장하기 위한 공간입니다.

해당 코드에 대한 저작권은 시로앤마로(안지민, [이인섭](https://github.com/insub789), [이형선](https://github.com/traceofpassion), [주은혁](https://github.com/EunHyeok-Ju))에게 있습니다.

주관 : [데이콘](https://dacon.io) / 주최 : KBO

# 1. 대회 설명

[DACON 타자 OPS 예측 대회](https://dacon.io/competitions/official/62540/overview/)의 상위 4 ~ 20등이 참가하는 시각화 대회

역대 KBO 타자들의 정규시즌 등 게임 데이터를 활용하여 미래 선수의 성적을 예측하기 위한 중요한 통찰(Insight)을 발굴하는 목적의 대회

## 1.1. 데이터 설명

### 1.1.1 제공 데이터
* Regular_Season_Batter.csv : KBO에서 활약한 타자들의 역대 정규시즌 성적을 포함하여 몸무게, 키 ,생년월일 등의 기본정보

### 1.1.2 산출 데이터

* filled.csv : 누락되어있는 선수에 대한 키/몸무게 값 크롤링 데이터

## 1.2. 데이터 처리 과정

데이터 전처리 - Feature Engineering - PCA - Clustering - Visualization - Verification

## 1.3. 주제 선정 배경

[맞으면 홈런인데 타율은 1할...MLB 특급 **공갈포**](https://www.chosun.com/site/data/html_dir/2018/08/11/2018081100125.html)
[**똑딱이** 신세 푸념하던 민병헌, 드디어 손맛 보다](http://news.chosun.com/site/data/html_dir/2018/08/11/2018081100125.html)

* [공갈포](https://namu.wiki/w/%EA%B3%B5%EA%B0%88%ED%8F%AC) : 파워는 준수하여 순장타율과 홈런갯수는 볼 만한 수준이나 타율 혹은 출루율이 매우 좋지 못해 실질적인 타석 생산력이 가진 파워에 비해 많이 떨어지는 선수
* [똑딱이](https://namu.wiki/w/%EB%98%91%EB%94%B1%EC%9D%B4) : 야구에서 홈런을 거의 치지 못하고 단타 위주의 타격을 하는 교타자들을 얕잡아 이르는 말

야구계의 은어로 사용되는 단어를 데이터를 통해 확인할 수 있는지에 주목하였습니다.

# 2. 데이터 분석

## 2.1. Feature Engineering
* 순장타율(Isolated Power) : 장타율(SLG) - 타율(avg)
* 순출루율(IsolatedDiscipline) : 출류율(OBP) - 타율(avg)
* 선구안(BattingEye) = 볼넷(BB)/(볼넷(BB) + 삼진(SO))

## 2.2. 모델링

선수들의 전성기 때의 모습을 비교하여, 선수 각자의 스타일을 비교하고자 OPS를 기준으로 전성기를 선정하였습니다.

* 주성분 분석(Principal Component Analysis) : 고차원의 데이터를 저차원의 데이터로 환원시키는 기법
* K-means : 비지도 학습, 주어진 데이터를 k개의 클러스터로 묶는 알고리즘

## 2.3. 시각화

<img src="https://user-images.githubusercontent.com/64209837/107844613-4b81cb80-6e18-11eb-913c-434d8f6a1c2d.PNG" width="80%" height="80%">

3개의 군집으로 매끄럽게 나뉘어져서 이 3개의 군집을 각각 Radar Chart를 통해 군짐명을 지었습니다.

### 2.3.1. Contatct Hitter Type

<img src="https://user-images.githubusercontent.com/64209837/107844724-6274ed80-6e19-11eb-92a2-bf4171602890.png" width="30%" height="30%">


선구안이 중요하며, 순장타율에 비해 순출루율의 중요성이 높게 나타나는게 특징입니다.

성적이 좋지 않을 경우 '똑딱이'라고 얕잡아 표현합니다.

### 2.3.2. Slugger Type

<img src="https://user-images.githubusercontent.com/64209837/107844725-63a61a80-6e19-11eb-8c8b-fe4777ca0de2.png" width="30%" height="30%">

순장타율과 몸무게의 중요성이 높게 나타나는점이 특징입니다.

성적이 좋지 않을 경우 '공갈포'라고 얕잡아 표현합니다.

### 2.3.3.Multi-Player Type

<img src="https://user-images.githubusercontent.com/64209837/107844726-63a61a80-6e19-11eb-910d-da2399452840.png" width="30%" height="30%">

어느 하나의 변수도 비중이 크게 나타나지 않지만, 모든 능력을 골고루 갖고 있는 점이 특징입니다.

## 2.4. 분석 결과 검증

각 군집을 대표하는 실제 인물과 관련 기사를 대조하여 데이터 분석의 결과를 확인하는 과정을 거쳤습니다.

# 3. 결론

```
1. Significance
* 선수별 플레이 스타일을 유형화하여 데이터를 바탕으로 선수의 성장 방향성을 파악 가능
* 타순 배치, 선수 영입, 수비 포메이션 등 다각도로 유형 정보 활용 가능

2. Threshold
* 전성기를 OPS로만 파악해서 각 선수의 특장점이 드러나는 성적(WAR, 체력 등)을 개인적으로 파악하지 못했다는 한계 존재
* 2010년 이전의 프로야구 과거 데이터 및 2군 데이터를 추가하여 표본 크기를 늘린다면 더 정교한 군집화가 이뤄질 것이라고 예상
```

## 3.1. 후기

야구계의 은어로 나타나는 단어를 실제 데이터 분석의 결과와 맞았다는 점이 흥미로웠음.

도메인 지식과 인사이트의 중요성을 깨달을 수 있었고, 마크다운의 상세 적용 방법 등 시각화에 대한 공부의 계기가 되었음.

데이터 분석을 통해 얻어낸 인사이트를 활용하여 팀별 전력 비교 등 다양한 채널을 활용하지 못했던 점이 아쉬웠음.

## 3.2. 결과

![최종 결과](https://user-images.githubusercontent.com/64209837/107845441-c352f480-6e1e-11eb-927a-276bb6c6fdec.PNG)

최종 2등으로 수상

## 폴더 구조

```sh
├─Github
│  │  README.md
│  ├─code
│  │      01-Crawling_Code.Rmd
│  │      02-github-회원가입.md
│  └─data
│          demun-001.jpg
│          demun-002.jpg
|  
```

