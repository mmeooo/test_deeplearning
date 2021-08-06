# Deep Learning

tensorflow: keras (https://www.tensorflow.org/api_docs/python/tf/keras?hl=ko)

---

## Classification
차원이 있는 데이터 처리

* Output Layer 
  * y_train의 unique값이 3개 이상 -> activation= 'softmax'
  * y_train의 unique값이 2개(binary) (ex.긍정/부정) -> activation = 'sigmoid' 

* Hidden Layer : activation = 'relu'

* Output Layer
  * Dense : y_train의 unique값의 개수
  * model.add - loss
    * 연속형 -> loss = mae (절대값) : mean(abs(y_true - y_pred), axis=-1)

    * regression -> loss = mse (오차값) :  mean(square(y_true - y_pred), axis=-1)

* Gadget
  * model.compile - loss
    * binary classification -> loss = binary_crossentropy : f.keras.metrics.binary_crossentropy( y_true, y_pred, from_logits=False, label_smoothing=0)

    * over 3 classification -> loss = sparse_categorical_crossentropy : tf.keras.metrics.categorical_crossentropy( y_true, y_pred, from_logits=False, label_smoothing=0 )

    * one-hot encoding 하기 싫을 때 -> loss = sparse_categorical_crossentropy : tf.keras.metrics.sparse_categorical_crossentropy( y_true, y_pred, from_logits=False, axis=-1)


---


## Artificial Neural Network

* 뉴런의 작동 방식 
  * 여러 개의 시냅스로 부터 받은 여러 개의 신호(양 *시간) 를 합침. 이 값이 특정 임계점을 넘어가면 신호가 다음 시냅스로 전달됨.
  * `Activation Function` 으로 도식화 : 임계점 넘어가면 1, 아니면 0을 리턴 

* 논리 
  * AND, OR : `Single Layer Network` 
  * XOR (두 개의 input이 같지 않으면 true) : `Multi Layer Network`



## BackPropagation

* Multi Perceptron : `Input Layer,  Hidden Layer, Output Layer` 으로 구성된 머신러닝의 학습 구조. 각 층은 가중치 값으로 연결되어 있음

* BackPropagation 오차역전법 : Output layer에서 계산한 값과 내가 원하는 Target 값의 차이를 구한 후,  그 오차값 ( ex. MSE )을 뒤로 전파해가며 각 노드가 가지고 있는 변수 (가중치)를 조정하는 방법 

 ->  `Chain Rule` : 미분. 최종값 변화량에 기여하는 각 변수의 기여도를 알 수 있음

#### Step
1. 오류 계산 : 실제 출력에서 얼마나 멀리 출력되는지 계산
2. 최소 오류 : 오류가 최소화되었는지 확인
3. 매개 변수 조정 : 오류가 크면 매개 변수(가중치 및 편차)를 조정.



## Recurrent Neural Network

* 입력과 출력을 Sequence 단위로 처리하는 모델.  시간에 따라 변화하는 데이터를 학습할 때 활용  
  * `Hidden Layer`에서 `Activation Function`를 통해 나온 결과값을 `Output Layer` 에 보내거나,   
  * 다시 `Hidden Layer` 의 다음 계산의 입력으로 보내 재귀적으로 참조. (데이터 순환)
  -> 스스로를 반복하면서 이전 단계에서 얻은 정보를 지속시킴
  
  
## LSTM
* RNN의 한 종류. 긴 의존 기간(문맥)을 필요로 하는 학습을 수행
