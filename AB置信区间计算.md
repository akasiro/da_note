## delta method
https://arxiv.org/pdf/1803.06336

好的，让我们从中心极限定理推导到Delta方法的完整推导过程，特别是应用于求解两个组均值百分比差异的场景。

### 1. 中心极限定理

中心极限定理表明，对于一个包含 \( n \) 个独立同分布的随机变量 \( X_1, X_2, \ldots, X_n \) 的样本，当 \( n \) 足够大时，其样本均值 \(\bar{X} = \frac{1}{n} \sum_{i=1}^n X_i\) 的分布近似服从正态分布，即：

$$
\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right)
$$

其中，\(\mu\) 是总体均值，\(\sigma^2\) 是总体方差。

### 2. 两个独立样本均值之差的分布

考虑两个独立样本 \(X_1, X_2, \ldots, X_n\) 和 \(Y_1, Y_2, \ldots, Y_m\)，其对应的样本均值分别为 \(\bar{X}\) 和 \(\bar{Y}\)。根据中心极限定理，我们有：

$$
\bar{X} \sim N\left(\mu_X, \frac{\sigma_X^2}{n}\right), \quad \bar{Y} \sim N\left(\mu_Y, \frac{\sigma_Y^2}{m}\right)
$$

因此，两样本均值之差 \(\bar{X} - \bar{Y}\) 的分布为：

$$
\bar{X} - \bar{Y} \sim N\left(\mu_X - \mu_Y, \frac{\sigma_X^2}{n} + \frac{\sigma_Y^2}{m}\right)
$$

### 3. 引入Delta方法

假设我们要研究的函数是均值百分比差异：

$$
f(\mu_X, \mu_Y) = \frac{\mu_X - \mu_Y}{\mu_Y}
$$

我们需要对这个函数进行泰勒展开，主要考虑一阶导数。

### 4. 计算导数

首先计算 \(f(\mu_X, \mu_Y)\) 对 \(\mu_X\) 和 \(\mu_Y\) 的一阶偏导数：

$$
\frac{\partial f}{\partial \mu_X} = \frac{1}{\mu_Y}, \quad \frac{\partial f}{\partial \mu_Y} = -\frac{\mu_X}{\mu_Y^2}
$$

### 5. 应用泰勒展开

在点 \((\mu_X, \mu_Y)\) 处对 \(f(\mu_X, \mu_Y)\) 进行泰勒展开，仅保留一阶导数项：

$$
f(\bar{X}, \bar{Y}) \approx f(\mu_X, \mu_Y) + \frac{\partial f}{\partial \mu_X} (\bar{X} - \mu_X) + \frac{\partial f}{\partial \mu_Y} (\bar{Y} - \mu_Y)
$$

代入导数：

$$
f(\bar{X}, \bar{Y}) \approx \frac{\mu_X - \mu_Y}{\mu_Y} + \frac{1}{\mu_Y} (\bar{X} - \mu_X) - \frac{\mu_X}{\mu_Y^2} (\bar{Y} - \mu_Y)
$$

### 6. 计算均值百分比差异的渐近分布

假设 \(g(\bar{X}, \bar{Y}) = \frac{\bar{X} - \bar{Y}}{\mu_Y}\)，由上式近似得到：

$$
g(\bar{X}, \bar{Y}) \approx \frac{\mu_X - \mu_Y}{\mu_Y} + \frac{1}{\mu_Y} (\bar{X} - \mu_X) - \frac{\mu_X}{\mu_Y^2} (\bar{Y} - \mu_Y)
$$

由于 \(\bar{X} \sim N\left(\mu_X, \frac{\sigma_X^2}{n}\right)\) 和 \(\bar{Y} \sim N\left(\mu_Y, \frac{\sigma_Y^2}{m}\right)\)，我们可以计算 \(g(\bar{X}, \bar{Y})\) 的均值和方差：

1. 均值：
   $$E\left[g(\bar{X}, \bar{Y})\right] = \frac{\mu_X - \mu_Y}{\mu_Y}$$

2. 方差：
   $$\text{Var}\left[g(\bar{X}, \bar{Y})\right] = \left(\frac{1}{\mu_Y}\right)^2 \text{Var}(\bar{X}) + \left(-\frac{\mu_X}{\mu_Y^2}\right)^2 \text{Var}(\bar{Y})$$

   即：
   $$\text{Var}\left[g(\bar{X}, \bar{Y})\right] = \frac{\sigma_X^2}{n \mu_Y^2} + \frac{\mu_X^2 \sigma_Y^2}{m \mu_Y^4}$$

### 7. 结论

均值百分比差异的渐近分布为：

$$
g(\bar{X}, \bar{Y}) \approx N\left(\frac{\mu_X - \mu_Y}{\mu_Y}, \frac{\sigma_X^2}{n \mu_Y^2} + \frac{\mu_X^2 \sigma_Y^2}{m \mu_Y^4}\right)
$$

通过以上推导，我们从中心极限定理推导出Delta方法，并得到了两组均值百分比差异的渐近分布。在代入导数时，我们确保计算了正确的一阶偏导数，并将其应用到泰勒展开中，以得到均值百分比差异的近似分布。


中心极限定理（Central Limit Theorem, CLT）和 Delta 方法都是统计学中常用的工具，用于推断统计模型参数的性质。中心极限定理是指在一定条件下，大量独立同分布的随机变量之和的分布近似服从正态分布。Delta 方法则是一种在参数估计中用于计算函数的渐近分布的方法。

让我们从中心极限定理开始。假设我们有两个独立的随机样本，分别来自两个总体，记为 $X_1, X_2, ..., X_n$ 和 $Y_1, Y_2, ..., Y_m$，它们分别服从总体分布 $X \sim F_X$ 和 $Y \sim F_Y$。我们想要比较这两个总体的均值之间的差异。根据中心极限定理，当样本量足够大时，这两个样本均值的差异的分布将近似服从正态分布。

设 $\bar{X}$ 和 $\bar{Y}$ 分别表示这两个样本的均值，$\sigma_X^2$ 和 $\sigma_Y^2$ 分别表示两个总体的方差，$n$ 和 $m$ 分别表示两个样本的大小。根据中心极限定理，我们有：

$$
\bar{X} \approx N(\mu_X, \frac{\sigma_X^2}{n})
$$

$$
\bar{Y} \approx N(\mu_Y, \frac{\sigma_Y^2}{m})
$$

其中，$\mu_X$ 和 $\mu_Y$ 分别是两个总体的均值。因此，两个样本均值之差 $\bar{X} - \bar{Y}$ 的分布近似服从正态分布：

$$
\bar{X} - \bar{Y} \approx N(\mu_X - \mu_Y, \frac{\sigma_X^2}{n} + \frac{\sigma_Y^2}{m})
$$

现在，假设我们想要比较两个总体均值之间的百分比差异，即 $\frac{\mu_X - \mu_Y}{\mu_Y}$。我们可以定义一个函数 $g(\bar{X}, \bar{Y}) = \frac{\bar{X} - \bar{Y}}{\bar{Y}}$ 来表示这个差异的百分比。接下来，我们使用 Delta 方法来估计 $g(\bar{X}, \bar{Y})$ 的渐近分布。

Delta 方法的关键在于利用泰勒展开式，假设函数 $g$ 在参数 $\mu_X$ 和 $\mu_Y$ 的附近是可导的。在我们的例子中，$g$ 是关于 $\mu_X$ 和 $\mu_Y$ 的比值的函数，我们有：

$$
g'(\mu_X, \mu_Y) = \frac{\partial g}{\partial \mu_X} = -\frac{1}{\mu_Y}
$$

$$
g'(\mu_X, \mu_Y) = \frac{\partial g}{\partial \mu_Y} = \frac{\mu_X - \mu_Y}{\mu_Y^2}
$$

现在，我们使用 Delta 方法来估计 $g(\bar{X}, \bar{Y})$ 的渐近分布。根据 Delta 方法，我们有：

$$
\sqrt{n} (\bar{X} - \mu_X) \xrightarrow[]{d} N(0, \sigma_X^2)
$$

$$
\sqrt{m} (\bar{Y} - \mu_Y) \xrightarrow[]{d} N(0, \sigma_Y^2)
$$

因此，我们可以得到 $g(\bar{X}, \bar{Y})$ 的渐近分布：

$$
\sqrt{n} (\bar{X} - \mu_X) \xrightarrow[]{d} N(0, \sigma_X^2)
$$

$$
\sqrt{m} (\bar{Y} - \mu_Y) \xrightarrow[]{d} N(0, \sigma_Y^2)
$$

将导数的值代入，我们有：

$$
\sqrt{n} (\bar{X} - \mu_X) \xrightarrow[]{d} N(0, \sigma_X^2)
$$

$$
\sqrt{m} (\bar{Y} - \mu_Y) \xrightarrow[]{d} N(0, \sigma_Y^2)
$$

所以，根据 Delta 方法，我们可以得到 $g(\bar{X}, \bar{Y})$ 的渐近分布为：

$$
\sqrt{n} (\bar{X} - \mu_X) + \sqrt{m} (\bar{Y} - \mu_Y) \xrightarrow[]{d} N(0, \sigma_X^2 + \frac{\mu_X^2}{\mu_Y^2} \sigma_Y^2)
$$

因此，我们可以利用中心极限定理和 Delta 方法来推断两个组均值百分比差异的渐近分布，从而进行统计推断和假设检验。

中心极限定理表明，对于独立同分布的随机变量 $X_1, X_2, \cdots, X_n$，它们的平均值 $\overline{X_n}$ 的分布随着 $n$ 的增大而趋近于正态分布。具体地，如果 $X_i$ 的期望为 $\mu$，方差为 $\sigma^2$，那么：

$$
\sqrt{n} \frac{\overline{X_n} - \mu}{\sigma} \rightarrow N(0,1) \quad as \ n \rightarrow \infty
$$

其中 $\rightarrow$ 表示收敛于，$N(0,1)$ 表示标准正态分布。

Delta method 则是建立在中心极限定理的基础上来推导，它可以用于估计某个函数关于随机变量的期望或方差的分布。具体来说，如果一个函数 $g(x)$ 满足下列条件：

$g(x)$ 在点 $\theta$ 处可导；
$\sqrt{n}(X_n - \theta) \xrightarrow{d} N(0, \sigma^2)$，其中 $X_n$ 是一个样本量为 $n$ 的随机变量序列；
$g'(\theta) \neq 0$
那么，我们可以得到如下结论：

$$
\sqrt{n}[g(X_n) - g(\theta)] \xrightarrow{d} N(0, \sigma^2[g'(\theta)]^2) \quad as \ n \rightarrow \infty
$$

其中 $\xrightarrow{d}$ 表示依分布收敛，$\sigma^2$ 为 $X_n$ 的方差。

这个结论意味着，我们可以通过中心极限定理来获得 $g(X_n)$ 的渐进分布，然后计算其方差，得到 $g(X_n)$ 的渐进标准误差。

总的来说，delta method 的应用范围比中心极限定理要窄一些，但是它在实际问题中也具有很大的实用价值，可以被广泛应用。

当我们需要对一个随机变量的函数进行统计推断时，中心极限定理和 Delta method 经常被用来进行渐进分析。

下面我们在具体地推导一下 Delta method。

假设随机变量 $X$ 的均值为 $\mu$，方差为 $\sigma^2$，而 $g$ 是一个在 $\mu$ 处可导的函数。设 $X_1, X_2, \cdots, X_n$ 是 $n$ 个来自同一分布的独立随机变量，且 $X_i$ 的均值和方差分别为 $\mu$ 和 $\sigma^2$。

我们希望研究随机变量 $Y_n = g(\overline{X_n})$ 的渐近分布情况，其中 $\overline{X_n} = \frac{1}{n}\sum_{i=1}^{n}X_i$ 表示样本的均值。

首先，我们考虑 $\overline{X_n}$ 的渐近法则，根据中心极限定理，当 $n$ 趋近于 $\infty$，有：

$$
\sqrt{n}(\overline{X_n}-\mu)\rightarrow N(0,\sigma^2)
$$

所以，有：

$$
\sqrt{n}(g(\overline{X_n})-g(\mu))=\frac{g(\overline{X_n})-g(\mu)}{\sqrt{\frac{\sigma^2}{n}}} \sqrt{n}(\overline{X_n}-\mu)\rightarrow N(0,g'(\mu)^2\sigma^2)
$$

其中，$g'(\mu)$ 表示 $g$ 在 $\mu$ 处的导数。这就是 Delta method 的结果。

因此，当 $n$ 趋近于 $\infty$ 时，我们有：

$$
Y_n=g(\overline{X_n})\sim N(g(\mu),\frac{g'(\mu)^2\sigma^2}{n})
$$

这个结论表明，当 $n$ 很大时，$Y_n$ 的渐近分布为正态分布，均值为 $g(\mu)$，方差为 $\frac{g'(\mu)^2\sigma^2}{n}$。这个结果可以用于构造渐近置信区间和假设检验。

需要注意的是，Delta method 同样适用于 $g$ 不止一阶可导的情况，在这种情况下，$g'(\mu)^2$ 应该被替换成 $[g'(\mu)]^2$。