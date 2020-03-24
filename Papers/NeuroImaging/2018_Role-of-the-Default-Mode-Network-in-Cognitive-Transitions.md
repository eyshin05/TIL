# Role of the Default Mode Network in Cognitive Transitions

* Verity Smith, Daniel J Mitchell, John Duncan
* July 2018
* Cerebral Cortex

-----

## Abstract

* DMN 이 focusted task 하는 동안 activation 이 줄어든다는 것은 여러번 보고된 연구 내용
  * Self-relevant thought process & currently task switch
* Task switch 연구를 replicate 하다가, rest 찍은 다음 다시 task 시작할 때 large DMN increase 를 발견했음
* 제안: DMN 은 scene, episode, context 를 encoding 함
  * 어떤 식으로? integrating spatial, self-referential, temporal information 으로
* 키워드: Context representation, Rereference to context



## Introduction

* DMN 은 어느 연구나 robust 하게 나오지만 기능은 아직 불명확함
* Early works
  * Rest vs. task
  * Task releated increase: dorsal attention (dAttention) network, multiple demand (MD) network
  * Mind-wandering, self-related thought, autographical memory recollection, imaging future, 등등...
  * 또한 DMN 이 internal scene, episode, context 를 create 한다는 제안이 있음
    * Internal scene 이나 context 는 spatial, temporal, social 또는 다른 요소들을 포함할지도 모름
    * Spatial representation 이나 navigation 할 때 DMN 의 일부인 posterior cingulate, retrosplenial cortex, hippocampus 가 연관되어 있다는 연구도 있음
  * Medial frontal, posterior parietal 은 social cognition 과 관련이 있고,
    * 다른 사람의 mental state 를 고려할 때 등
  * 다른 DMN activity 도 시간, 미래에 대한 계획 등과 연관되어 있음
* 이 연구
  * Yes / no task
  * Pictures, words, shapes 도메인 안에 두 가지 타입
  * Within-domain, between-domain 으로 switch
  * 얘네는 core, MTL, dmPFC subnetwork 라고 쓰네
  * Task switching 인데 왜 우리가 refer 해야하는거지?
  * Task-related pattern 을 보기 위해 task-positive MD network 도 씀



## Materials and Methods

### Participants

* 28 명

### Task

* Same 인지 different 인지 선택하는 task 인데, color box 가 주제를 알려줌

* Rest trial 도 있음
  * Rest + task = restart, 
  * rest + rest, 
  * task + rest, 
  * tast + different (dissimilar) task, 
  * task + same domain (similar) task, 
  * task + same task

### Regions of Interest

* 8mm spherical DMN ROIs
* Frontoparietal MD ROIs 도 사용함
  * inferior rontal sulcus,
  * dorsal prefrontal cortex, 
  * inferior frontal junction, 
  * anterior insula/frontal operculum, 
  * presupplementary motor area/dorsal anterior cingulate, 
  * intraparietal sulcus

### Univariate analyses

* Task phase (cue, execution) 별로, task type (6개의 task 종류) 별로, task pair 별 regressor 를 만들어서 GLM 수행
  * Execution 에서는 response type (same or different) 도 나누어서 구함
* Incorrect trial 은 따로 modeling 되기는 했지만 제거됨
* Dummy trial 도 제외됨 (모델링 후? 아님 모델링을 안함?)
* HRF 는 delta function 으로 convolve 되었음
  * Cue 에서는 onset time 으로, execution 에서는 execution block 에서 middle(?) 으로.
    * Execution 다시 읽어보니까 until response 까지가 execution 임 이런 경우엔 middle 도 괜찮은 것인가

* Subject 마다 각 ROI 에서 평균 contrast value 를 구한 다음에, 각각 subnetwork 별로 평균냄

### Multivariate analyses

* Z-scoring beta values (across task, within each voxel)

* 15 possible task pair 별로 pairwise classification 을 수행함
  * 여기에서도 univariate 과 multivariate analysis 의 target 이 다르군요... 고민
* Linear SVM 사용, leave one run out cross-classification
* Accuracy - chance level (50%) 를 각각 task pair 별로, ROI 별로, subject 별로 구함
* 그 다음 이걸 subnetwork 안의 ROI 끼리 평균냄

### Finite Impulse Response Model (FIR Model)

* 잘 모르겠음 나중에 봐야지



## Results

### Behavioral Switch Costs

* 얼마나 사람들이 잘 맞췄는지: 95.9 %
* Same task pair 가 얼마나 빨랐는지: dissimilar 랑 비교했을 때 t=3.97, similar 랑 비교했을 때 t=4.22
  * Crittenden et al., 2015 랑은 다르게 similar vs. dissimilar 는 significant 한 차이가 없었음
    * Design 때문인가봉가

### Increased DMN Activity on Rest Trials

* Cognitive switching 분석을 위해 cue 에만 초점을 두고 execution 은 제외함
* Task-negative characteristic of DMN (Univariate analyses)
  * Task 는 task stay, similar, dissimilar task 다 평균 낸 것
  * Rest switch > task 는 rest switch 랑 task 비교한 것
    * Core, MTL, dmPFC significantly increased, MD (less) significantly decreased
  * Rest stay > task
    * Core, MTL significantly increased
  * Additional t-test (rest stay vs. rest switch)
    * Core, MTL significantly different (rest stay 가 높음)
  * 2-way repeated measures ANOVA
    * rest switch > task stay, rest stay > task stay 로
      * task 는 같은데..?
    * subnetwork 의 main effect 랑 interaction effect 는 significant
  * 그리고 multiple comparison correction 했단 얘기는 없네용? 

### Increased DMN Activity for Large Task Switches

* To replicate Crittenden et al., 2015...
  * 의 univariate analysis 결과
  * Dissimilar task 에서 core 와 MTL subnetwork 의 activity 가 증가했음 (repliate 되었음)
    * dissimilar > similar task
    * dissimilar > same task
  * dmPFC subnetwork 는 similar > dissimilar task (replicate 되었음)

### Large Increases in DMN Activity for Task Restarts

* 그 이상으로 restart 와 rest (rest-rest 와 task-rest 의 평균) 의 activity 가 컸다...
* Restart vs. task stay
  * Core 와 MTL 에서는. dmPFC 에서는 아니었음.
* Restart 와 task stay trial 들에서, cue 와 execution 을 더한 average beta 값을 이용해 restart vs. task stay 분석
  * Core, MTL: restart > task
    * Rest > task stay in Core
    * MTL 은 아니었음
  * dmPFC: rest > task stay , 하지만 restart 는 아니었음

### Component ROIs within each subnetwork

* Individual ROIs in each DMN subnetwork 로 ROI 분석도 해 봄
  * Supplimentary figures

### MD activity across trial types

* Greater MD activity for restart
* Greater MD activity in similar > same task
* 2-way repeated ANOVA 
  * Dissimilar, similar, same
  * Core, MD
    * no main effect, but a significant interaction
  * MTL, MD
    * no main effect, but a significant interaction 

### Increased activity at task restart is distinct from prolonged rest activity

* Restart 란 sustained neural activity 나 prolonged hemodynamic response 는 아닌가?
  * Task 앞의 rest 에서 이어져 오는 activity 의 연장...
* 모든 subject 에서 3.88 개의 4 개의 rest 가 이어지는 row 가 있었는데 이를 뽑아냄
* FIR model 로 activity 를 estimate 해봄
* 결과
  * Long rest 다음에 restart 하는 경우에는 통상 rest trial 의 activity 보다 더 높은 DMN activity 가 있었음
  * DMN subnetwork 와 restart, rest 사이에 2 way ANOVA 해보니 marginal main effect 와 significant interaction 이 있었음
  * Restart effect 는 MTL 에서 가장 컸음
  * MD network 에서도 restart 할 때 activity 가 significantly 증가했음

### Individual voxels in DMN and MD regions show sensitivity to both rest and between-domain task switches

