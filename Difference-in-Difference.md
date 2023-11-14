==本质是一种固定效应==

原理
$Y_{it} = \alpha_0 + \alpha_1du + \alpha_2dt + \alpha_3dt*du + \epsilon_{it}$
其中：
$i$ 样本
$t$ 时间
$du$ 是否为实验组，是为1
$dt$ 处理前后（aa期还是ab期），处理后（ab期）为1

| | aa期 | ab期 | difference|
|--|--|--|--|
| 实验组| $\alpha_0 + \alpha_1$|$\alpha_0 + \alpha_1 + \alpha_2 + \alpha_3$|$\alpha_2 + \alpha_3$|
| 对照组|$\alpha_0$| $\alpha_0 + \alpha_2$| $\alpha_2$|
|difference| $\alpha_1$|$\alpha_1 + \alpha_3$| $\alpha_3$|

所以 Difference-in-difference 为$\alpha_3$

在具体的应用中由于直接用变量识别个体和时间的固定效应，将替换$du$ 和$dt$
实际应用的公式为
$Y_{it} = \alpha_0 + \lambda_i + v_t + \alpha_3dt*du + \epsilon_{it}$
其中：
$\lambda_i$ 为个体的固定效应
$v_t$ 为时间固定效应

在分桶世界实验中使用的原理为
$Y_{itk} = \alpha_{ki} + \lambda_k + v_t + \alpha_3dt*du + \epsilon_{kit}$
其中
k代表桶编号
t代表时间
i代表组
$\lambda_k$ 分桶固定效应
$v_t$ 时间固定效应
$\alpha_{ki}$ 组间固定效应
$\alpha_3$ did效应
假设：$\epsilon_{kit}$ 独立同分布：
+ 在给定的t，不同分桶的$\epsilon_{kit}$ 独立同分布
+ 在给定的分桶ki，不同时间维度上$\epsilon_{kit}$ 独立同分布




reference
https://zhuanlan.zhihu.com/p/48952513