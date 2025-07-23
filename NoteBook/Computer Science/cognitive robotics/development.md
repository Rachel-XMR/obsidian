---
LINK:
  - "[[cognitive robotics]]"
  - "[[Computer Science]]"
---



# NAOqi Python API 
這個需要實際的robot 進行連接操作


http://doc.aldebaran.com/2-5/ref/python-api.html 

https://gist.github.com/knaggita/9015d2f282421e61c38aac18e62c0472
https://aldebaran.com/en/support/kb/nao6/downloads/nao6-software-downloads/ 



http://doc.aldebaran.com/2-5/nao/webpage.html

這個只能用2.7版本的 不能使用3.11等版本 
需要下載 2.7版本的
該內容不能使用pip安裝 到Naoqi 網站去下載 zip文件後解壓到python路徑下並添加到path

## 初始化 python 


```bash
# 安裝 pip
py -2.7 -m ensurepip
# 更新pip
py -2.7 -m pip install --upgrade pip
#安裝ipykernel模組 
py -2.7 -m pip install ipykernel
#註冊成Jupyter可用內核 
py -2.7 -m ipykernel install --user --name python2 --display-name "Python 2.7"
```



https://blog.csdn.net/qq_22820121/article/details/81083894


### 創建環境
 單獨設立一個環境

```bash
conda create -n nao_env python=2.7
conda activate nao_env
pip install naoqi
pip install opencv-python==3.4.5.20
pip install numpy
pip install ipykernel
python -m ipykernel install --user --name nao_env --display-name "Python 2.7 (nao_env)"
set PYTHONPATH=D:\naoqi-sdk\lib
pip install https://pypi.python.org/packages/source/n/naoqi/naoqi-2.1.4.13.tar.gz

```




```python 
import sys
sys.path.append(r"C:\Python27\naoqi-sdk\lib") #把手動解析的文檔位置添加進去
#check：
import naoqi
print("NAOqi module imported successfully!")
```

![](PICTURE/development/1322e7c7e3f0adf67930b9e0a388b9f4_MD5.jpeg)

















