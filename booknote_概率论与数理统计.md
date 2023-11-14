## 第1章 随机事件与概率
### 1.1 随机事件
#### 一、概率论的研究对象：随机现象
#### 二、随机现象可研究的原因：统计规律性

+ 统计规律性：随机现象在大量重复出现时所表现出来的量的规律
+ 研究的方式：随机试验（对随机现象的观察）
	+ 可重复性
	+ 可观察性
	+ 随机性

#### 三、样本空间  $\Omega$：所有样本点$\omega$（随机试验可能的结果）的全体

#### 四、随机事件：具备某一指定的可观察特征

#### 五、事件的集合表示

#### 六、事件间的关系与运算

+ 包含：$A \subset B$; $\emptyset \subset A \subset \Omega$
+ 相等：$A = B$
+ 并：$A \cup B$
+ 交集：$A \cap B$（或$AB$）
+ 差：$A-B$
+ 互不相容：$AB = \emptyset$
+ 对立事件：$A\bar{A} = \emptyset, A \cup \bar{A} = \Omega$ 
+ 完备事件组：对于有限个事件 $A_1,A_2,...,A_n$ ，如果$A_iA_j = \emptyset, i \neq j,i,j = 1,2,...$ 并且$\cup_i A_i = \Omega$

#### 七、随机事件的运算

+ 求和：
	+ 交换律：$A\cup B = B \cup A$
	+ 结合律：$(A \cup B) \cup C = A \cup (B \cup C) = A \cup B \cup C$
+ 求交：
	+ 交换律：$A \cap B = B \cap A$
	+ 结合律：$(A \cap B) \cap C = A \cap (B \cap C) = A \cap B \cap C$
+ 混合运算
	+ 第一分配律：$A \cap (B \cup C)) = (A \cap B) \cup (A \cap C))$
	+ 第二分配律：$A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
+ 求对立事件
	+ 自反律：$\overline{\bar{A}} = A$
+ 和及交对立事件
	+ 第一对偶律：$\overline{A\cup B} = \bar{A} \cap \bar{B}$
	+ 第二对偶律：$\overline{A\cap B} = \bar{A} \cup \bar{B}$

### 1.2 随机事件的概率