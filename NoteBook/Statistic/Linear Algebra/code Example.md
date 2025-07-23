---
LINK:
  - "[[Statistic]]"
  - "[[Linear Algebra]]"
---



### 散點圖
```python
# Make a plot as part of EDA
plt.figure(figsize=(4,4))
plt.scatter(x,y,marker='.',c='grey',s=5,edgecolors="None") # 散點圖
#sns.kdeplot(data=data,x='balloffootcircumference',y='balloffootlength',cmap="Reds") # Old syntax: sns.kdeplot(X,Y,cmap="Reds")
plt.xlabel("Ball of Foot Circumference")
plt.ylabel("Ball of Foot Length")
plt.tight_layout()
sns.kdeplot(data=data,x='balloffootcircumference',y='balloffootlength',cmap="Reds")
plt.show()
#plt.savefig('./feet.pdf',format='pdf')
```


### calculate correlation matrix 
[Linear Regression as  Correlation Maximisation 最大相關性](Statistic/Linear%20Algebra/Linear%20Regression%20as%20%20Correlation%20Maximisation%20最大相關性.md)
```python 
R = np.corrcoef(x,y)
```




### calculate eigensystem 
[Eigensystem 特征系統](Statistic/Linear%20Algebra/Eigensystem%20特征系統.md)
```python
# Calculate the Eigensystem
la, vv = np.linalg.eigh(R)
```


### standardization
[Standardisation 標準化](Statistic/Standardisation%20標準化.md)
```python 
# Create standardised data to visualise PCs on
Z1 = (x-np.mean(x))/np.std(x)
Z2 = (y-np.mean(y))/np.std(y)
stdf = pd.DataFrame({'Z1':Z1, 'Z2':Z2}) # Create a dataframe with the standardised variables
```




### 縮放特征向量
```python
# Make a plot as part of EDA

plt.figure(figsize=(4,4))

plt.scatter(Z1,Z2,marker='.',c='grey',s=5,edgecolors="None") # Old syntax: c=[0.5,0.5,0.5]

sns.kdeplot(stdf,x='Z1',y='Z2',cmap="Reds") # Old syntax: sns.kdeplot(Z1,Z2,cmap="Reds")

#   縮放三倍
plt.plot(
    -3*np.sqrt(la[1])*np.array([0,vv[1,0]]),
    -3*np.sqrt(la[1])*np.array([0,vv[1,1]]),
    c=[1,1,1],
    linewidth=3
)

plt.plot(
    3*np.sqrt(la[0])*np.array([0,vv[0,0]]),
    3*np.sqrt(la[0])*np.array([0,vv[0,1]]),
    c=[1,1,1],
    linewidth=3
)

plt.plot(
    -3*np.sqrt(la[1])*np.array([0,vv[1,0]]),
    -3*np.sqrt(la[1])*np.array([0,vv[1,1]]),
    c=[0,0.6,0],
    linewidth=2
)

plt.plot(
    3*np.sqrt(la[0])*np.array([0,vv[0,0]]),
    3*np.sqrt(la[0])*np.array([0,vv[0,1]]),
    c=[0,0.6,0],
    linewidth=2
)

plt.xlabel("Standardised Ball of Foot Circumference")

plt.ylabel("Standardised Ball of Foot Length")

plt.xlim([-4, 4])

plt.ylim([-4, 4])

plt.tight_layout()

plt.show()

#plt.savefig('./feet_pcs.pdf',format='pdf')
```











