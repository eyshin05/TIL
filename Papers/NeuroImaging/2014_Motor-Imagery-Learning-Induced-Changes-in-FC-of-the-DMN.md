# Motor Imagery Learning Induced Changes in Functional Connectivity of the Default Mode Network

* Ge Ruiyang, Zhang Hang, Yao Li, Long Zhiying
* Jul 2014
* IEEE Trans Neural Syst Rehabil Eng

---

## Abstract

* It is unclrear how motor learning affects the (resting) DMN
* Motor imagery learning 실험
* Graph theory method 로 DMN 사이에서 interregional connectivity 를 구함
  * 학습 후 increase 했음
* ICA 로 activity 를 구함
  * 그대로였음
* Execution rate 의 변화랑 랑 lateral parietal cortex 의 activity 사이의 변화랑 negative correlation 이 있었음.
* DMN 이 motor learning 에 관여하는 것은 interregional connectivity 의 변화로 설명될 수 있지 않나, DMN 이 behavioral performance 를 개선하는 데 어떤 역할을 하는게 아닌가... 싶다.



## Introduction

* Motor skill learning 의 정의
  * Motor skill learning refers to the process by which movements are executed more smoothly and accurately with practice.
* DMN
  * ... plays a role in introspective function which linked to episodic memory, attention, and working-memory.
  * Activities within the DMN might reflect ongoing offline processing of information from prior experiences and learning.
  * It is noteworthy that the relevance of the **DMN dysfunction** has been emphasized in several neuropsychiatric diseases, such as **Parkinson's disease**, autism and Alzheimer's disease et al. 
* Mental imagery task
  * 블록을 머릿속에서 rotate 한 모양을 맞추는 것 (mental rotation) 포함..한 비슷한 task 들인듯
  * Mental imagery task 연구들에서 DMN 이 activate → DMN 은 supra-modal imagery network 이지 않을까?
  * Generally, motor learning can be carried out through mental imagery practice.
    * Because DMN plays an important role in the mental imagery tasks, it is possible to alter DMN activity for motor learning **through mental imagery practice**.
* Graph theory, ICA 얘기
* This study
  * DMN 의 변화 → mental imagery 를 통한 motor learning

## Mehods

### Participants

* 26 오른손잡이
  * 14 명: motor imagery learning
  * 12 명: control
* Movement Imagery Questionnaire, vividness of Movement Imagery Questionnaires 라는게 있네

### Experiomental Procedures

1. Familiarization stage
2. Pre-learning fMRI scanning stage
3. Two-week motor imagery learning stage (or control)
4. Post-learning fMRI scanning stage

* Motor sequence learning 이고 sequence 는 정해져 있음... 

* Task
  * Motor execution: 실제로 하는거
  * Motor imagery: 상상으로 하는거

### Behavioral Data Analysis

* mean execution rate 이랑 mean execution error rate 을 비교함

### Image Preprocessing

* Rest 를 SPM8 으로... commom procedure... 

### Independent Component Analysis

* 이것도 multivariate pattern analysis 네 싶고
* Prior to the ICA analysis, two-step principal component analysis (PCA) was used to reduce data dimensionality, and the number of ICA components was set to 38 for both groups to preserve at least 99.99% of the original variance on average. 
* Then the data were decomposed by group-ICA using the Infomax algorithm.

* A two-sample t-test was performed on the individual DMN component of all subjects to examine whether there were differences of DMN before the training between the two groups.

* The mean Goodness of Fit of each component across all subjects was obtained.
  * Goodness of fit: The **goodness of fit** of a statistical model describes how well it fits a set of observations.
* The power spectrums of the time-course corresponding to the selected DMN of each subject were calculated.
* One-sample t-tests were performed on the experimental and control groups respectively to determine the group DMN maps of the pre-learning and post-learning resting run. 

* The DMN maps were compared between pre- and post-learning scans using paired t-tests for the experimental and control groups respectively. 

### ROI selection

### Graph Theory Analyses

* Functional connectivity 를 graph measure 로 구함



## Results

* Behaviore change 를 봤더니 control 은 차이 없었는데 실험한 그룹은 차이가 있었다
* Total connectivity degree 는 lMTL, rLPC 에서 significantly 증가했다
* Connectivity degree 의 alteration (노드와 노드 간) 는 
  * lMTL 에서는 rLTC, rLPC, dMPFC 가 significantly 증가
  * rLPC 에서는 LMTL, rLTC, dMPFC 에서 significantly 증가
* Alteration 과 performance improvement 와의 correlation
  * 실험한 그룹에서 rLPC (r=−0.555,p=0.039) 나머지는 significant 하지 않았음

* 나온 애들 정리
  * Core network
    * 없음
  * dmPFC network
    * LTC, DMPFC
  * MTL network
    * MTL, LPC 가 여기? (pIPL??)

## Discussion

https://ieeexplore.ieee.org/mediastore_new/IEEE/content/media/7333/7001725/6849455/6849455-fig-5-source-large.gif

그림 귀엽다

* Motor learning 과 DMN FC 와의 관계
  * The performance of the motor execution task was significantly improved by the motor imagery training and the alteration of the behavioral performance was correlated with the increment in activity of the lateral parietal region.
  * Motor imagery training increased the functional connectivity between the lateral parietal, medial temporal and lateral temporal regions within the DMN.

* ICA 분석 결과
  * Comparison between pre- and post-learning revealed that the motor learning did not induce any significant alteration of the activity in the brain regions of the DMN for either the experimental or control group.
* DMN 의 role
  * The DMN was generally characterized by episodic memory recollection, manipulation of conceptual knowledge, creativity, problem solving, prospection, and planning.
  * & supra-modal imagery network
  * It could be altered through cognitive training tasks
  * A series of cognitive processes can participate in motor imagery training, including retrieving the pre-learned sequence with its contextual scenarios from memory, generating and enhancing the conceptual knowledge about the numerical sequence, translating the movement patterns into spatial coordinates, etc..
  * Due to the putative role of the MTL, LPC, and LTC in memory, spatial cognition, and conceptual knowledge processing, respectively, these brain regions have been reported to be engaged in the motor imagery task.
  * MTL might work with the LPC to participate in the encoding and retrieval of the spatial information.

* ICA & graph 로 분석한 DMN
  * Motor imagery learning could not lead to differential contributions of particular regions to the DMN, but could lead to changes of their interactions.
* Behavioral correlation
  * This result is consistent with the previous study that found the changes of the DMN engagement were negatively correlated with performance increases after training.
    * D. D. Jolles, M. A. van Buchem, E. A. Crone, S. A. Rombouts, "Functional brain connectivity at rest changes after working memory training", *Hum. Brain Mapp.*, vol. 34, no. 2, pp. 396-406, Feb. 2013.
  * LPC 는 spatial processing 과 연관되어 있을 가능성
    * Based on the neural efficiency hypothesis that **faster-performing individuals show less neural activity than slower performers**, we inferred that training may result in smaller increases in the activity in LPC for participants who have greater ability in integrating spatial information with conceptual knowledge of the numerical sequence and the digit actions.
* There are several limitations in this preliminary study.



## Conclusion

