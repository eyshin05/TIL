# Recruitment of the default mode network during a demanding act of executive control

* Ben M Crittenden et al.
* Apr 2015
* eLife



## Abstract

* Task 를 하는 동안 DMN, 또는 task-negative network 에서 activity 가 감소함.
  * 대개 mind wandering 이나 자기 자신에 대한 생각 등 internally directed process 이 감소한 것으로 해석하는 모양
* 한편, task 가 switch 될 때에는 DMN 이나 task-negative network 의 activity 가 증가하였음.
* 나아가서, MVPA 해서 DMN 안에서 task-relevant information 을 encoding 하는 영역을 찾아보았음.
  * 뭔가 cognitive context 가 바뀔 때 (내부적이든, 외부적이든) 이 영역들의 activity 가 변화하는 것으로 생각될 수 있겠다...



## eLife digest

* Mind wandering 이나 자기 자신에 대한 생각을 하는 것이 DMN 과 관련있다는 것으로는 잘 알려져 있었음
  * 하지만 task 하는 동안엔 inactive 하는 것으로 생각되어져 왔었다..
* 이 논문에서는 task swiching 할 때 DMN이 active 하게 된다는 것을 보여줌



## Introduction

* 기존 논문들의 DMN 의 발견
  * 감소 case
    * rest 에서 증가, task 일 때 감소
    * 어려운 task 를 할 때 감소
  * 증가 case
    * 자기 자신, 자기의 관점, 다른 사람의 관점을 생각할 때 증가
    * 과거의 경험을 회상할 때,
    * 미래를 상상할 때,
    * Mind wandering (그냥 흘러가는 생각들)
    * Theory of mind 의 taks 를 할 때
  * High-level cognitive process 와도 연관 있음
    * self-referential processing
    * imaginary scene construction

* DMN 이 세 개의 sub network 로 나누어져 있음에 대한 논의 (Andrews-Hanna et al., 2010)
  * Core sub-network: PCC + AMPFC
  * MTL sub-network: VMPFC + HF + PHC + Rsp + pIPL
    * Mental scenes based on memory
  * DMPFC sub-network: DMPFC + TPJ + LTC + TempP
    * Mentalising
  * 근데 이 구분은 절대적이라기 보다는 상대적인 것으로 보임. Conscious recollection 실험을 했을 때 모든 sub-networks 가 연관된 것으로 나오기도 했음.
* DMN 의 기능에 대해 간단하게 개념화 해 보고 이를 Andrews-Hanna framework 에 적용해보자.
  * 상상, mind-wandring, 다른 사람의 관점을 취하기 같은 task 는 최근의 cognitive context 와 많이 다르다
  * 의식적인 기억 회상은 과거의 경험을 다시 활성화하는 것으로, 복잡한 주변 환경이나 맥락과 연결되어 있음
  * 맥락의 shift 는 일상 생활에서 흔한 일임
    * 저녁 요리를 하다가 손님의 전화를 받는 것 등
    * 그치만 실험실에서는 잘 일어나지 않는다...
  * 특정한 고차원의 cognitive process 보다, DMN 은 어쩌면 cognitive context 의 switch 와 관련이 있는게 아닐까?
* 가설 검증을 위한 실험 디자인
  * 6개의 task; 3 카테고리로 2 종류씩
  * Task 의 surrounding box 색깔로 task 의 종류를 알려줌
  * No-switch trial
    * (앞의 것과) Task 의 종류가 동일한 것
  * Similar-task-switch trial
    * 같은 카테고리에 속한 다른 task
  * Dissimilar-task-switch trial
    * 다른 카테고리의 task
* 가설
  * Dissimilar-task-switch trial 에 DMN 의 recruitment 가 증가할 것이다.
    * Core 랑 MTL 의 activity 가 증가함을 발견했음
  * 추가로, 모든 sub-networks 가 task 하는 동안 task 와 관련된 정보를 표상한다는 증거를 보여줄 것임.



## Results

### Behavior results

* 사람들의 performance: 잘했음
* Reaction time: 다른 과제일때 더 길었음

### Task-switch related activity in DMN

* fMRI 분석 내용
* Preprocessing steps
  * 평범..

* 다른 과제 vs. 같은 과제 GLM 수행
  * FDR corrected p < 0.05 로 thresholding
  * Core, MTL 네트워크와 관련된 영역들은 나왔는데, DMPFC 네트워트와 관련된 영역은 안 나왔음
* Definition of individual DMN ROIs
  * Use previously defined
* DMN sub-networks 별 평균 activation
  * ROI 안에서 switch type 에 따라 평균 베타 값을 구함
  * 다른 과제 vs. 같은 과제 ROI 분석 결과
    * Core, MTL 네트워크에서 유의미하게 증가하였음
    * DMPFC 에서는 de-activation 하는 경향 (TPJ 에서는 유의미) 을 보임
  * 비슷한 과제 vs. 같은 과제는 차이 없음
  * Two-way repeated measures ANOVA
    * Core, MTL, DMPFC
    * 다른 과제 vs. 같은 과제
    * Core 랑 MTL 은 유의미하게 증가
    * DMPFC 는 maginal 하게 감소 (p=0.06)
  * Sub-network level 에서 차이를 분석
    * 각각 sub-network 별로 ROI 에서 나온 평균 베타 값을 평균하여 two-way repeated measures ANOVA 수행
    * Main effect, interaction 둘 다 유의미하게 있음
* Exploratory analysis
  * 다른 과제의, 서로 다른 3 카테고리 별로 previous trial - current trial task 로 짝지어서 univariate ROI analysis 수행 (같은 과제와 paired t-test)
  * Perceptual 카테고리에서 lexical 카테고리로 바뀌었을 때 특히 DMPFC sub-network 가 감소했고,
  * Lexical 카테고리에서 perceltual 카테고리로 바뀌었을 때 특히 Core sub-network 가 증가했음



### Multivariate decoding demonstrates task representation across the DMN

* Preprocessing step

  * 같은데 smoothing 은 안 함

* MVPA

  * Target: task pair (per-lex 등 15개)
    * 6 * 5 / 2 = 15?? 그냥 단순히 하면 6 * 6 이어야 할텐데 왜지? 다른 (similar 포함) 과제만 하는데 순서는 상관 없음?
    * 같은 과제 제외... 하고 순서 상관 없이 15개 한 것이 맞는 듯. Univariate EDA 에서 다르게 나왔는데 왜? 30개면 못 맞춰서?
    * 그리고 matrix 그릴 때에는... 대각선 기준으로 아래 위 같고 위쪽 삼각형에 significance 를 표시한 것이네요.
    * 흠 나라면 앞에건 맞추고 뒤에 나오는 trial 의 task 를 맞추게 하던가 카테고리로만 했을 듯
    * 아님... 같은 과제 / 비슷한 과제 / 다른 과제... 흠 서로 상이하니까 그건 좀 그런가
  * Leave-one-run-out cross-validation

* Accuracy 를 구해서 similar, dissimilar 를 비교함

  * 서로 다른 과제 사이의 decoding 은 task feature 에 따른 많은 차이에 의해 야기될 것
  * 한편, 유사한 과제 사이의 decoding 은 internal representation 에 의해 야기될 것
  * Core, MTL, DMPFC 각각 네트워크 안의 ROI 를 average 해서 similar, dissimilar 비교한 것임
  * Core, MTL, DMPFC 다 dissmilar 가 significant 했고, 약하긴 했지만 DMPFC 에서 similar pair decoding acc. 도 significant 했음.

* RT 가 accuracy 의 차이를 야기한다는 연구 결과들이 있음

  * Regression analysis (CA 와 RT 의 차이의 절대값), 세 개의 sub-network 별로 각각.

    * Each ROI, each subject 별로 accuracy 를 구해서, subject 별로 sub-network 안의 ROI 의 accuracy 값을 평균내서, 
    * 3 sub-network × 18 subject × 15 task pair 의 3차원 matrix 를 구해서,
    * 서로 다른 / 유사한 task 별로 구분 한 다음,
    * RT 와 accuracy 사이의 Spearman's correlation analysis 를 수행함
    * 그림 보면, RT 와 상관 없이 dissimilar 가 전반적으로 더 accuracy 가 높고, similar 가 더 낮음.
    * Correlation analysis 에서 나온 p-value 도 이와 유사한 결과.

  * 각각 subject 별로 따로, 각각 ROI 안에서, similar와 dissimilar 따로, accuracy 를 모델링한 regression analysis

    * 종속변수는 RT 차이값
    * beta 값 나온 것을 각각 subject 마다 구했음
    * sub-network 안의 ROI 끼리 평균냈음
    * RT 가 accuracy 를 systematically 예측하지 못하는 것으로 보임
      * Core, dissimilar task 는 significant 하지만 나머지는.. 특히 similar task 는 아님

     

## Discussion

* Rest 에서 sustained DMN activity 가 나타나는 것과 연관 지어서
  * Sustained activity 가 switch-related activity 와 어떻게 연관되는가?
  * 한 가지 가능성: Rest 상태에서 인식하고 있는 내용에 주기적으로 큰 shift 가 있다고 가정하면, sustained DMN activity 가 나타나는 것도 타당함
  * 만약 DMN 기능의 주요 측면이 relaxing an attentional focus 라면, unfocusing 도 switching focus 도?