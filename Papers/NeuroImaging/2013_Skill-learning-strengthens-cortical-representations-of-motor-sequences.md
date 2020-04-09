# Skill learning strengthens cortical representations of motor sequences

* Tobias Wiestler, Jörn Diedrichsen
* Jul, 2013
* eLife

---

## Abstract

* Increase 는 neural recruitment 일 수 있고, decrease 는 unimportant 를 의미하거나 more efficient representation 일 수도 있다.
  * 해석하기 어렵잖아
* 제안
  * Motor-skill acquisition 하면 이것이 highly distinguishable activity patterns 를 만든다는 것을 보여줄것임
* Multivariate pattern analysis 했더니 untrained, trained 둘 다 distinguish 되었지만 (M1/S1), SMA 등을 보면 trained 가 좀 더 잘 classified 되었다.
* Skill learning → specialized neuronal circuits 를 발달시킴 → 빠르고 정확한 movement (without brain activity increase)



## Introduction

* Hypothetical learning-related chances in activity patterns associated with two sequences of five finger-presses.
  * 처음엔 한 손가락 누르기에 따라 encoding 되는 영역이 있다면, 같은 버튼을 다른 sequence 로 누를 때 같은 영역이 activate 될 것임
  * 학습이 진행되면서 이 영역의 뉴런들이 develop 되면 (efficient 하게 encoding 되면서...) 한 손가락 하나씩 encoding 되는게 아니라 두개씩 묶어서 encoding 하게 되고... 그러면 서로 다른 sequence 로 누르더라도 겹치지 않는 영역이 생길 것임
    * Transition 이라고 하고, M1, SMA 에서 이런 현상이 있다는 single cell recoding 연구 결과가 있음
  * 이렇게 점점 학습이 진행될수록 dissociation 됨
    * The development of more distinct cortical activation patterns associated with each individual sequence



## Results

### Behavioral correlateds of skill learning

* Experimental design
  * As fast as possible
* Generalization
  * Untrained  sequence &  untrained hand
  * Pre-test vs. post-test 비교해보니 significantly drop 했음

### Average activation is reduced for trained relative to untrained sequences

* Univariate analysis
  * sequence-related activation increase 영역을 잡기 위해 rest 랑 비교해서 significant 한 영역을 찾음
    * left S1 이랑 M1, dorsal & ventral premotor, SMA, IPS, occipital-parietal junction 에서 나옴
      * right 에서도 나왔는데 Verstynen et al., 2005 레퍼했음
    * 그림에서 overlap 영역 그린게 흥미롭군.. 어떻게 binary 가 아니게 그렸지
      * thresholding 해서 그린거고 group mean 데이터를 그린건 알겠는데... alpha 값으로 두고 그렸나?
      * 어쨌든 t-value 표시해줬으니 별로 중요하진 않은듯
  * Trained vs. untrained
    * Our task instructions regarding speed were designed such that the error rate for the two sequence types during scanning was exactly matched (see methods)
      * We instructed participants to decrease their MT if they had an error-rate of less than 20% and to focus on accuracy if the error rate was larger than 20%. This speed-accuracy instruction served to keep error-rates stable across the experiment.
      * To correct for possible pre-test differences between sequences, we calculated a regression between the pre-test difference (x-variable) and the post-test differences (y-variable) and tested whether the intercept was significantly different from zero.
      * dorsal premotor 랑 IPS 에서만 lower activity 가 발견됨
        * trained sequence 에서 덜 관여하거나, trained sequence 가 더 efficiently encode 되어 있기 때문?
        * left 가 더 decreased 되었음

### Multiple motor and premotor regions show requence-specific activation patterns

* LDA classifier 는 Duda et al., 2001 를 레퍼하네 근데 뭔가 되게 이상한 방법
* Surface-based searchlight analysis 결과
  * highly significant: right M1, bilateral PMd, IPS
  * also significant: PMv, SMA, pre-SMA
* 결과 해석
  * Finger movement 를 different timescale 로 encoding 한 것일까? Unlikely.
    * first, the spatial distribution of classification accuracy for sequences differs substantially from that for single finger movements ([Diedrichsen et al., 2012](https://elifesciences.org/articles/00801#bib8)), especially in the ipsilateral, left hemisphere.
      * Single finger movement 를 decoding 하면 central sulcus 쪽이 나오는데, sequence 는 premotor 랑 parietal 이 나왔음
    *  Secondly, to test the idea of different temporal activation profiles directly, we defined six bilateral regions of interest.
      * Temporal response 의 main component 를 뽑아서 보니까, first componenet 는 canonical activation profile 이었고, 나머지는 temporal variation 을 설명하고 있었다.
      * 여기서 first temporal component 로 classification 해보니 accuracy 가 가장 높았다.
        * 다른 temporal component 넣어주면 acc 감소 → 정보 없음 (?) 의 가능성
  * Instruction / execution related activity 중 어느 것일까?
    * Temporal analysis
      * S1 은 2번째 TR (2.7-5.4s) 로 classification 했을 때 above chance 였지만,
      * 다른 영역들은 3번째 TR 이후부터 above chance
      * 아마 SMA 는 부분적으로 instruction related activity 일지도?
    * OPJ 나 PMd 같은 영역들 (visual..?) 에서도 accuracy 가 높았다
      * 글자가 안 보이는 시기에도 높았음
  * 1, 2, 3 dimension 으로 압축해서 classification 했을 때 만약 single component 로만 패턴이 영향을 받는다면 1 dimension 에서도 accuracy 가 높을텐데 모든 ROI 가 3-dimension 이어야 accuracy 가 올라갔음
    * we can conclude that sequences are encoded in unique spatial activation patterns, rather than in differently scaled versions of a single pattern.

### Sequence-specific activation patterns become more distinct with learning

* MVPA 결과 learning-dependent change 가 있었던 영역: SMA, pre-SMA

* Dimensionality analysis 로 sequence-specific pattern 이 separate 한지, overlap 되는지 살펴봄
  * Untrained sequence 가 unique 하지만 basically random activity pattern 이었음
  * This means that any two activation patterns exhibit some non-overlapping features, but also share a specific amount of shared activity.
* Could these accuracy differences be an artifact of performance differences during the scan?
  * While trained and untrained sequences were executed at slightly different speeds and average forces ([Table 1](https://elifesciences.org/articles/00801#tbl1)), the individual differences in overall classification accuracy did not correlate with the difference in MT (p=0.75), force (p=0.51), or error rate (p=0.21). 
  * We tested how well a linear classifier could discriminate between each set of four sequences based on MT, average force, or error rate, either considered in isolation or in any combination as separate features. 
    *  None of the seven combinations showed a significant difference between trained and untrained sequences (all *t*(15) < 1.15, p>0.269; see [Table 1](https://elifesciences.org/articles/00801#tbl1)).
  * Furthermore, when including the differences in classification accuracy based on all behavioral variables as a covariate, the accuracy difference based on fMRI patterns remained significant, *t*(15) = 2.56, p=0.01.
  * Thus, the higher classification accuracy for trained sequences was not a simply a consequence of more stable behavioral performance.



## Discussion

