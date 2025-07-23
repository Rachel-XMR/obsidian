---
LINK:
  - "[[Neural Networks 神經網絡]]"
---





![](PICTURE/Deep%20Learning%20for%20NLP/ee6b7f6dd041eb7eac4ae20590b90865_MD5.jpeg)



![](PICTURE/RNN/b9dc718f47189f7383f5b87c38d1575f_MD5.jpeg)





## Sequence Learning in Feedforward Neural Network 

![](PICTURE/RNN/8d8c406bbf568bfd2459a93094caa689_MD5.jpeg)



## SRN (Simple Recurrent Network ) / Elman Network 
-  Simplified: extra layer of memory/context units (copy)
- Character and Word predictions




### Vanishing and Exploding Gradient Problems

![](PICTURE/RNN/d0dc4a977dc8cabb8c7b9c8982b4cf4a_MD5.jpeg)

Each gradient of the hidden state h with respect to the previous one is further decomposed as the product of gradients of the current $h_t$ state against $h_{t-1}$
• Gradient < 1, product gets smaller and smaller (vanishing)
• Gradient > 1, product gets bigger and bigger (exploding)
• Gradients from far-away steps do not contribute
anything to the learning process
• Not learning long range dependencies
• Simple RNNs cannot learn long term dependencies

















