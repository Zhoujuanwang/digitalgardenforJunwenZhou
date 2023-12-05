---
{"dg-publish":true,"permalink":"/Epidemiology_and_Health_Statistics/Principles of Biostatistics/","dgPassFrontmatter":true}
---


## 8. Sampling Distribution of the Mean
### 一些概念
statistical inference：统计推断
用样本的信息来推断总体的信息的过程
maximum likelihood estimator：最大似然估计
一种统计方法，用于根据已知的观测数据来估计未知参数的值，该方法基于最大化观测数据出现的概率，假设观测数据是独立同分布的？
standard error：标准误差（标准误）标准误差：随机变量的概率函数或概率密度函数的标准差，特别是指从具有正态分布的总体中抽取的样本的平均值的标准误差，它等于正态分布的标准差除以样本大小的平方根。

## 19. Multiple Regression
### The Model
建立多元回归模型基于以下几点假设：
1. 我们假定对于$x_1,x_2,……x_q$的测量都是精准的，y值分布服从均值为$\mu_{y|x_1,x_2,……,x_q}$标准差为$\sigma_{y|x_1,x_2,……,x_q}$的正态分布
2. y的取值的独立的
3. 方差齐性假说：即对于任意的$x_1,x_2,……x_q$取值，$\sigma_{y|x_1,x_2,……,x_q}$是不变的
4. $\mu_{y|x_1,x_2,……,x_q}$与$x_1,x_2,……x_q$之间满足等式：
$$\mu_{y|x_1,x_2,……,x_q}=\alpha+\beta_1x_1+\beta_2x_2+\cdots+\beta_qx_q$$

多元回归模型的评价
和简单线性回归模型一样，我们可以使用决定系数$R^2$以及残差图来评价模型的拟合效果。
需要注意的是，我们比较多元回归模型和简单线性回归模型的$R^2$时需要谨慎，因为只要我们往简单线性模型里面增加一个变量成为多元回归模型，那么，新模型的$R^2$一定是比旧模型大的

#### 指示变量
二分类变量也可以以分布为0和1的取值加入到多元回归模型中，此时，它们被称为指示变量

#### 交互项
什么是交互项：一个解释变量对y值的预测效果随着另一个解释变量值的变化而变化


