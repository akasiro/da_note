## 1、实验概述
+ 实验目的
+ 实验设计
+ 实验预期
+ 实验链接
+ 实验分组
+ 分析周期
+ 实验范围

## 2、实验前分析

### 2.1 计算样本量（power anlaysis）

==等待补充方法==

| table of error types | | $H_0$ is | |
|-- | --| -- | -- |
| | | True | False |
| Decision | accept | correct (true negative)| Type 2 error (false negtive) (probability = $\beta$) |
| | reject | Type 1 error (false positive)(probability = $\alpha$) | Correct (true positive) |

Type 1 error: significance
Type 2 error: power of  a test = $1-\beta$
$power = Pr(reject\ H_0|H_1\ is\ true)$

### 2.2 pre-AA

核心指标AA diff

###  2.3 设计方案

Bootstrap vs. t test

## 3、核心指标及趋势

## 4、人群细拆（多维分析多重检验矫正）
### 4.1 Introduction
+ 1 为什么要细拆
	+ 用户对于相同实验处理反应不同是广泛存在的（异质实验效果HTE），希望对用户异质性进行洞察，知道***为什么***指标移动或***谁***对改动更感兴趣。
+ 2 细拆有什么问题
	+ 出现多重比较(Multiple comparisons problem)导致虚假发现率增加(false discovery rate, FDR)（人话：直接人群细拆进行简单的分组比较，不管是否存在真正的异质性，总能很容易找到处理效果与平均群体差异很大的子群体）
		+ **[Multiple comparisons problem](https://en.wikipedia.org/wiki/Multiple_comparisons_problem)**：多组统计推断同时进行时产生。例如一个样本中同时检验多个变量，或者一个样本细拆成多个维度的子群体。
			+ 产生的原因是，例如：在完全没有任何效果的AA实验中，在显著性水平5%的情况下，每20个子人群就会出现一个显著人群，这是完全随机的结果，而非异质实验效果（HTE）
		+ **[FDR](https://en.wikipedia.org/wiki/False_discovery_rate)**：$FDR = E[Q]$
			+ $Q = V/(V+S)$ ，V表示false discovery的群体数，S表示true discovery的群体数。用Q表示对于所有我们检测出有差异的子群体，实际没有差异但是被检测出有差异的子群体的比例
			+ 假设有m个假设检验，这些假设检验的FWER (family-wise error rate)
				+ $\bar\alpha = 1 - (1- \alpha_{per\ comparison})^m$ （翻译：1-全对的概率）（假设各个检验独立）
				+ $\alpha_{per\ comparison} = 1 - (1-\bar\alpha)^{1/m}$ 
				+ 
| | $H_0$ is true | $H_A$ is true | total |
| -- | -- | --| -- |
|test is declared significant | V | S | R |
| test is declared non-siginifant | U | T | m-R|
|total | $m_0$ | $m-m_0$ | m |



### 4.2 方法
+ 优化目标：**FDR**
	+ $FDR = E[Q]$
	+ false discover rate，用Q表示对于所有我们检测出有差异的子群体，实际没有差异但是被检测出有差异的子群体的比例
+ 目标变量transformed outcome
	+ $Y_i^* = Y_i^{obs} \times \frac{T_i - p}{p(1-p)}$ 
		+ $Y_i^{obs}$ 用户i的观测值
		+ $T_i$ 用户是否在实验组
		+ p 实验组所占的流量比例
		+ 这个公式好处是可以将$Y_i^*$作为因变量进行回归，得到的结果就是在对应人群上的CATE(conditional average treatment effect)。证明见[Recursive partitioning for heterogeneous causal effects | PNAS](https://www.pnas.org/doi/10.1073/pnas.1510489113)
+ 实现步骤
	+ 假设有n个用户，p个待检测的子群体
	+ 第1步：构建一个n\*p的矩阵X，如果第i个用户属于第j个子群体，则$X_{i,j} = 1$
	+ 第2步：计算每个用户的transformed outcome $Y_i^*$，再计算$Y = Y_i^* - ATE$
	+ 第3步：将Y对X回归，得到参数和p-value
	+ 第4步：根据BH procedure (Yoav Benjamini and Yosef Hochberg. 1995. Controlling the False Discovery Rate: A Practical and Powerful Approach to Multiple Testing.)进行选取，挑出在控制了FDR情况下仍旧显著的子人群。
	+ 