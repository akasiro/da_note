






屏蔽单列单关作者消费，看一下关注分发在公域应占10%的合理性
分消费侧和生产侧实验
+ 消费侧屏蔽50%和100%看对用户打开频次使用时长的影响
+ 生产侧按作者屏蔽单关流量看对作者生产和活跃情况的影响
# 0 时间切片直接比较（最常见）
# 1 染色分析（trigger analysis）
+ 适用场景：实验实际生效人群占分流分群渗透率低，实验效果被其他用户稀释
+ 具体原理：
	+ 只对实验组和对照组的子集（实际触发了这些功能的流量）进行统计分析
	+ 具体根据对于触发子集粒度可以分为：
		+ 用户染色分析：一旦用户触发了功能就进入样本
		+ session染色分析：只保留触发功能的session（适用渗透更低的功能）
+ 优势：
	+ 提供较小的方差提高统计效力
	+ 可以无偏的估计整体效果
+ 实验操作：实验时创建一个与实验组相同流量的对照染色组，染色组模拟实验发生过程，但是不执行实验策略。
+ 估计整体效果：
	+ 由于染色分析得到的是生效用户的效果，需要计算得到整体效果
	+ 对于可加指标$\Delta_{overall} = \Delta_{trigger} * \frac{N_{trigger}}{N}$
	+ 对于比例指标$\Delta_{overall} = \Delta_{trigger} * \frac{N_{trigger}}{N}*(\frac{trigger分母}{分母})$
	+ 这是无偏估计
+ 参考文献：[Diluted Treatment Effect Estimation for Trigger Analysis in Online Controlled Experiments](https://alexdeng.github.io/public/files/wsdm2015-dilution.pdf)












# 2 DID
+ 使用场景：AA不平
+ 
# 3Matching

# 4 累积入组分析
+ 使用场景：
	+ 用户入组后特征会被策略影响导致时间切片上拿到的特征实验组和对照组不平
	+ 需要对用户特征拆维度，但是这些特征会随着时间或策略变化

