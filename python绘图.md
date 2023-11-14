```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
# 构造数据
df2 = pd.DataFrame({
    'a':np.linspace(0,10,11),
    'b':np.random.normal(0,1,11),
    'c':np.random.uniform(size=11)
})
df2['b'] = df2['a'].apply(lambda x:2*x+1+np.random.normal(0,1))
# 画图，使用subplots确定布局
fig,ax = plt.subplots(1,1)
fig.set_size_inches(20,10)
# 多条折线图
sns.lineplot(data=df2,x='a',y = 'b',ax=ax,label='b',color = 'green')
sns.lineplot(data=df2,x='a',y = 'c',ax=ax,label = 'c')
# 格式配置
ax.set_title('test',fontsize = 40)
ax.legend(fontsize = 20)
ax.set_ylabel('ylabel',fontsize = 20)
ax.tick_params(labelsize = 20,axis='x')
# 数据标签
for r in df2.itertuples():
    _x = getattr(r,'a')
    _y = getattr(r,'b')+0.1
    _l = '{:.2f}'.format(_y)
    ax.text(_x,_y,_l,fontsize = 10,ha = 'center')
```

[[绘制带置信区间的图]]