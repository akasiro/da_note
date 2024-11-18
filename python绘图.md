```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import matplotlib.ticker as ticker

# mac中文字体显示
plt.rcParams['font.sans-serif'] = ['Arial Unicode MS']
# 默认字体大小
plt.rcParams.update({'font.size': 20})
# 构造数据
df2 = pd.DataFrame({
    'a':np.linspace(0,10,11),
    'b':np.random.normal(0,1,11),
    'c':np.random.uniform(size=11)
})
df2['b'] = df2['a'].apply(lambda x:2*x+1+np.random.normal(0,1))
# 画图，使用subplots确定布局
fig,ax = plt.subplots(1,1,figsize = (20,10))
fig.set_size_inches(20,10)
# 多条折线图
sns.lineplot(data=df2,x='a',y = 'b',ax=ax,label='b',color = 'green')
sns.lineplot(data=df2,x='a',y = 'c',ax=ax,label = 'c')
# 格式配置
ax.set_title('test',fontsize = 40)
ax.set_ylabel('ylabel',fontsize = 20)
ax.set_xlabel('xlabel',fontsize = 20)
ax.legend(fontsize = 20)
ax.tick_params(labelsize = 20,axis='x')

# 数据标签
for r in df2.itertuples():
    _x = getattr(r,'a')
    _y = getattr(r,'b')+0.1
    _l = '{:.2f}'.format(_y)
    ax.text(_x,_y,_l,fontsize = 10,ha = 'center')
# 坐标轴
ax.set_xlim(0,500000)
ax.xaxis.set_major_locator(ticker.MultipleLocator(1))
# 定义格式化函数 
def to_percent(y, position): 
	return f'{y * 100:.0f}%' 
# 设置 y 轴的格式化器 
ax.yaxis.set_major_formatter(ticker.FuncFormatter(to_percent)) 
# 设置 x 轴的格式化器（如果需要） 
ax.xaxis.set_major_formatter(ticker.FuncFormatter(to_percent))
# 辅助线
ax.axhline(y=0.002,color='r')
ax.axvline(x=150000,color='r')
# 网格线
ax.grid(axis='x')

```

[[绘制带置信区间的图]]

[[箱线图]]