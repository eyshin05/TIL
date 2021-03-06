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

* 어떤 복셀이 dissimilar 만큼 rest 에 sensitive 한지 알아보려고 함
* ROI 안에서, Rest > task, dissimilar > same task 둘 다 uncorrected p < 0.05 수준으로 significant 한 영역을 찾음
* Core 는 18.3 %, MTL 은 26.9 %, dmPFC 는 11.7 %, MD 는 10.8 %

### DMN and MD activity patterns distinguish task domains

* 드디어 multivariate pattern analysis 에 도달하였다.... orz
  * 이 논문에서도 크게 중요한 부분은 아닌가 싶고
* Cue period activity 로, task type 을 classification 수행함.
* linear SVC
* 아, 이제야 이해가 갔는데...
  * Task type 은 trial type (총 6개) 이고, 
  * 6 * 5 / 2 해서 pair 가 15 개라고 했는데 이게 class type 을 두 개씩 엮어서 train / test 를 각각 수행해서 accuracy 를 구했다는 뜻이었군;
  * 그래서 chance level 도 50%...
  * Decoding accuracy 는 비교가 목적이니까 말은 되나... 평균 낼 거리도 많으니까 좀 더 stable 할 테고...
    * (하지만 누군가 나에게 이렇게 하라고 하면 싫어했을 것 같음;)
* ROI 별로 구한 후 Subnetwork 안에서 평균 냄
* Decoding accuracy 자체가 높진 않지만 significant 했음
* Target 두 개가 within-domain 인지 between-domain 인지 나눠서 averaging
* 결과
  * Between domain 인 경우 모든 network 에서 significant 했음
  * Within domain 인 경우 MD 만 significant 했음
  * Between vs. Within mean accuracy 비교했더니 core 랑 MTL 은 between 이 significantly high
  * 2-way repeated ANOVA (subnetwork, task pair domain) 해 봄
    * 데이터는 subnetwork 별로 평균내서 구했음
    * Subnetwork, domain 다 main effect 있었고 interaction 도 있었음.

## Discussion

* Our finding
  * Crittenden et al., 2015 결과가 replicate 되었음
  * Rest 와 비교했을 때 새로운 결과도 찾았음
* Crittenden et al., 2015 에서는 이렇게 증가한 DMN activity 가 relaxation of the previous task set 인지, establishment of the next 인지 알 수 없었는데 우리는 rest 를 도입해서 연구했다
  * Previous cognitive focus 가 relaxing 될 때에도 (task-rest pair), 새로운 것이 제시됐을 때에도 (rest-task pair) activity 는 강했다
* DMN function
  * 이 연구 결과를 볼 때 DMN function 을 internal 이나 self-directed cognition 으로 생각하면 설명하기 힘들고, (내부 환경)
  * Switch related activity 로는 설명할 수 있음 (외부 환경적 요소)
  * 짧은 rest 에서 mind-wandering 등이 나타난다는건 이상함
  * Task 시작할 때에도 activity 가 높은 것도 이상함 (DMN 이 rest related activity 라면)
* Many results in the literature (of the DMN)
  * Broad features of a current scene, episode or context, including spatial surroundings (Hassabis and Maguire 2007, 2009; Howard et al. 2014), 
  * time (Addis et al. 2007; Andrews-Hanna et al. 2010), 
  * social aspects of self and others (Frith and Frith 2003; D’Argembeau et al. 2005), etc
  * “Situation model” by Ranganath and Ritchey (2012)
  * 이건 context encoding 에 대한 얘기고, 또한 implementation and control of current cognition 에 대한 것이기도 함
  * 어떤 role 을 수행하기에  Context representation 을 가능하게 하는 걸까
    * 현 context 에서 어떤 옵션이 가능한지에 대한 참조
    * 지금 하는 행동의 구성 요소를 묶어서 대안으로 가능한 행동보다 이게 더 나음을 제시 (의역 파티)
* 우리의 제안
  * 인지가 unfold 될수록 (전개될수록?) context representation 의 상대적인 중요성이 왁스칠되고 줄어들어서, 그래서 DMN 이 활동하는 것이 아닐가
  * Context representation 은 rest 할때는 강하고 (? strong at rest),
    * 어쩌면 약간은 cognitive resource 로 경쟁하고 있을수도 있음
  * 이렇게 표현된 컨텍스트가 때로는... 내부적으로 향한 생각같은 걸수도 있지만, 
    * 단순히 자기 주변 환경의의 representation 이  강화되었기 때문일 수도 있음
  * 아니면 보완적으로, 집중하고 있는 작업의 operation 이 점차로 embedding 되어서,
    * Context representation 이 점차 줄어들고,
    * 선택적인 주의에 의해 억압되어 별로 상관 없는 것이 되었기 때문일수도
    * Context representation 이 약화 → losing ourselves → task-negative 와 task-positive 의 anti correlation(Fox, Snyder, et al. 2005; Kelly et al. 2008)
  * 근데 새 작업이 주어지면 이 context representation 이 다시 약화되어서 다시 DMN activity 증가하고 “becoming aware of our surroundings” 하게 된 것이 아닐까
* 여기에 일치하는 여러 논문들
  * MTL 은 perceptual processing hierarchy 랑 memory 기능
    * HF 등... 장면에 대한 기억 뿐만 아니라 perceptual processing of scenes
    * MVPA 와 memory
      * DMN 으로 MVPA 해봤더니 TV 프로그램 에피소드를 다시보거나 기억할 때 acc 가 높았(겠지)
      * 청각 서술로 기억하는 연구도 MVPA results 가 있었고,
      * Nonspatial task contexts 연구도 있었고...
  * grid cell 도 있고...

