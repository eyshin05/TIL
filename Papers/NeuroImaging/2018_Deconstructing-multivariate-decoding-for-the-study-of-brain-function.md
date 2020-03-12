# Deconstructing multivariate decoding for the study of brain function

* Martin N. Herbert, Chris I. Baker
* Oct, 2018
* NeuroImage

## 2. Two sources of confusion

* fMRI 에서 Multivariate analysis 의 적용에 크게 두 가지 confusion 이 있음
  * real world 에 적용하기 위한 ML 과 brain 을 interprete 하기 위한 ML 은 다르다.
    * decoding acc 가 높지 않아도 significant 하게 다르면 됨
  * univariate 과 multivariate 에는 많은 차이가 있는데 해석할 때 이를 엄밀히 구분하지 않고 있다. (statistical frameworks 가 달라야 한다)
    * Activation based philosophy - standard statistical framework - classical univariate analysis
    * Informational based philosophy - information based framework - multivariate decoding
* Importantly, this activation-based philosophy is not limited to univariate analysis, but can be extended to [multivariate analysis](http://www.sciencedirect.com.ssl.libmeta.knou.ac.kr:8010/topics/medicine-and-dentistry/multivariate-analysis), when a pattern of conjoint activation is the focus of study. This philosophy, however, does not underlie the statistical framework of multivariate decoding.
  * conjoint activation 이라고 하는 게 따로 있는 모양 🤔
  * ROI 를 univariate 으로 significant 한 영역을 구해 만든 다음 여기에서 multivariate analysis 를 하는 것은 의미가 있는 일인가?
  * 흠...
  * ML 에서 통상적으로 쓰는 univariate 한 feature selection 의 변형이라고 생각할 수는 있긴 한데...
* 오잉? t-test 쓰지 말고 mutual information 쓰라네.
  * limited data 에서 사용할 수 있는 대안: accuracy
  * subject level 이야기인가?
* Signal 과 noise 언급. 이후에 나오겠지만 signal = mean = univariate, noise = covariance = multivariate

## 3. Differences between classical univariate analysis and multivariate analysis

* Multivariate analysis - justification
  * sensitivity up (더 많은 차이점을 찾을 수 있다. across multiple voxel 에서. house vs. face 등)
  * specificity up (inactivation 도 정보로 보는 것 등)
* 근데 여기에 함의되어 있는 univariate 과 multivariate 의 차이점들...
  * univariate vs. multivariate
    * multivariate analysis allows optimally combining voxeld by taking into account each voxel's contribution to discriminability.
    * covariance between voxels carries additional information
  * uniform vs. non-uniform
    * ROI 안에서의 반응이 uniform 하다 vs. 아니다
    * uniform 하다는 것은 same sign 의 activation 을 이야기한 것
  * directional vs. non-directional
    * directional 은 estimates of activation or deactivation 의 sign 이 중요함
    * F-tests 는 non-directional, 하지만 subject level 에서는 쓰이지 않음
    * multivariate 은 non directional 이고 sign 이 중요한 게 아니라 말하자면 pattern 들의 similarity 가 더 중요..
    * 만약 uniform response 만 존재한다면? MVPA 를 써도 directional 인 셈
    * 혹은 representative response 가 across subject 로 존재한다면, 그 difference 가 direction 이 될 수 있다?
    * discriminability 가 중요하다면 non-directional 쓰면 됨.
    * multivariate 에는 directional / non-directional 둘 다 의미가 있음
  * encoding vs. decoding
    * univariate 은 high-level description of 연구를 제공하기 때문에 encoding 임
      * experimental condition → data
    * multivariate 은 data → condition 
      * 그치만 decoding 이다보니 complete functional description of brain regions 은 제공해주지 않고, accuracy 가 chance ~ 100% 범위가 있으니까 limitation 이 있다는 듯? (noise ceiling) (Naselaris et al., 2011)
    * mutivariate encoding model
      * MANCOVA, CCA, partial least squares 등
      * 그치만 잘 안 쓰이는 여러가지 문제점들이 있음. 
      * 그에 비해 multivariate decoding 은 그런 문제를 피하면서 sensitivity 를 올려준다.
  * within-sample vs. out-of-sample
    * 아, 보니까 이제야 알겠는 부분들이... 있다.
    * univariate 은 encoding 모델이고, degree of freedom 이 덜하니까 데이터를 다 써서 estimate 할 수 있고,
    * multivariate 은 encoding 이 목적이 아니고, dof 가 높아서 (variable 은 많은데 measurement 는 적기도 하고) generalization 목적으로 cross-validation 이 필요함.
      * 그리고...주석 보면 decoding 모델이지만 weight of classifier 같은걸로도 encoding 을 시도할 수 있는데, 이는 information 도 아니고 activateion framework 도 아니라는 점이... (Haufe et al., 2014)
  * activation vs. information
    * information philosopy 는 inactivation (0) 도 정보로 취급
    * variability 도 중요! → 좀 이따 나옴
    * widely distributed population 이 coding 하고 있다는 아이디어
  * What differences are necessary for increased sensitivity and specificity?
    * 6개의 차이점이 있는데 그럼 어떻게 해석해야 하나?
    * multivariate 의 장점에 해당하는 것
      * multivariate: 복셀 여러개로 분석해서 sensitivity 를 올림
      * information: specificity 를 올림
    * 나머지 네 개는 거의 byproduct 이고, 찾아보면 우회할 방법도 있음
    * 위 두개에 대해서
      * discriminability 에만 초점을 맞출건지,
      * variability of response pattern 도 다뤄져야 할지 이야기할 것임

## 4. What is signal and what is noise in multivariate decoding?

* signal: 관심있는 measurement
* noise: 관심 없는 measurement (error, not explained?)
* activation-based philosophy
  * neuro 에서는, 원래 noisy 해서 statistical model 로 formalize 해야 useful approximation 을 구할 수 있는 것으로 취급되어 왔음
  * condition-independent noise
    * variance, covariance, non-normal error
  * condition-dependent noise
    * variance, covariance, confound
  * signal strength: size of the difference between mean parameters
  * signal-to-noise ratio: ratio of difference of means : noise
* multivariate decoding (information-based philosophy)
  * linear classifier 의 weight vector: a **large absolute weight** reflects a stronger contribution of that voxel to the final classification.
  * 각 voxel 의 information 에 contribution 하는 정도가 존재
    * 그러므로, 평균에서 차이가 noise 가 아니라, 여기에서는 differences in the data distribution can be information for a classifier.
    * covariance 자체만으로는 discrimination 이 안되지만, correlated noise 를 줄임으로써 classification 성능을 높일 수 있다는 연구 결과도 있음.
  * signal-to-noise ratio 는 information based 에서는 accuracy 로 번역될 수 있음
  * weight parameter 는 discriminability 를 직접 반영하지는 않지만,
    * 절댓값은 그 voxel 이 discrimination process 에서 다른 voxel 들과 함께 얼마나 쓸모 있게 (usefulness) 쓰이는지를 직접 반영함

* The collision of signal, noise, and information
  * example 3 개를 보면서 data generation → classifier 로 classification 하면서 1) weight parameters = signal strength, 2) accuracy = signal-to-noise ratio 인지 볼 것임
  * Example 1 (Fig 3. B. 1)
    * Signal + 0 covariance Gaussian noise
    * covariance 가 없고 gaussian noise 인 경우: GNB 가 best
      * weight = how much signal there is 이므로 weight = signal strength 임
      * accuracy 도 signal-to-ratio 를 잘 반영함
  * Example 2 (Fig 3. B. 2)
    * Signal + Gaussian noise with covariance
    * 예를 들어 두 voxel 이 negative covariance 가 있어서 하나가 증가할 때 하나가 감소한다면, 의 상황.
    * Bayse-optimal classifier 는 Fisher linear discriminant 임
    * 이 경우 weight 는 usefulness 를 나타내긴 하지만 signal strength 는 아니지만 combination of signal and noise 이긴 함.
    * accuracy 는 여전히 signal-to-noise ratio 를 반영함
  * Example 3 (Fig 3. B. 3)
    * No signal + heteroskedastic Gaussian noise
    * 신호는 없고 노이즈밖에 없음.. covariance 도 없음.. 
    * Linear SVC 는 이걸 구분할 수 있다;; 왜냐면 두 condition 에 따라 두 voxel 의 noise 가 다르기 때문..
    * d-prime 이나 area under the curve 써도 마찬가지임.
    * accuracy != signal-to-noise 이고 (왜냐면 걍 noise 빨이니까), signal 이 아니라 noise 가 정보를 가지고 있는 것임.
    * weights != signal 이지만 important of voxel (usefulness) 는 맞음.
    * out-of-sample 에서 테스트 했을 때 accuracy 가 높다는 건 이 경우에는 noise 도 stability 를 가진다는 것임.
  * Example 3 는 어떻게 해석해야 하는 케이스?
    * neural 이 맞다면.. processing strategy 를 나타낼 수 있음
    * 한편 non-neural factor 도 noise correlation 에 영향을 줄 수 있는데 분리하기 어려울 수도 있다
      * head motion, respiratory cycle 등
    * 그래도 non-neural factor 가 condition 에 영향을 받는 것?

## 5. Interpretation of multivariate decoding

