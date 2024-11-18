## 染色分析
1、定义染色群体（实验组对照组）
2、稀释效果



背景：低覆盖率功能

certain dilution formula is then applied to translate the estimated effect in triggered analysis back to the original all up population

  

难点：比例型指标（Ratio metrics or double averaging metrics)，
e.g.
$session人均成功率 = avg(session成功率)$ ，$session成功率 = 成功session数/用户session数$

  

微软经验值：在搜索引擎里功能渗透低于0.1%为低覆盖率功能，一般渗透低于20%就需要提供trigger analysis

  

Definition of triggering

+ 一般来说我们能够知道实验组真实生效的以及对照组可能生效的单元

  

session-trigger 和user-trigger的区别在于假设处理效果会不会对后序没有发生策略对session生效

  

Effect Dilution

$\Delta_{Tr}(X)$ ：标X 实验组对照组染色人群diff
N :用户数
对于user- trigger ：
formula 1: $\Delta_{overall-user\_trriger} = \Delta_{Tr} \frac{N_{Tr}}{N}$

假设treatment只在染色人群生效，非染色人群效果为0
