## store-sales-time-series-forecasting
### 資料分析


Column A | Column B 
---------|----------
商品類別 | 33 種
店家數量 | 54間
訓練資料時間 |2017-04-01至2017-08-15 


### 同商品在不同店的銷售總量
圖內可看出同商品在不同店中銷售價格差異相當大。

![hw3-1](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-1.png)

### 同一間店中不同商品的銷售總量
圖內可看出不同商品在不同店中銷售價格差異相當大

![hw3-2](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-2.png)
 	
### 長時間油價影響銷售平均
圖為2013至2017年的油價與銷售平均，在長時間軸中確實有重要的影響，但因我們取短時間的資料做訓練，所以我們不拿油價當作特徵。

![hw3-3](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-3.png)

### 節日不影響整體銷售
我們將節日用重要性給予1-6分，圖中可看出，整體銷售並未因節日有顯卓影響。節日僅對少數商品有影響。

![hw3-4](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-4.png)

(下圖：某商品對日期的售量) 

![hw3-5](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-5.png)

### 星期規律影響銷售
我們將星期標示1~7(一~日)從圖中可以發現，六日的銷售量較好。

![hw3-6](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-6.png)

### 分析資料結論
從資料分析中，發現不同店家對應不同商品，銷售價都有相大的變化，而RNN是時間序列顯示建模能力較強的神經網絡，所以依照RNN模型特性，我們認為將店家對應的商品分別用簡單的RNN模型做訓練(共54 x 33個模型)，就能達到相當好的成績。 


**Training set (54 x 33個 training set)**

每筆資料：特徵：2017-04-01至2017-08-15 每日的價格
		  長度：10天

### Model
**structure**
1.	keras 的sequential model使用了 1層的RNN  (如圖)
2.	epoch = 1、batch_size =1

**Loss function**
使用 mean_squared_error

**Optimizers**
使用 adam

![hw3-7](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-7.png)

### 訓練預測結果比對
![hw3-8](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-8.png)
### 測試與測結果比對
![hw3-9](https://github.com/OuTingYun/DeepLearning-NCU/blob/main/img/hw3-9.png)
