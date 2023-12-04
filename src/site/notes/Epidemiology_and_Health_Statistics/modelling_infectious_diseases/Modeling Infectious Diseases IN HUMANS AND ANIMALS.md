---
{"dg-publish":true,"title":"传染病建模","author":"Junwen Zhou","permalink":"/Epidemiology_and_Health_Statistics/modelling_infectious_diseases/Modeling Infectious Diseases IN HUMANS AND ANIMALS/","dgPassFrontmatter":true}
---


# introduction
## 传染性疾病的四阶段模型
SEIR (susceptible-exposed-infectious-recovered)
![传染病的四阶段模型](C:\Users\zhouj\Documents\Obsidian_Vault\Epidemiology_and_Health_Statistics\modelling_infectious_diseases\images\Pasted_image_20231128112835.png)
在不同情境下，SEIR模型可以简化为：SIR模型（去掉exposed阶段），一些性传播疾病的模型为SIS(susceptible-infectious-susceptible)
把传染病模型从个体层面外推到群体层面，有两个非常重要的参数：
1. the basic reproductive ratio, $R_0$
2. the timescale of infection,
$R_0$
1. 定义：
it defines the average number of secondary cases an average primary case produces in a totally susceptible population
2. 意义
this single parameter allows us to determine whether a disease can successfully invade or not, the threshold level of vaccination required for eradication, and the long-term proportion of susceptible individuals when the infection is endemic.
判断一种传染病能否入侵（流行？）根除这种疾病所需的疫苗接种阈值水平、感染流行时易感个体的长期比例

传染病模型的特点：感染阶段、参数的值（$R_0$等）、（感染的）时间跨度的多变性
控制传染病的方法
1. 疫苗
Vaccination operates by reducing the number of susceptible individuals in the population.
2. 隔离（quarantine）
Quarantining operates by reducing the number of infected individuals freely mixing in the population.（隔离是通过减少人群中被感染个体的活动范围来控制传染病的）
However, quarantining can be applied only once an infectious individual is identified, by which time the individual may have been transmitting infection for many days. In addition, unless the number of cases is small, quarantining can be a prohibitive drain on resources
3. culling（只适用于植物和动物的传染病），杀灭感染者和易感者
4. contact tracing（类似流调？）
Contact tracing operates by refining the targeting of other control measures

建立模型的三元素：accuracy, transparency, and flexibility（准确度、透明度、灵活度）
1. 准确性：
重现观测数据和可靠地预测未来动态的能力。这涉及到定性拟合和定量拟合的问题，定性拟合可能足以深入了解传染病的动态，但如果模型用于对未来的控制政策提出建议，则通常需要良好的定量拟合。
提高准确性：模型的复杂程度提高，纳入更多异质性的和相关的生物信息（Accuracy generally improves with increasing model complexity and the inclusion of more heterogeneities and relevant biological detail.）
2. 透明性
Transparency comes from being able to understand (either analytically or more often numerically) how the various model components influence the dynamics and interact.
透明性是指我们能多大程度上理解模型中各个组分是如何影响动态（我理解的是模型结果）以及是如何相互作用的
3. 灵活性
灵活性看的是一个模型是否能很好地适应一个新的情境

模型能做什么？
两大核心功能：预测和理解，分别对应上面提到的准确性和透明性
一个准确的预测模型能发挥哪些作用？
1. 如果一个模型在某个特定地区预测失败了（之前是准确的），这可能警示我们该地区的某些参数发生了变化
2. 一个准确的预测模型应该能预测一个阈值病例数，当病例数超过阈值时，则警示我们需要采取控制措施了
3. 在消灭（传染病）活动期间，通过预测模型，可以发现响应速度不及模型预测的地区，并针对这些地区采取更强化的控制措施
4. 对报告病例和住院病例进行详细的建模和稳健的统计分析可能能够识别疫情的早期出现。

什么是一个好的模型？
First, a model should be suited to its purpose，在此基础上尽可能地简单
比如，一个帮助我们理解传染病行为的模型，就应该专注于我们感兴趣的特征；一个目标是准确预测的模型，就需要包括宿主和疾病的所有特征，同时需要复杂的过程来确定哪些因素是需要纳入模型的
Second, the model should be parameterizable (where necessary) from available data（模型中的参数是可以通过现存的数据得到的）

# 第二章
## SIR模型
SIR模型是适用于急性传染病，而且是感染后能获得终生免疫的急性传染病。
将宿主分为易感者、感染者、康复者三大类
SIR模型中的两大过程：
I-->R
从临床的角度观察，传染病是有一个平均的“感染期”的，因此，个体从I阶段转变到R阶段的概率，取决于个体I阶段的长度。方便期间，建模时通常将康复率$\gamma$视作一个常数
(From a modeling perspective, this translates into the probability of an individual moving from I to R being dependent on how long they have been in the I class.)
S-->R
从S到R的过程实际上是一个疾病传播的过程，由三个主要的因素决定：
the prevalence of infecteds, （流行率）
the underlying population contact structure,（潜在的接触人群的结构） 
and the probability of transmission given contact.（接触后传播的概率）
相关术语：
感染力$\lambda$
感染力的定义为：易感个体感染的人均比率，也就是说，如果S阶段的人数为$X$，那么会有$\lambda*X$的人会进入到I阶段
感染力与接触率、感染率以及I阶段的人数有关，我们猜想它可能有两种模式：
$\lambda=\beta Y$或者$\lambda=\frac{\beta Y}{N}$
其中，$\beta$是接触率和感染率的积，Y是感染者人数，N是人群总数
The first of these formulations will be referred to as frequency dependent (or mass action) transmission and the second as density dependent (or pseudo mass action) transmission.
频率依赖的传播，建立在这样一个假设上：（一个传染者对易感者的）接触数与人口规模无关：
Frequency-dependent transmission reflects the situation where the number of contacts is independent of the population size. 
而密度依赖的传播，建立在相反的假设上：人口规模（或者说人口密度）越大，接触数也越大
频率依赖(群体作用)传播被认为适用于媒介传播的病原体和具有异质接触结构（我理解的是接触过程因人而异，受很多因素影响的）的病原体（those with heterogeneous contact structure.）；密度依赖(伪群体作用)传播更适用于植物和动物疾病，
The <mark style="background: #BBFABBA6;">transmission term</mark> is generally described by frequency dependence βXY/N (or βSI ), or by density dependence βXY . 
（推导过程）
The differences between frequency- and density-dependent transmission become important if the population size changes or we are trying to parameterize disease models across a range of population sizes.

不考虑人口学特征的SIR模型
此时有：
$$\frac{dS}{dt}=-\beta SI\tag{2.1}$$
$$\frac{dI}{dt}=I(\beta S-\gamma)\tag{2.2}$$
$$\frac{dR}{dt}=\gamma I\tag{2.3}$$
其中，$\gamma$表示康复率，它的倒数$1/\gamma$表示平均感染时间？（which determines the average infectious period）
这个模型非常简单，虽然它不能帮助我们计算S和I 的值，但是，由这个模型可衍生出两个及其重要的推论：
#### 阈值现象
从公式2.2可得，如果$S<\frac{\gamma}{\beta}$那么，$\frac{dI}{dt}<0$，I就会一直减少，感染会逐渐消退
$\frac{\gamma}{\beta}$被称为相对去除率，而它的倒数$\frac{\beta}{\gamma}$称为基本生殖比率(普遍用符号R0表示)，是流行病学中最重要的值之一
#### 感染爆发
式（2.1）与式（2.3）相除，得到
$$\frac{dS}{dR}=-\frac{\beta S}{\gamma}=-R_0S$$
通过对R积分，得到：
$$S=e^{-R_0R}$$
S和R都是关于时间t的函数，有：
$$S(t)=S(0)e^{-R(t)R_0}$$
由于R(t)<1，所以总有：$S>e^{-R_0}$，也就是说，人群中总有一些易感者逃避感染
从而得到一条重要推论：
The chain of transmission eventually breaks due to the decline in infectives, not due to a complete lack of susceptibles.（传播链最终由于感染人数的下降而破裂，而不是由于完全缺乏易感者）
![[数学作业/传染病建模/images/Pasted image 20231202183211.png\|数学作业/传染病建模/images/Pasted image 20231202183211.png]]
