## Digit-Recognition 

1.	資料分布

![data](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw2-1.png)

2.	檢查資料是否有缺

![missing data](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw2-2.png)

### 資料前處理

**1. 增加mnist訓練資料**:

增加訓練資料能夠有效的提升正確率，因此選擇使用keras 提供的 mnist 資料集加入訓練資料。

**2. 對訓練資料做標準化**:

訓練資料皆為 `0~255` 的整數，我們將他們全部除255，將數值限制於 `0~1` 之間，可以加快訓練的速度並增加準確度。

**3. One hot encoding**:

我們要預測的答案為 `0~9`，因此我們對標籤做one hot encoding，分成10類

### Model

**structure**

我們選擇 keras 的sequential model使用了4層 convolution layer + 2層max pooling layer + 1層Dense layer + Output layer  (如圖)

**Activation function**

Convolution layer , Dense layer 使用relu, Output layer使用 softmax 來預測每個數字的機率

**Loss function** - 使用 cross-entropy 

**Optimizers** - 使用 adam

**Kernel_init** - 使用 random_normal 

**Call back** -  使用ReduceLROnPlateau 來獲得更精準預測結果

![model](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw2-3.png)

### 預測結果

![resulit](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw2-4.png)
