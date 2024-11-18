# 推荐系统实践

项亮：中科院博士

## 第一章 好的推荐系统

### intro

+ 问题：什么是好的推荐系统
	+ 推荐系统是什么
	+ 不同领域的推荐系统
	+ 推荐系统评测指标

### 1.1 什么是推荐系统

关键词总结：信息过载、用户没有明确目的、联系、联系方式

在信息过载（information overload）的时代，辅助信息消费者找到信息的自动化工具，同时也是辅助信息生产者找到用户的工具

推荐系统的基本任务是联系用户和物品，解决信息过载的问题。

推荐系统和搜索引擎对于用户来说是两个互补的工具。搜索引擎满足了用户有明确目的时的主动查找需求，而推荐系统能够在用户没有明确目的的时候帮助他们发现感兴趣的新内容。


推荐系统可以更好的发掘物品的长尾
推荐系统通过发掘用户的行为，找到用户的个性化需求，从而将长尾商品准确地推荐给需要它的用户，帮助用户发现那些他们感兴趣但很难发现的商品。

推荐系统的本质是通过一定的方式将用户和物品联系起来，不同的推荐系统利用了不同的方式：好友、历史兴趣、注册信息

推荐系统就是自动联系用户和物品的一种工具，它能够在信息过载的环境中帮助用户发现令他们感兴趣的信息，也能将信息推送给对它们感兴趣的用户


### 1.2 个性化推荐系统的应用

+ 推荐系统常见组成部分：
	+ 前台的展示页面
	+ 后台的日志系统
	+ 推荐算法系统

#### 1.2.1 电子商务-亚马逊网
[A Guide to Recommender Systems](https://readwrite.com/recommender_systems/)

+ 前台界面：
	+ 推荐结果的标题、缩略图以及其他内容属性
	+ 推荐结果的平均分
	+ 推荐理由
+ 算法：
	+ item-based method：推荐用户之前喜欢的物品相似的物品
	+ 基于facebook好友的推荐
	+ 相关推荐（打包销售）
		+ 购买这个商品的用户也经常购买的其他商品
		+ 浏览过这个商品的用户经常购买的其他商品

#### 1.2.2 电影和视频网站-Netflix、Youtube、Hulu

+ Netflix
	+ 前台界面
		+ 电影标题和海报
		+ 用户反馈模块：播放、评分和不感兴趣
		+ 推荐理由
	+ 算法：基于物品的推荐算法（item-based method）
+ YouTube
	+ 算法：基于物品的算法
+ Hulu
	+ 界面：视频标题、缩略图、视频的平均分、推荐理由和用户反馈模块

#### 1.2.3 个性化音乐网络电台：Pandora、Last.fm、豆瓣

+ Pandora
	+ 算法
		+ 利用专家标注标签计算相似度：音乐基因工程，音乐家和研究人员对歌曲特性进行标注，推荐系统根据标注的相似度推荐用户之前喜欢的音乐相似的阴雨
+ Last.fm
	+ 算法
		+ 利用用户行为计算相似度：记录所有用户听歌记录以及用户反馈，在这一基础上计算不同用户在歌曲上的喜好程度，从而给用户推荐和他有相似听歌爱好的其他用户喜欢的歌曲

#### 1.2.4 社交网络 Facebook、Twitter

+ 主要应用：
	+ 利用用户的社交网络信息对用户进行个性化的物品推荐
	+ 信息流的会话推荐
	+ 给用户推荐好友
+ Facebook
	+ 日志系统：
		+ 用户间的社交网络关系
		+ 用户的偏好信息

#### 1.2.5 个性化阅读：google reader、鲜果网、Zite、Flipboard

+ Google reader
	+ 关注的用户分享的文章
+ Zite
	+ 收集用户对文章的偏好信息
+ Digg
	+ 根据用户的Digg历史计算用户之间的兴趣相似性

#### 基于位置的服务 Foursquare

+ Foursquare
	+ 推荐好友在附近的行为

#### 1.2.7 个性化邮件

+ Tapestry
	+ 分析用户阅读邮件的历史行为和习惯对新邮件进行重新排序

#### 1.2.8 个性化广告

+ 目前广告投放技术
	+ 上下文广告：分析正在浏览的网页投放相关广告
	+ 搜索广告：分析当前会话的搜索记录，判断搜索目的投放相关广告
	+ 个性化展示广告：根据用户的兴趣投放

### 1.3 推荐系统测评

+ 推荐系统参与方
	+ 用户
	+ 内容提供方
	+ 提供推荐系统的网站
+ 好的推荐系统是三方共赢的
	+ 推荐系统满足用户的需求
	+ 推荐系统满足内容提供方需求
	+ 推荐系统本身收集到高质量的用户反馈，不断完善质量
+ 好的推荐系统不仅能够准确预测，还能够拓展用户的视野，发现那些长尾需求

#### 1.3.1 推荐系统实验方法

+ 3种评测推荐效果的实验方法
	+ 离线实验
		+ 步骤：
			+ 通过日志系统获得用户行为数据，并按照一定格式生成一个标准的数据集
			+ 将数据集按照一定的规则分成训练集和测试集
			+ 在训练集上训练用户兴趣模型，在测试集上进行预测
			+ 通过实现定义的离线指标评测算法在测试集上的预测结果
		+ 主要优缺点：
			+ 缺点：
				+ 无法获得商业上关注的指标，如点击率转化率
				+ 离线指标与商业指标存在差距
			+ 优点：
				+ 不需要对实际的系统的控制权
				+ 不需要用户参与
				+ 速度快可以测试大量算法
	+ 用户调查
	+ 在线实验AB测试

#### 1.3.2 评测指标

+ 1 用户满意度
	+ 只能通过用户调查或者在线实验获得
+ 2 预测准确度：可以离线实验计算
	+ 评分预测：通过RMSE和MAE计算
	+ TopN 推荐：通过准确率和召回率度量
+ 3 覆盖率：描述推荐系统对物品长尾的能力。
	+ 定义一：能够推荐出来的物品占总物品集合的比例
	+ 定义二：物品在推荐列表中出现次数的分布
		+ 信息熵：$H = -/sum^{n}_{i=1}p(i)log p(i)$，其中$p(i)$是物品i的流行度除以所有物品流行度之和
		+ 基尼系数：$G = \frac{1}{n-1}\sum^{n}_{j=1}(2j-n-1)p(i_j)$ 其中$i_j$是按照物品流行度p从小到大排序的第j个物品
			+ ![[基尼系数计算原理.png]]
+ 4 多样性
	+ 某一个用户u的多样性：$Diversity = 1 - \frac{\sum_{i,j \in R(u),i \neq j}s(i,j)}{\frac{1}{2} |R(u)|(|R(u)-1}$，其中$s(i,j)$代表物品i和j的相似性，$R(u)$是用户u的推荐列表
	+ 推荐系统整体多样性：$Diversity = \frac{1}{|U|}\sum_{u \in U}Diversity(R(u))$
	+ $s(i,j)$可以有不同的定义
		+ 用内容相似度
		+ 用户系统过滤相似度
+ 5 新颖性
	+ 给用户推荐那些以前没有听说过的物品
+ 6 惊喜度serendipity
	+ 推荐结果和用户的历史兴趣不相似，但让用户觉得满意
+ 7 信任度
	+ 只能通过问卷度量
	+ 提高信任度的两种方法：
		+ 增加透明度
		+ 考虑用户的社交网络信息
+ 8 实时性
	+ 推荐系统的实时性包含两个方面
		+ 满足用户的行为变化
		+ 将新加入系统的物品推荐给用户：冷启动能力
+ 9 健壮性
	+ 抗击作弊的能力
+ 10 商业目标
+ 总结
	+ ![[推荐系统评价指标.png]]
#### 1.3.3 测评维度
+ 用户维度
+ 物品维度
+ 时间维度

## 第2章 利用用户行为数据

+ 基于用户行为的个性化推荐举例
	+ 简单的用户行为统计：热门排行榜
	+ 个性化推荐算法：啤酒与尿布，通过计算机去发现用户行为数据中蕴含的不是那么显而易见的规律。
+ 基于用户行为分析的推荐算法：协同过滤算法

### 2.1 用户行为数据简介

+ 日志：用户行为数据在网站上最简单的存在形式
+ 用户行为：
	+ 按反馈的明确性区分：
		+ 显性反馈行为(explicit feedback)：明确表示对物品喜爱的行为
		+ 隐性反馈行为(implicit feedback)：
	+ 按反馈的方向分：
		+ 正反馈
		+ 负反馈
+ 一种统一表示用户行为的方式（不唯一）(下表)

| 用户行为的统一表示 | |
|-- | -- |
| user id | 产生行为的用户的唯一标识 |
| item id | 产生行为的对象的唯一标识 |
|behavior type | 行为的种类（比如是购买还是浏览）|
| context|产生行为的上下文，包括时间和地点等|
|behavior weight| 行为的权重（如果是观看视频的行为，那么这个权重可以是观看时长；如果是打分行为，这个权重可以是分数）|
|behavior content|行为的内容（如果是评论行为，就是评论的文本；如果是打标签的行为，就是标签）|

+ 有代表性的数据集：
	+ 无上下文信息的隐性反馈数据集：只包含用户id和物品ID
	+ 无上下文信息的显性反馈数据集：用户ID+物品ID+用户对物品的评分
	+ 有上下文信息的隐性反馈数据集：用户ID+物品ID+用户对物品产生行为的时间戳
	+ 有上下文信息的显性反馈数据集：用户ID+物品ID+用户对物品的评分+评分行为发生的时间戳

### 2.2 用户行为分析

#### 2.2.1 用户活跃度和物品流行度的分布

+ 长尾分布
	+ $f(x) = \alpha x^k$
	+ Zipf定律：单词出现的频率按照高到低排序，每个单次出现的频率和它在热门排行榜中排名的常数次幂成反比

#### 2.2.2 用户活跃度和物品流行度的关系

+ 一般认为新用户倾向于浏览热门物品，老用户则会逐渐开始浏览冷门的物品
+ 协同过滤算法：仅仅基于用户行为数据设计的推荐算法
	+ 学术界提出不同的方法：
		+ 基于领域的方法（neighborhood-based）（应用最广泛）
			+ 基于用户的协同过滤算法：给用户推荐和他兴趣相似的其他用户喜欢的物品。
			+ 基于物品的协同过滤算法：给用户推荐和他之前喜欢的物品相似的物品
		+ 隐语义模型（latent factor model）
		+ 基于图的随机游走算法（random walk on graph)

### 2.3 实验设计和算法评测--用离线实验方法评测算法

#### 2.3.1 [数据集](http://grouplens.org/datasets/movielens/)
+ GroupLens提供的MovieLens数据集：6000uid对4000电影共100万条评分
+ 预测目标是：用户会不会对某一部电影评分

#### 2.3.2 实验设计

+ 数据集分为M（取M=8)份，进行M次实验，每次挑选其中一份为测试机，其他M-1份为训练集。训练集建立模型在测试集上评估，M次实验测出的评估指标均值为最终评测指标（防止某次实验的过拟合）

#### 2.3.3 评测指标
+ [[基础知识#召回率（recall）|召回率]]
	+ $R(u)$ 表示对用户$u$推荐N个物品，$T(u)$ 表示用户$u$在测试集上喜欢的物品
	+ $Recall = \frac{\sum_u|R(u) \cap T(u)|}{\sum_u|T(u)|}$
+ [[基础知识#准确率（accuracy）|准确率]]
	+ $Precision = \frac{\sum_u|R(u)\cap T(u)|}{\sum_u|R(u)|}$
+ 覆盖率（coverage）
	+ $Coverage = \frac{|U_{u \in U}R(u)|}{|I|}$
+ 新颖度：推荐列表中物品的平均流行度

### 2.4 基于领域的算法
+ 基于用户的协同过滤算法
+ 基于物品的协同过滤算法

#### 2.4.1 基于用户的协同过滤算法(UserCF)
+ 最古老的，1992年提出被用于邮件过滤

##### 1. 基础算法
+ 两个步骤
	+ 1. 找到和目标用户兴趣相似的用户集合
		+ 计算两个用户的兴趣相似度，$N(u)$表示用户$u$有过正反馈的物品集合，$N(v)$表示用户$v$有过正反馈的物品集合
			+ Jaccard公式相似度：$w_{uv} = \frac{|N(u) \cap N(v)|}{|N(u) \cup N(v)|}$
			+ 余弦相似度：$w_{uv} = \frac{|N(u) \cap N(v)|}{\sqrt{|N(u)||N(v)|}}$
		+ 用户数很大时算法复杂度是$O(|U|*|U|)$, 考虑到很多用户之间$|N(u) \cap N(v)| = 0$ ,所以可以先计算$|N(u) \cap N(v)| \neq 0$ 
			+ 建立物品对用户的倒查表
	
	+ 2.找到这个集合中的用户喜欢的，且目标用户没有听说过的物品推荐给目标用户
		+ 用户u对物品i的感兴趣程度：$p(u,i) = \sum_{v \in S(u,K) N(i)}w_{uv}r_{vi}$
			+ $S(u,K)$和用户u兴趣最接近的K个用户
			+ $N(i)$ 是对物品$i$有过行为的用户集合
			+ $w_{uv}$ 是用户u和用户的兴趣相似度
			+ $r_{vi}$代表用户$v$对物品$i$的兴趣，因为使用的是单一行为的隐反馈数据，所有$r_{vi}  = 1$
```python
def UserSimilarity(train):
	# build inverse table for item_users
	item_users = dict()
	for u, items in train.items():
		for i in items.keys():
			if i not in item_users.keys():
				item_users[i] = set()
			item_users[i].add(u)
	# calculate co-rated items between users
	C = dict()
	N = dict()
	for i,users in item_users.items():
		for u in users:
			N[u] += 1
			for v in users:
				if u == v:
					continue
				C[u][v] += 1
	# calculate final similiarity matrix W
	W = dict()
	for u, related_users in C.items():
		for v, cuv in related_users.items():
			W[u][v] = cuv / math.sqrt(N[u]*N(v)
	return W

def Recommend(user,train,W):
	rank = dict()
	interacted_items = train[user]
	for v,wuv in sorted(W[u].items,key = itermgetter(1),reverse=True)[0:K]:
		for i, rvi in train[v].items:
			if i in interacted_items:
			# we should filter items user interacted before
				continue
			rank[i] += wuv * rvi
	return rank
```

+ 验证：
	+ 评价指标的benchmark：
		+ random算法：每次随机挑选10个用户没有产生行为的物品
		+ MostPopular算法：每次推荐没产生过行为的物品中最流行的10个
	+ 结果：
		+ UserCF的准确率和召回率相对MostPopular提高1倍
		+ K是重要参数，K的调整会影响评测指标
##### 2. 用户相似度计算的改进
+ 改进相似度计算
	+ 余弦公式过于粗糙，因为热门物品的相似不代表兴趣相似（同样买《新华字典》不代表兴趣相同，但冷门物品相似更可能代表相似。
		+ 通过公式$\frac{1}{log(1+|N(i)|)}$ 惩罚了用户u和用户v共同兴趣列表中热门物品对他们相似度的影响(Breese, Heckerman & Kadie, 1998)。
			+ $w_{uv} = \frac{\sum_{i \in N(u)\cap N(v)}\frac{1}{log(1+|N(i)|)}}{\sqrt{|N(u)||N(v)}}$
```python
# User-IIF
def UserSimilarity(train):
	# build inverse table for item_users
	item_users = dict()
	for u,items in train.items():
		for i in items.keys():
			if i not in item_users:
				item_users[i] = set()
			item_users[i].add(u)
	#calculate co-rated items between users
	C = dict()
	N = dict()
	for i,users in item_users.items():
		for u in users:
			N[u] += 1
			for v in users:
				if u == u:
					continue
				C[u][v] += 1/math.log(1+len(users))
	#calculate finial similarity matrix W
	W = dict()
	for u, related_users in C.items():
		for v, cuv in related_users.items():
			W[u][v] = cuv / math.sqrt(N[u]*N[v])
	return W
```

##### 3.实际在线系统使用UserCF的例子
+ 目前UserCF用的不多
+ 最著名的使用者是Digg

### 2.4.2 基于物品的协同过滤算法

+ 模型融合对提高评分预测的精度至关重要
	+ 模型级联融合
		+ 和Adaboost算法类似，每次产生一个新模型，按一定的参数加到旧模型上，是训练集的误差最小化。
	+ 模型加权融合
		+ 基于物品的协同过滤（item-based collaborative filtering）（Greg, Brent & Jeremy, 2003)
##### 1.基础算法
+ UserCF的问题
	+ 用户数目越大，相似度矩阵越来越困难
	+ 基于用户的协同过滤很难对推荐结果做出解释
+ 基于物品的协同过滤（ItemCF）：给用户推荐那些和他们之前喜欢的物品相似的物品
	+ 不利用物品的内容属性计算物品之间的相似度，主要通过分析用户的==行为记录==计算物品之间的相似度。
+ ItemCF两个步骤
	+ 1. 计算物品之间的相似度
		+ $w_{ij} = \frac{|N(i) \cap N(j)|}{|N(i)|}$，其中$N(i)$是喜欢物品$i$的用户数，公式可以理解为喜欢$i$的人有多少比例也喜欢物品
		+ 上面公式会因为$j$是个热门物品导致$w_{ij}$接近1，因此改进为$w_{ij} = \frac{|N(i) \cap N(j)|}{\sqrt{|N(i)||N(j)|}}$ 
			+ 背后假设：每个用户的兴趣都局限在某几个方面，因此如果两个物品属于一个用户的兴趣列表，那么这两个物品可能就属于有限的几个领域，而如果两个物品属于很多用户的兴趣列表，那么它们就可能属于同一个领域
	+ 2. 根据物品的相似度和用户的历史行为给用户生成推荐列表
		+ 用户u对一个物品j的兴趣$p_{ij} = \sum_{i \in N(u) \cap S(j,K)}w_{ij}r_{ui}$
			+ $N(u)$ 用户喜欢的物品集合
			+ $S(j,k)$ 和物品j最相似的K个物品的集合
			+ $w_{ij}$ 是物品j和i的相似度
			+ $r_{ui}$是用户u对i的兴趣，这里令其为1
```python
def ItemSimilarity(train):
	# calculate co-rated users between items
	C = dict()
	N = dict()
	for u, items in train.items():
		for i in users:
			N[i] += 1
			for j in users:
				if i == j:
					continue
				C[i][j] += 1 # 同时喜欢物品i和物品j的用户数
	# calculate finial similarity matrix W
	W = dict()
	for i, related_items in C.items():
		for j, cij in related_items.items():
			W[u][v] = cij / math.sqrt(N[i] * N[j])
	return W
def Recomendation(train, user_id,W,K):
	rank = dict()
	ru = train[user_id]
	for i,pi in ru.items():
		for j, wj in sorted(W[i].items(),key=itemgetter(1),reverse=True)[0:K]:
			if j in ru:
				continue
			rank[j] += pi* wj
	return rank
		
				
```

