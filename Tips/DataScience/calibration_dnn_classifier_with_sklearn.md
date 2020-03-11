# 딥러닝 classifier 를 sklearn 으로 calibration 하기

calibration 에 대해서 잘 몰랐는데, https://www.facebook.com/deeplearningtalk/posts/600293953656233 여기에 링크된 유튜브 동영상을 보고 알게 되었다.

즉, 모델의 softmax 레이어에서 나온 0.9 가 정말로 90% 의 확률을 의미하고 있다면, 0.9 가 나온 답변들을 모아서 실제 answer 를 살펴보았을 때 그 답이 90% 는 맞아야 한다는 이야기다.

작업하고 있는 classifier 가 실제로도 그런지 궁금해서 그림을 그려보니 처참한 수준이었다. 아마도 unbalance 데이터를 balance 맞추게 하기 위해 sampling 해서 넣었기 때문일 수도 있고, 뭐 워낙 multi class 라고 말하기 미묘한 문제였기 때문일수도 있고, 논문에서 말하듯 모델이 overfitting 되어서일수도 있다고 생각했다.

그래서 논문 외에도 다른 calibration 방법에 대해 찾아보니, sklearn 에 [`CalibratedClassifierCV`](http://scikit-learn.org/stable/modules/generated/sklearn.calibration.CalibratedClassifierCV.html#sklearn.calibration.CalibratedClassifierCV) 이 있다는 것을 알게 되었다. 그래서 한번 이 기능을 사용해보기로 마음 먹음.



## 방법

1. 내 DNN classifier 를 sklearn estimator 로 wrapping 한다
2. sklearn 기능으로 calibration 한다 (cv="prefit" 으로 주면 이미 학습된 classifier 를 calibration 할 수 있다.)



## Sklearn estimator wrapping 코드

[Rolling your own estimator in scikit-learn](http://scikit-learn.org/stable/developers/contributing.html#rolling-your-own-estimator) 를 보면 estimator 를 wrapping 하는 방법이 나와있다. 이 부분을 참고해서 만든 뼈대는 다음과 같다.

```python
from sklearn.base import BaseEstimator, ClassifierMixin
from sklearn.calibration import CalibratedClassifierCV
from sklearn.utils.validation import check_X_y, check_array, check_is_fitted
from sklearn.utils.multiclass import unique_labels

class DNNMulticlassClassifier(BaseEstimator, ClassifierMixin):
    def __init__(self, model=None, classes=None):
        self.model = model
        self.classes_ = classes
        # 다른 옵션이 있으면 변경
        
    def fit(self, X, y):
        X, y = check_X_y(X, y)
        
        # 아무런 일도 하지 않는 fit 메소드
        self.X_ = X
        self.y_ = y

        return self
    
    def predict(self, X):
        check_is_fitted(self, ['X_', 'y_'])
        X = check_array(X)
        
        # inference 코드를 작성
        # 저의 경우는 그냥 함수 하나 만들어서 따로 뺐습니다
        probs = inference(self.model, X)
        
        return self.classes_[np.argmax(probs)]
        
    # rolling your own estimator 에는 없는 메소드지만
    # 이 메소드를 override(?) 해 줘야 calibration 이 돌아갑니다
    def predict_proba(self, X):
        check_is_fitted(self, ['X_', 'y_'])
        
        probs = []
        
        for x in X:
            # inference 코드 작성
            # batchfy 하면 좀 더 효율적으로 진행할 수 있겠죠
            prob = inference(self.model, x)
            probs.append(prob)
        
        return np.array(probs)
```

이런 식으로 만든 sklearn classifier 는 다음과 같이 instance 를 만들면 된다.

```python
# model 은 가져온 DNN classification 모델
# class_list 는 model output 의 class list
classifier = DNNMulticlassClassifier(model, class_list)

# model fitting
classifier.fit(X=np.zeros((len(class_list), 1)), y=class_list)

# inference
classifier.predict('test해 보고 싶은 data를 넘겨준다')
```



##  Calibrated Classifier CV 로 calibration

sklearn 의 calibration classifier CV 를 이용하여 calibration 을 해 보자. [document](http://scikit-learn.org/stable/modules/generated/sklearn.calibration.CalibratedClassifierCV.html#sklearn.calibration.CalibratedClassifierCV) 를 보면 알겠지만, method 는 sigmoid 와 isotonic 을 제공해주고 있다.

> Can be ‘sigmoid’ which corresponds to Platt’s method or ‘isotonic’ which is a non-parametric approach. It is not advised to use isotonic calibration with too few calibration samples `(<<1000)` since it tends to overfit. Use sigmoids (Platt’s calibration) in this case. 

sigmoid method 로 calibration 을 수행하는 예제 코드는 아래를 참고.

```python
# X_valid: valid dataset 에서 X values. shape 은 (sample 크기, variables) 임. np.array 타입.
# y_valid: valid dataset 에서 target values. shape 은 (sample 크기) 임. np.array 타입.

calibration = CalibratedClassifierCV(classifier, method='sigmoid', cv='prefit')
calibration.fit(X_valid, y_valid)
```



## Visualization 해서 확인하기

calibration curve 를 그리기 위해 각각의 클래스를 binary 라고 생각하고 그림을 그리려고 했는데, sklearn 에서 함께 제공되는 [`sklearn.calibration.calibration_curve`](http://scikit-learn.org/stable/modules/generated/sklearn.calibration.calibration_curve.html#sklearn.calibration.calibration_curve) 를 쓸까 하다가, 그냥 예전에 썼던 코드를 좀 수정해서 visualization 해 보기로 했다.

```python
def print_calibration_data(bins):
    bin_size = len(bins)
    bin_width = 1 / bin_size
    bin_pad = bin_width / 2
    
    print('bin 크기:', [len(b) for b in bins])
    print('total 해당 클래스 데이터:', sum(sum(b) for b in bins))
    
    # 파란색은 가장 이상적인 line
    plt.bar([(j) / bin_size for j in range(bin_size)], 
            [(j+bin_pad) / bin_size for j in range(bin_size)], 
            width=bin_width, alpha=0.5, label='expectation')
    
    # 빨간색은 실제 line
    plt.bar([(j) / bin_size for j in range(bin_size)],
             [np.mean(b) if b else 0 for b in bins], 
             width=bin_width, alpha=0.5, label='actual', color='red')
    
    plt.show()
```

```python
# X_train: test dataset 의 inputs
# y_train: test dataset 의 outputs

# bin_size 는 몇개의 bin 으로 데이터를 나눌것인지 이다. probability 인 경우 0~1 사이의 값일것이므로 bin_size 가 10 이면 0~0.1, 0.1~0.2, ..., 0.9~1.0 의 10개의 bin 이 만들어진다.
bin_size = 10
y_pred = calibration.predict_proba(X_test)

for i, class_name in enumerate(class_list):
    bins = [[] for i in range(bin_size)]
    
    for preds, actual in zip(y_pred, y_test):
        bin_idx = min(int(preds[i] * bin_size), bin_size-1)
        
        if actual == class_name:
            bins[bin_idx].append(1)
        else:
            bins[bin_idx].append(0)
                
    print(class_name)
    print_calibration_data(bins)
```

그림으로 확인하니 확실히 calibration 이 좀 된 것 같다. 다행!


## 저장 & 불러오기
tensorflow model 을 그대로 pickling 하지 않는 방법으로 하려면 아래처럼 저장하고 불러올 수 있다.

```python
backup1, calibration.base_estimator =calibrationsigmoid.base_estimator, None
backup2, calibration.calibrated_classifiers_[0].base_estimator = calibration.calibrated_classifiers_[0].base_estimator, None

with open('calibration.pkl', 'wb') as file:
    pickle.dump(file=file, obj=calibration)
```

```python
# classifier 는 따로 로딩 후 붙여준다
with open('calibration.pkl', 'rb') as file:
    calibration = pickle.load(file=file)
    
calibration.base_estimator = classifier
calibration.calibrated_classifiers_[0].base_estimator = classifier
```



## 참고

* [테리의 딥러닝 토크 #33. On Calibration of Modern Neural Networks](https://www.facebook.com/deeplearningtalk/posts/600293953656233)
* [Rolling your own estimator in scikit-learn](http://scikit-learn.org/stable/developers/contributing.html#rolling-your-own-estimator)

