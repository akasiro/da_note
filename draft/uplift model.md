## 一、原理：预测treatment的增量值

基于因果推断“反事实”的逻辑，将base组视为exp组的“反事实”，增量就是treatment带来的。

> Uplift models用于预测一个treatment的增量反馈价值。举个例子来说，假如我们想知道对一个用户展现一个广告的价值，通常的模型只能告诉我们用户在展示广告后的购买意愿很强，但事实很有可能是他们在被展示广告之前就已经很想购买了。Uplift models聚焦于用户被展示广告后购买意愿的增量。
> [一文读懂uplift model - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/100821498)

预测值：$Lift = P(buy|treatment) - P(buy|no\_treatment)$

![[uplift_custom_type.png]]
理想条件下，我们希望能够识别每个人在这个图里的类别，只将产品卖给persuadables。但是现实是，我们对每个人只能进行一种treatment。因此只能借助统计工具和machine learning计算==相似的人== 的平均水平。uplift可以给每个个体介于（-1,1）之间的lift score，来确定个体所属的类型。

## 二、实现方案
+ 要想准确的使用uplift模型，需要调整损失函数(loss function)是lift最大化。现有的loss function方案里：
	+ Leo Guelman’s  [R Uplift](https://cran.r-project.org/web/packages/uplift/index.html) package:  A wonderful, commonly-used and fully-featured implementation，但是loss function很难求最优，运行速度慢
	+ machine learning algorithms in scikit-learn：beautifully optimized
	+ Transformed outcome (pylift包使用的方法)：牺牲了一点运行速度，allows you to simply transform your outcome label and leverage scikit-learn algorithms
## 2.1 The transformed outcome tree




[About Wayfair | Pylift: A Fast Python Package for Uplift Modeling](https://www.aboutwayfair.com/data-science/2018/10/pylift-a-fast-python-package-for-uplift-modeling/)

