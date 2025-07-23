---
aliases: 
LINK:
  - "[[Data Science/Neural Networks 神經網絡/Neural Networks 神經網絡]]"
---



CNN是專門設計來處理圖像的神經網絡，可以自動提取圖像的特征，並完成分類、檢測、分割等任務


核心想法：
- 保留圖像的空間結構 (像素位置)
- 使用局部連接和權重共享來大幅度減少參數數量 (避免想MLP那樣暴增)


## 結構 


```css
[輸入圖像]
   ↓
[卷積層 Convolution Layer]
   ↓
[激活函數 ReLU]
   ↓
[池化層 Pooling Layer]
   ↓
（可重複多次）
   ↓
[全連接層 Fully Connected Layer]
   ↓
[輸出層（分類結果）]

```






## Feature Detectors

![](Pasted%20image%2020250519010144.png)

![](PICTURE/Neural%20Networks%20%E7%A5%9E%E7%B6%93%E7%B6%B2%E7%B5%A1/5f58ee32e1fb71974b8dd37cedacbcfa_MD5.jpeg)
當隱藏單元檢測到與內核圖像相似的圖像塊時，會出現最大輸出響應






![](PICTURE/CNN%20Convolutional%20Neural%20Networks/5d38140a56e7eb632f1389f3cdbd3aca_MD5.jpeg)



## Example：a typical CNN Architectures

![](PICTURE/CNN%20Convolutional%20Neural%20Networks/ac1888e1f1aff9b8177af65c206a5a72_MD5.jpeg)




# Faster R-CNN 
![](PICTURE/CNN%20Convolutional%20Neural%20Networks/22cb1c3816f3e07867104ca384d0ccba_MD5.jpeg)



### Segmentation 
![](PICTURE/CNN%20Convolutional%20Neural%20Networks/d924d7c82ae4b7ca2fc38ee9b6731912_MD5.jpeg)

![](PICTURE/CNN%20Convolutional%20Neural%20Networks/27bb441e6c089c00a8825d3799da1b4b_MD5.jpeg)






































































