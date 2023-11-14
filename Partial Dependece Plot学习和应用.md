# PDP

## 定义

- 偏依赖图（Partial Dependence Plot，简称PDP或PD图）展示了机器学习模型预测结果中一个或两个特征的边际影响效果([[Friedman 2001.pdf]])。
- 作用：预测结果与特征的关系是线性、多元还是复杂的
## 原理
+ $\hat{f}_S(x_S) = E_{X_C}[\hat{f}(x_S,X_C)] = \int \hat{f}(x_S,X_C)dP(X_C)$ 
	+ 其中$x_S \cup X_C = X$，$X$ 是所有的特征集合，$x_S$是要探究与预测结果关系的特征
+ $\hat{f}_S$使用训练集的均值计算$\hat{f}_S(x_S) = \frac{1}{n}\sum_{i=1}^n \hat{f}(x_S,x_C^{(i)})$ （Monte Carlo method：通过不同抽样来逼近）
## Limitation

+ 假设各个特征之间是相互独立的

## 应用
### code：使用xgboost+pdp画图分析相关性

+ [data_analyst_tool](https://github.com/akasiro/data_analyst_tool.git)
## 附录

- [8.1 Partial Dependence Plot (PDP) | Interpretable Machine Learning (christophm.github.io)](https://christophm.github.io/interpretable-ml-book/pdp.html)
- [科研中的部分依赖图（PDP）绘制_樊川_Minus Type的博客-CSDN博客](https://blog.csdn.net/boycetoon29/article/details/117658130)
- [4.1. Partial Dependence and Individual Conditional Expectation plots — scikit-learn 1.3.0 documentation](https://scikit-learn.org/stable/modules/partial_dependence.html)