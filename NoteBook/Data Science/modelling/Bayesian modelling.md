---
LINK:
  - "[[Data Science]]"
  - "[[modelling]]"
  - "[[Statistic]]"
---


# Binomial model  二項式模型
是一種離散時間金融模型 用來估算期權 (option) 價格

## 基本想法：
- 把資產價格的變化視為一個隨機過程，在每個小時間隔中，資產價格只能上升 (up) or 下降(down)
- 隨著時間的推進，這些上下的變化構成一顆二叉樹 (binomial tree) 也叫資產價格樹
- 然後用 **風險中性概率(risk-neutral probability)** 反推期權的價值 

> [!tip]+  公式：
> $$
> p = \frac{e^{r\Delta t} - d}{u - d}
> $$
> 
> - 資產當前價格：SSS
>    
> - 單位時間內價格上升倍數：uuu
>   
> - 單位時間內價格下降倍數：ddd
>     
> - 無風險利率（年化）：rrr
>     
> - 每單位時間長度：Δt\Delta tΔt
>     
> - 期權期限：TTT，分成 NNN 期（也就是時間分割成 N 份）
>     
> - 風險中性機率（risk-neutral probability）
> 





# Hierarchical model  分層模型

## Bayesian uncertainty estimation
![](PICTURE/Bayesian%20modelling/9e47cf836bb0c36b0a7153d39512c316_MD5.jpeg)

![](PICTURE/Bayesian%20modelling/5e24bee192661db806ee67890dc5ab1e_MD5.jpeg)

- Probability distributions as model building blocks 概率分佈作為模型構建塊
	- need to understand the math part 理解數學部分
	- continuous vs discrete 連續與離散
	- observation model, likelihood, prior 觀察模型，可能性，先驗
	- constructing bigger models 構建更大的模型
- Computation
	- need to be able to compute expectations:
		$$
		\mathrm{E}_{\theta|y}[g(\theta)] = \int p(\theta|y)g(\theta)d\theta
		$$ 
	- when analytic solutions are not available, computational approximations with finite number of function evaluations 當無法獲得解析時，可使用有限次數的函數進行求值
	- grid, importance sampling, Monte Carlo, Markov chain Monte Carlo
- Workflow
	- steps of model building, inference, and diagnostics    模型構建 推理 和診斷













# Bayesian decision analysis  貝葉斯決策分析

[Bayesian probability theory](Statistic/Bayesian%20probability%20theory.md)













































