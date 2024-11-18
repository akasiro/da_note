## 【统计类】问dislike率什么时候收敛
+ 背景：已知人工策略在dislike率高的时候生效，但是生效的时候基本已经是分发的后期了，视频本身已经没有流量了，想要==利用dislike率这个信号加速发现劣质视频提前打压==
+ 思路：
	+ 由统计可以知道大盘vv粒度上dislike率，可以讲这个是为每一次观看（vv）发生dislike的可能性
	+ 那么视频的dislike率问题可以视为一个伯努利分布服从$B(n,p)$ 其中n为视频观看数（vv），p为大盘dislike率
	+ 大样本伯努利分布可以近似为正态分布，均值为p，方差为pq
	+ 我们可以认为当某个播放数对应的dislike率超过95%的置信区间上限即为远高于均值，可能是劣质视频，由此问题被转化为==在每个播放次数（vv）下正常dislike的上限为何==
	+ 这个问题就可以直接用python画图
	+ 假设p = 0.00028
+ 代码
```python
from math import sqrt
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import matplotlib.ticker as ticker
df = pd.DataFrame({
'n':np.linspace(5,5000,5000-4)
})
p = 0.00028
df['ucb'] = df['n'].apply(lambda x:p + 1.96 * sqrt(p*(1-p)/x))
fig,ax = plt.subplots(1,1,figsize = (20,10))
sns.lineplot(data= df,x = 'n',y = 'ucb',ax = ax)
```
+ 结果
![[Pasted image 20240130111349.png]]
+ 结果解读
	+ 可以发现曲线在1000左右收敛，可以就是在播放次数达到1000左右的时候上限基本确定，当dislike率超过0.002的时候就是劣质视频
+ 最后补充case说明