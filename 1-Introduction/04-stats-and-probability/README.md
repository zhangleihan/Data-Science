# A Brief Introduction to Statistics and Probability

|![ Sketchnote by [(@sketchthedocs)](https://sketchthedocs.dev) ](../../sketchnotes/04-Statistics-Probability.png)|
|:---:|
| Statistics and Probability - _Sketchnote by [@nitya](https://twitter.com/nitya)_ |

统计和概率论是与数据科学高度相关的两个高度相关的数学领域。即使没有深厚的数学知识也可以对数据进行操作，但至少了解一些基本概念仍然更好。在这里，我们将提供一个简短的介绍，以帮助您入门。
<!-- Statistics and Probability Theory are two highly related areas of Mathematics that are highly relevant to Data Science. It is possible to operate with data without deep knowledge of mathematics, but it is still better to know at least some basic concepts. Here we will present a short introduction that will help you get started. -->

[![Intro Video](images/video-prob-and-stats.png)](https://youtu.be/Z5Zy85g4Yjw)


## [Pre-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/6)

## Probability and Random Variables

概率是 0 到 1 之间的数字，表示事件发生的可能性有多大。它被定义为积极结果（导致事件）的数量除以结果总数，前提是所有结果的可能性相同。例如，当我们掷骰子时，得到偶数的概率是 3/6 = 0.5。

当我们谈论事件时，我们使用随机变量。例如，表示掷骰子时获得的数字的随机变量的值为 1 到 6。从 1 到 6 的数字集合称为样本空间。我们可以讨论随机变量取某个值的概率，例如 P(X=3)=1/6。

前面示例中的随机变量称为离散变量，因为它具有可数样本空间，即存在可以枚举的单独值。在某些情况下，样本空间是一个实数范围或整个实数集。此类变量称为连续变量。一个很好的例子是公共汽车到达的时间。


<!-- **Probability** is a number between 0 and 1 that expresses how probable an **event** is. It is defined as a number of positive outcomes (that lead to the event), divided by total number of outcomes, given that all outcomes are equally probable. For example, when we roll a dice, the probability that we get an even number is 3/6 = 0.5.

When we talk about events, we use **random variables**. For example, the random variable that represents a number obtained when rolling a dice would take values from 1 to 6. Set of numbers from 1 to 6 is called **sample space**. We can talk about the probability of a random variable taking a certain value, for example P(X=3)=1/6.

The random variable in previous example is called **discrete**, because it has a countable sample space, i.e. there are separate values that can be enumerated. There are cases when sample space is a range of real numbers, or the whole set of real numbers. Such variables are called **continuous**. A good example is the time when the bus arrives. -->

## Probability Distribution

在离散随机变量的情况下，很容易用函数 P(X) 来描述每个事件的概率。对于样本空间S中的每个值s，它将给出一个从 0 到 1 的数字，这样所有事件的 P(X=s) 的所有值的总和将为 1。

最著名的离散分布是均匀分布，其中有一个包含 N 个元素的样本空间，每个元素的概率均为 1/N。

使用从某个区间 [a,b] 或整个实数集 ℝ 提取的值来描述连续变量的概率分布更加困难。考虑公交车到达时间的情况。事实上，对于每个确切的到达时间t，公交车恰好在该时间到达的概率为 0！

<!-- In the case of discrete random variables, it is easy to describe the probability of each event by a function P(X). For each value *s* from sample space *S* it will give a number from 0 to 1, such that the sum of all values of P(X=s) for all events would be 1.

The most well-known discrete distribution is **uniform distribution**, in which there is a sample space of N elements, with equal probability of 1/N for each of them. 

It is more difficult to describe the probability distribution of a continuous variable, with values drawn from some interval [a,b], or the whole set of real numbers &Ropf;. Consider the case of bus arrival time. In fact, for each exact arrival time *t*, the probability of a bus arriving at exactly that time is 0!-->

<!-- > Now you know that events with 0 probability happen, and very often! At least each time when the bus arrives! -->

> 现在您知道，概率为 0 的事件会发生，而且经常发生！至少每次公共汽车到达时！

<!-- We can only talk about the probability of a variable falling in a given interval of values, eg. P(t<sub>1</sub>&le;X&lt;t<sub>2</sub>). In this case, probability distribution is described by a **probability density function** p(x), such that  -->

我们只能讨论变量落入给定值区间的概率，例如，P(t<sub>1</sub>&le;X&lt;t<sub>2</sub>)。在这种情况下，概率分布由概率密度函数**p(x)描述，使得

![P(t_1\le X<t_2)=\int_{t_1}^{t_2}p(x)dx](./images/probability-density.png)
  
<!-- A continuous analog of uniform distribution is called **continuous uniform**, which is defined on a finite interval. A probability that the value X falls into an interval of length l is proportional to l, and rises up to 1.

Another important distribution is **normal distribution**, which we will talk about in more detail below. -->

均匀分布的连续模拟称为连续均匀，它是在有限区间上定义的。值 X 落入长度为 l 的区间的概率与 l 成正比，并且最高可达 1。

另一个重要的分布是正态分布，我们将在下面更详细地讨论它。

## Mean, Variance and Standard Deviation

<!-- Suppose we draw a sequence of n samples of a random variable X: x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>. We can define **mean** (or **arithmetic average**) value of the sequence in the traditional way as (x<sub>1</sub>+x<sub>2</sub>+x<sub>n</sub>)/n. As we grow the size of the sample (i.e. take the limit with n&rarr;&infin;), we will obtain the mean (also called **expectation**) of the distribution. We will denote expectation by **E**(x). -->

假设我们绘制随机变量 X 的 n 个样本序列： X: x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>。我们可以用传统的方式将序列的平均值（或算术平均值）定义为(x<sub>1</sub>+x<sub>2</sub>+x<sub>n</sub>)/n。随着样本规模的增大（即取 n&rarr;&infin 的极限），我们将获得分布的平均值（也称为期望）。我们用**E**(x)表示期望。

<!-- > It can be demonstrated that for any discrete distribution with values {x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>N</sub>} and corresponding probabilities p<sub>1</sub>, p<sub>2</sub>, ..., p<sub>N</sub>, the expectation would equal to E(X)=x<sub>1</sub>p<sub>1</sub>+x<sub>2</sub>p<sub>2</sub>+...+x<sub>N</sub>p<sub>N</sub>. -->

> 可以证明，对于具有值 {x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>N</sub>} 和相应概率 p<sub>1</sub>, p<sub>2</sub>, ..., p<sub>N</sub>的任何离散分布，期望将等于 E(X)=x<sub>1</sub>p<sub>1</sub>+x<sub>2</sub>p<sub>2</sub>+...+x<sub>N</sub>p<sub>N</sub>。

<!-- To identify how far the values are spread, we can compute the variance &sigma;<sup>2</sup> = &sum;(x<sub>i</sub> - &mu;)<sup>2</sup>/n, where &mu; is the mean of the sequence. The value &sigma; is called **standard deviation**, and &sigma;<sup>2</sup> is called a **variance**. -->

为了确定值的分布范围，我们可以计算方差 &sigma;<sup>2</sup> = &sum;(x<sub>i</sub> - &mu;)<sup>2</sup>/n，其中&mu;是序列的平均值。值 &sigma; 称为标准差，&sigma;<sup>2</sup>称为方差。

## Mode, Median and Quartiles

<!-- Sometimes, mean does not adequately represent the "typical" value for data. For example, when there are a few extreme values that are completely out of range, they can affect the mean. Another good indication is a **median**, a value such that half of data points are lower than it, and another half - higher.

To help us understand the distribution of data, it is helpful to talk about **quartiles**: -->

有时，平均值并不能充分代表数据的“典型”值。例如，当存在一些完全超出范围的极值时，它们可能会影响平均值。另一个很好的指示是中位数，该值使得一半数据点低于它，另一半数据点高于它。

为了帮助我们理解数据的分布，讨论四分位数会很有帮助：

<!-- * First quartile, or Q1, is a value, such that 25% of the data fall below it
* Third quartile, or Q3, is a value that 75% of the data fall below it

Graphically we can represent relationship between median and quartiles in a diagram called the **box plot**: -->

* 第一个四分位数或 Q1 是一个值，25% 的数据低于该值
* 第三四分位数或 Q3 是 75% 的数据低于该值的值
我们可以用图形方式表示中位数和四分位数之间的关系，称为箱线图：

<img src="images/boxplot_explanation.png" width="50%"/>

<!-- Here we also compute **inter-quartile range** IQR=Q3-Q1, and so-called **outliers** - values, that lie outside the boundaries [Q1-1.5*IQR,Q3+1.5*IQR]. -->

在这里，我们还计算四分位数范围IQR=Q3-Q1，以及所谓的异常值，即位于边界 [Q1-1.5*IQR,Q3+1.5*IQR] 之外的值。



<!-- For finite distribution that contains a small number of possible values, a good "typical" value is the one that appears the most frequently, which is called **mode**. It is often applied to categorical data, such as colors. Consider a situation when we have two groups of people - some that strongly prefer red, and others who prefer blue. If we code colors by numbers, the mean value for a favorite color would be somewhere in the orange-green spectrum, which does not indicate the actual preference on neither group. However, the mode would be either one of the colors, or both colors, if the number of people voting for them is equal (in this case we call the sample **multimodal**). -->

对于包含少量可能值的有限分布，一个好的“典型”值是出现最频繁的值，称为众数。它通常应用于分类数据，例如颜色。考虑这样一种情况：我们有两组人 - 一些人非常喜欢红色，另一些人则喜欢蓝色。如果我们用数字对颜色进行编码，那么最喜欢的颜色的平均值将位于橙绿色光谱中的某个位置，这并不表明对这两个组的实际偏好。但是，如果投票给它们的人数相等，则模式可以是其中一种颜色，也可以是两种颜色（在这种情况下，我们将样本称为 multimodal ）。

## Real-world Data

<!-- When we analyze data from real life, they often are not random variables as such, in a sense that we do not perform experiments with unknown result. For example, consider a team of baseball players, and their body data, such as height, weight and age. Those numbers are not exactly random, but we can still apply the same mathematical concepts. For example, a sequence of people's weights can be considered to be a sequence of values drawn from some random variable. Below is the sequence of weights of actual baseball players from [Major League Baseball](http://mlb.mlb.com/index.jsp), taken from [this dataset](http://wiki.stat.ucla.edu/socr/index.php/SOCR_Data_MLB_HeightsWeights) (for your convenience, only first 20 values are shown): -->

当我们分析现实生活中的数据时，它们通常不是随机变量，从某种意义上说，我们不会进行结果未知的实验。例如，考虑一支棒球运动员团队及其身体数据，例如身高、体重和年龄。这些数字并不完全随机，但我们仍然可以应用相同的数学概念。例如，人的体重序列可以被认为是从某个随机变量中提取的值序列。以下是[美国职业棒球大联盟](http://mlb.mlb.com/index.jsp)中实际棒球运动员的体重序列，取自此[数据集](http://wiki.stat.ucla.edu/socr/index.php/SOCR_Data_MLB_HeightsWeights)（为方便起见，仅显示前 20 个值）：

```
[180.0, 215.0, 210.0, 210.0, 188.0, 176.0, 209.0, 200.0, 231.0, 180.0, 188.0, 180.0, 185.0, 160.0, 180.0, 185.0, 197.0, 189.0, 185.0, 219.0]
```

<!-- > **Note**: To see the example of working with this dataset, have a look at the [accompanying notebook](notebook.ipynb). There are also a number of challenges throughout this lesson, and you may complete them by adding some code to that notebook. If you are not sure how to operate on data, do not worry - we will come back to working with data using Python at a later time. If you do not know how to run code in Jupyter Notebook, have a look at [this article](https://soshnikov.com/education/how-to-execute-notebooks-from-github/). -->

> 注意：要查看使用此数据集的示例，请查看随附的笔记本。本课程中还存在许多挑战，您可以通过向该笔记本添加一些代码来完成这些挑战。如果您不确定如何操作数据，请不要担心 - 我们稍后会使用 Python 来处理数据。如果您不知道如何在 Jupyter Notebook 中运行代码，请查看这篇[文章](https://soshnikov.com/education/how-to-execute-notebooks-from-github/)。

<!-- Here is the box plot showing mean, median and quartiles for our data: -->
这是显示数据的平均值、中位数和四分位数的箱线图：

![Weight Box Plot](images/weight-boxplot.png)

<!-- Since our data contains information about different player **roles**, we can also do the box plot by role - it will allow us to get the idea on how parameters values differ across roles. This time we will consider height: -->
由于我们的数据包含有关不同玩家角色的信息，因此我们还可以按角色绘制箱线图 - 这将使我们了解不同角色的参数值有何不同。这次我们将考虑高度：

![Box plot by role](images/boxplot_byrole.png)

<!-- This diagram suggests that, on average, height of first basemen is higher that height of second basemen. Later in this lesson we will learn how we can test this hypothesis more formally, and how to demonstrate that our data is statistically significant to show that. -->
该图表明，平均而言，一垒手的身高高于二垒手的身高。在本课后面，我们将学习如何更正式地检验这个假设，以及如何证明我们的数据具有统计显着性。

<!-- > When working with real-world data, we assume that all data points are samples drawn from some probability distribution. This assumption allows us to apply machine learning techniques and build working predictive models. -->
>在处理现实世界数据时，我们假设所有数据点都是从某种概率分布中抽取的样本。这一假设使我们能够应用机器学习技术并构建有效的预测模型。

<!-- To see what the distribution of our data is, we can plot a graph called a **histogram**. X-axis would contain a number of different weight intervals (so-called **bins**), and the vertical axis would show the number of times our random variable sample was inside a given interval. -->
要查看数据的分布情况，我们可以绘制一个称为直方图的图表。X 轴将包含许多不同的权重区间（所谓的bin），垂直轴将显示随机变量样本位于给定区间内的次数。 

![Histogram of real world data](images/weight-histogram.png)

<!-- From this histogram you can see that all values are centered around certain mean weight, and the further we go from that weight - the fewer weights of that value are encountered. I.e., it is very improbable that the weight of a baseball player would be very different from the mean weight. Variance of weights show the extent to which weights are likely to differ from the mean. -->
从这个直方图中，您可以看到所有值都以某个平均权重为中心，并且距离该权重越远，遇到的该值的权重就越少。即，棒球运动员的体重与平均体重相差很大的可能性是非常小的。权重方差显示权重可能与平均值不同的程度。

<!-- > If we take weights of other people, not from the baseball league, the distribution is likely to be different. However, the shape of the distribution will be the same, but mean and variance would change. So, if we train our model on baseball players, it is likely to give wrong results when applied to students of a university, because the underlying distribution is different. -->
>如果我们采用其他人的权重，而不是棒球联盟的权重，那么分布可能会有所不同。然而，分布的形状将是相同的，但均值和方差会改变。因此，如果我们在棒球运动员上训练我们的模型，当应用于大学学生时，很可能会给出错误的结果，因为潜在的分布是不同的。

## Normal Distribution

<!-- The distribution of weights that we have seen above is very typical, and many measurements from real world follow the same type of distribution, but with different mean and variance. This distribution is called **normal distribution**, and it plays a very important role in statistics. -->
我们在上面看到的权重分布非常典型，现实世界中的许多测量都遵循相同类型的分布，但具有不同的均值和方差。这种分布称为正态分布，它在统计学中起着非常重要的作用。

<!-- Using normal distribution is a correct way to generate random weights of potential baseball players. Once we know mean weight `mean` and standard deviation `std`, we can generate 1000 weight samples in the following way: -->
使用正态分布是生成潜在棒球运动员随机权重的正确方法。一旦我们知道了平均重量mean和标准差std，我们就可以通过以下方式生成 1000 个重量样本：

```python
samples = np.random.normal(mean,std,1000)
``` 

<!-- If we plot the histogram of the generated samples we will see the picture very similar to the one shown above. And if we increase the number of samples and the number of bins, we can generate a picture of a normal distribution that is more close to ideal: -->
如果我们绘制生成样本的直方图，我们将看到与上图非常相似的图片。如果我们增加样本数量和箱数，我们可以生成更接近理想的正态分布图：

![Normal Distribution with mean=0 and std.dev=1](images/normal-histogram.png)

*Normal Distribution with mean=0 and std.dev=1*

## Confidence Intervals

<!-- When we talk about weights of baseball players, we assume that there is certain **random variable W** that corresponds to ideal probability distribution of weights of all baseball players (so-called **population**). Our sequence of weights corresponds to a subset of all baseball players that we call **sample**. An interesting question is, can we know the parameters of distribution of W, i.e. mean and variance of the population? -->
当我们谈论棒球运动员的体重时，我们假设存在某个随机变量 W对应于所有棒球运动员（所谓的总体）体重的理想概率分布。我们的权重序列对应于我们称为样本的所有棒球运动员的子集。一个有趣的问题是，我们能否知道W的分布参数，即总体的均值和方差？

<!-- The easiest answer would be to calculate mean and variance of our sample. However, it could happen that our random sample does not accurately represent complete population. Thus it makes sense to talk about **confidence interval**. -->
最简单的答案是计算样本的均值和方差。然而，我们的随机样本可能无法准确代表完整的总体。因此谈论置信区间是有意义的。

<!-- > **Confidence interval** is the estimation of true mean of the population given our sample, which is accurate is a certain probability (or **level of confidence**). -->
>置信区间是对给定样本的总体真实平均值的估计，其准确度是一定的概率（或置信水平）。


<!-- Suppose we have a sample X<sub>1</sub>, ..., X<sub>n</sub> from our distribution. Each time we draw a sample from our distribution, we would end up with different mean value &mu;. Thus &mu; can be considered to be a random variable. A **confidence interval** with confidence p is a pair of values (L<sub>p</sub>,R<sub>p</sub>), such that **P**(L<sub>p</sub>&leq;&mu;&leq;R<sub>p</sub>) = p, i.e. a probability of measured mean value falling within the interval equals to p. -->
假设我们有一个来自分布的样本 X 1 , ..., X n 。每次我们从分布中抽取样本时，都会得到不同的平均值 μ。因此μ可以被认为是一个随机变量。置信区间为置信度p，是一对值(L<sub>p</sub>,R<sub>p</sub>)，使得**P**(L<sub>p</sub>&leq;&mu;&leq;R<sub>p</sub>) = p，即测量平均值落在该区间内的概率等于p。


<!-- It does beyond our short intro to discuss in detail how those confidence intervals are calculated. Some more details can be found [on Wikipedia](https://en.wikipedia.org/wiki/Confidence_interval). In short, we define the distribution of computed sample mean relative to the true mean of the population, which is called **student distribution**. -->
它超出了我们简短的介绍，详细讨论了如何计算这些置信区间。更多详细信息可以在[维基百科](https://en.wikipedia.org/wiki/Confidence_interval)上找到。简而言之，我们定义计算样本均值相对于总体真实均值的分布，称为学生分布。


<!-- > **Interesting fact**: Student distribution is named after mathematician William Sealy Gosset, who published his paper under the pseudonym "Student". He worked in the Guinness brewery, and, according to one of the versions, his employer did not want general public to know that they were using statistical tests to determine the quality of raw materials. -->
> 有趣的事实：学生分布以数学家威廉·西利·戈塞特 (William Sealy Gosset) 的名字命名，他以笔名“学生”发表了论文。他在吉尼斯啤酒厂工作，根据其中一个版本，他的雇主不希望公众知道他们正在使用统计测试来确定原材料的质量。

<!-- If we want to estimate the mean &mu; of our population with confidence p, we need to take *(1-p)/2-th percentile* of a Student distribution A, which can either be taken from tables, or computer using some built-in functions of statistical software (eg. Python, R, etc.). Then the interval for &mu; would be given by X&pm;A*D/&radic;n, where X is the obtained mean of the sample, D is the standard deviation. -->
如果我们想要以置信度 p 估计总体的平均值 μ，我们需要采用学生分布 A 的*(1-p)/2-th个百分位数，这可以从表格中获取，也可以使用某些内置的计算机获取统计软件的功能（例如Python、R等）。那么 μ 的区间将由 X&pm;A*D/&radic;n 给出，其中 X 是获得的样本平均值，D 是标准差。

<!-- > **Note**: We also omit the discussion of an important concept of [degrees of freedom](https://en.wikipedia.org/wiki/Degrees_of_freedom_(statistics)), which is important in relation to Student distribution. You can refer to more complete books on statistics to understand this concept deeper. -->
注意：我们还省略了对[自由度](https://en.wikipedia.org/wiki/Degrees_of_freedom_(statistics))这一重要概念的讨论，该概念对于学生分布很重要。你可以参考更完整的统计学书籍来更深入地理解这个概念。


<!-- An example of calculating confidence interval for weights and heights is given in the [accompanying notebooks](notebook.ipynb). -->
随附的[notebook](notebook.ipynb)中给出了计算体重和身高置信区间的示例。

| p | Weight mean |
|-----|-----------|
| 0.85 | 201.73±0.94 |
| 0.90 | 201.73±1.08 |
| 0.95 | 201.73±1.28 |

<!-- Notice that the higher is the confidence probability, the wider is the confidence interval.  -->
请注意，置信概率越高，置信区间越宽。

## Hypothesis Testing 

<!-- In our baseball players dataset, there are different player roles, that can be summarized below (look at the [accompanying notebook](notebook.ipynb) to see how this table can be calculated): -->
在我们的棒球运动员数据集中，有不同的球员角色，可以总结如下（查看随附的[notebook](notebook.ipynb)以了解如何计算此表）：

角色	高度	重量	

<!-- | Role | Height | Weight | Count |
|------|--------|--------|-------|
| Catcher | 72.723684 | 204.328947 | 76 |
| Designated_Hitter | 74.222222 | 220.888889 | 18 |
| First_Baseman | 74.000000 | 213.109091 | 55 |
| Outfielder | 73.010309 | 199.113402 | 194 |
| Relief_Pitcher | 74.374603 | 203.517460 | 315 |
| Second_Baseman | 71.362069 | 184.344828 | 58 |
| Shortstop | 71.903846 | 182.923077 | 52 |
| Starting_Pitcher | 74.719457 | 205.163636 | 221 |
| Third_Baseman | 73.044444 | 200.955556 | 45 | -->

| 角色 | 身高 | 体重 | 人数 |
|------|--------|--------|-------|
| Catcher | 72.723684 | 204.328947 | 76 |
| Designated_Hitter | 74.222222 | 220.888889 | 18 |
| First_Baseman | 74.000000 | 213.109091 | 55 |
| Outfielder | 73.010309 | 199.113402 | 194 |
| Relief_Pitcher | 74.374603 | 203.517460 | 315 |
| Second_Baseman | 71.362069 | 184.344828 | 58 |
| Shortstop | 71.903846 | 182.923077 | 52 |
| Starting_Pitcher | 74.719457 | 205.163636 | 221 |
| Third_Baseman | 73.044444 | 200.955556 | 45 |


<!-- We can notice that the mean heights of first basemen is higher than that of second basemen. Thus, we may be tempted to conclude that **first basemen are higher than second basemen**. -->
我们可以注意到，一垒手的平均身高高于二垒手。因此，我们可能会得出这样的结论：一垒手高于二垒手。

<!-- > This statement is called **a hypothesis**, because we do not know whether the fact is actually true or not. -->
> 这种陈述被称为假设，因为我们不知道事实是否真实。

<!-- However, it is not always obvious whether we can make this conclusion. From the discussion above we know that each mean has an associated confidence interval, and thus this difference can just be a statistical error. We need some more formal way to test our hypothesis. -->
然而，我们是否能得出这个结论并不总是显而易见的。从上面的讨论中我们知道每个均值都有一个相关的置信区间，因此这种差异可能只是统计误差。我们需要一些更正式的方法来检验我们的假设。

<!-- Let's compute confidence intervals separately for heights of first and second basemen: -->
让我们分别计算一垒手和二垒手身高的置信区间：

| Confidence | First Basemen | Second Basemen |
|------------|---------------|----------------|
| 0.85 | 73.62..74.38 | 71.04..71.69 |
| 0.90 | 73.56..74.44 | 70.99..71.73 |
| 0.95 | 73.47..74.53 | 70.92..71.81 |

<!-- We can see that under no confidence the intervals overlap. That proves our hypothesis that first basemen are higher than second basemen. -->
我们可以看到，在没有置信度的情况下，区间重叠。这证明了我们的假设，即一垒手高于二垒手。

More formally, the problem we are solving is to see if **two probability distributions are the same**, or at least have the same parameters. Depending on the distribution, we need to use different tests for that. If we know that our distributions are normal, we can apply **[Student t-test](https://en.wikipedia.org/wiki/Student%27s_t-test)**. 
更正式地说，我们要解决的问题是查看两个概率分布是否相同，或者至少具有相同的参数。根据发行版的不同，我们需要使用不同的测试。如果我们知道我们的分布是正态的，我们可以应用[学生t检验](https://en.wikipedia.org/wiki/Student%27s_t-test)。

<!-- In Student t-test, we compute so-called **t-value**, which indicates the difference between means, taking into account the variance. It is demonstrated that t-value follows **student distribution**, which allows us to get the threshold value for a given confidence level **p** (this can be computed, or looked up in the numerical tables). We then compare t-value to this threshold to approve or reject the hypothesis. -->
在学生 t 检验中，我们计算所谓的t 值，它表示均值之间的差异，同时考虑方差。事实证明，t 值遵循学生分布，这使我们能够获得给定置信水平p的阈值（这可以计算，或在数值表中查找）。然后，我们将 t 值与该阈值进行比较以批准或拒绝假设。

<!-- In Python, we can use the **SciPy** package, which includes `ttest_ind` function (in addition to many other useful statistical functions!). It computes the t-value for us, and also does the reverse lookup of confidence p-value, so that we can just look at the confidence to draw the conclusion. -->
在Python中，我们可以使用SciPy包，其中包含ttest_ind函数（此外还有许多其他有用的统计函数！）。它为我们计算 t 值，并反向查找置信度 p 值，以便我们只需查看置信度即可得出结论。

<!-- For example, our comparison between heights of first and second basemen give us the following results:  -->
例如，我们比较一垒手和二垒手的身高，得出以下结果：

```python
from scipy.stats import ttest_ind

tval, pval = ttest_ind(df.loc[df['Role']=='First_Baseman',['Height']], df.loc[df['Role']=='Designated_Hitter',['Height']],equal_var=False)
print(f"T-value = {tval[0]:.2f}\nP-value: {pval[0]}")
```
```
T-value = 7.65
P-value: 9.137321189738925e-12
```
<!-- In our case, p-value is very low, meaning that there is strong evidence supporting that first basemen are taller. -->
在我们的例子中，p 值非常低，这意味着有强有力的证据支持一垒手更高。


<!-- There are also different other types of hypothesis that we might want to test, for example: -->
我们可能还想测试其他不同类型的假设，例如：

<!-- * To prove that a given sample follows some distribution. In our case we have assumed that heights are normally distributed, but that needs formal statistical verification.  -->
* 证明给定样本遵循某种分布。在我们的例子中，我们假设身高呈正态分布，但这需要正式的统计验证。

<!-- * To prove that a mean value of a sample corresponds to some predefined value -->
* 证明样本的平均值对应于某个预定义值


<!-- * To compare means of a number of samples (eg. what is the difference in happiness levels among different age groups) -->
* 比较多个样本的平均值（例如，不同年龄组的幸福水平有何差异）

## Law of Large Numbers and Central Limit Theorem

<!-- One of the reasons why normal distribution is so important is so-called **central limit theorem**. Suppose we have a large sample of independent N values X<sub>1</sub>, ..., X<sub>N</sub>, sampled from any distribution with mean &mu; and variance &sigma;<sup>2</sup>. Then, for sufficiently large N (in other words, when N&rarr;&infin;), the mean &Sigma;<sub>i</sub>X<sub>i</sub> would be normally distributed, with mean &mu; and variance &sigma;<sup>2</sup>/N. -->
正态分布如此重要的原因之一是所谓的中心极限定理。假设我们有一个独立的 N 个值X<sub>1</sub>, ..., X<sub>N</sub>的大样本，从具有均值 μ 和方差 &sigma;<sup>2</sup>的任何分布中采样。那么，对于足够大的 N（换句话说，当 N&rarr;&infin;时），均值 &Sigma;<sub>i</sub>X<sub>i</sub>将呈正态分布，均值 μ 和方差 &sigma;<sup>2</sup>/N。


<!-- > Another way to interpret the central limit theorem is to say that regardless of distribution, when you compute the mean of a sum of any random variable values you end up with normal distribution.  -->
> 解释中心极限定理的另一种方法是，无论分布如何，当您计算任何随机变量值之和的平均值时，您最终都会得到正态分布。


<!-- From the central limit theorem it also follows that, when N&rarr;&infin;, the probability of the sample mean to be equal to &mu; becomes 1. This is known as **the law of large numbers**. -->
由中心极限定理还可以得出，当N&rarr;&infin;时，样本均值等于μ的概率变为1。这就是大数定律。

## Covariance and Correlation

<!-- One of the things Data Science does is finding relations between data. We say that two sequences **correlate** when they exhibit the similar behavior at the same time, i.e. they either rise/fall simultaneously, or one sequence rises when another one falls and vice versa. In other words, there seems to be some relation between two sequences. -->
数据科学所做的事情之一就是寻找数据之间的关系。当两个序列同时表现出相似的行为时，我们说它们相关，即它们同时上升/下降，或者一个序列在另一个序列下降时上升，反之亦然。换句话说，两个序列之间似乎存在某种关系。



<!-- > Correlation does not necessarily indicate causal relationship between two sequences; sometimes both variables can depend on some external cause, or it can be purely by chance the two sequences correlate. However, strong mathematical correlation is a good indication that two variables are somehow connected. -->
> 相关性并不一定表明两个序列之间存在因果关系；有时两个变量都可能取决于某些外部原因，或者两个序列可能纯粹是偶然相关的。然而，很强的数学相关性很好地表明两个变量之间存在某种联系。


 <!-- Mathematically, the main concept that shows the relation between two random variables is **covariance**, that is computed like this: Cov(X,Y) = **E**\[(X-**E**(X))(Y-**E**(Y))\]. We compute the deviation of both variables from their mean values, and then product of those deviations. If both variables deviate together, the product would always be a positive value, that would add up to positive covariance. If both variables deviate out-of-sync (i.e. one falls below average when another one rises above average), we will always get negative numbers, that will add up to negative covariance. If the deviations are not dependent, they will add up to roughly zero. -->
 从数学上讲，显示两个随机变量之间关系的主要概念是协方差，其计算方式如下： Cov(X,Y) = **E**\[(X-**E**(X))(Y-**E**(Y))\]。我们计算两个变量与其平均值的偏差，然后计算这些偏差的乘积。如果两个变量一起偏离，则乘积将始终为正值，这将导致正协方差。如果两个变量偏离不同步（即一个变量低于平均值，而另一个变量高于平均值），我们将始终得到负数，这将导致负协方差。如果偏差不相关，它们加起来将大致为零。

<!-- The absolute value of covariance does not tell us much on how large the correlation is, because it depends on the magnitude of actual values. To normalize it, we can divide covariance by standard deviation of both variables, to get **correlation**. The good thing is that correlation is always in the range of [-1,1], where 1 indicates strong positive correlation between values, -1 - strong negative correlation, and 0 - no correlation at all (variables are independent).  -->
协方差的绝对值并不能告诉我们相关性有多大，因为它取决于实际值的大小。为了对其进行标准化，我们可以将协方差除以两个变量的标准差，以获得相关性。好处是相关性始终在 [-1,1] 范围内，其中 1 表示值之间存在强正相关性，-1 - 强负相关性，0 - 根本没有相关性（变量是独立的）。

<!-- **Example**: We can compute correlation between weights and heights of baseball players from the dataset mentioned above: -->
示例：我们可以从上述数据集中计算棒球运动员体重和身高之间的相关性：

```python
print(np.corrcoef(weights,heights))
```
<!-- As a result, we get **correlation matrix** like this one: -->
结果，我们得到如下的相关矩阵：

```
array([[1.        , 0.52959196],
       [0.52959196, 1.        ]])
```

<!-- > Correlation matrix C can be computed for any number of input sequences S<sub>1</sub>, ..., S<sub>n</sub>. The value of C<sub>ij</sub> is the correlation between S<sub>i</sub> and S<sub>j</sub>, and diagonal elements are always 1 (which is also self-correlation of S<sub>i</sub>). -->
> 可以针对任意数量的输入序列S<sub>1</sub>, ..., S<sub>n</sub>计算相关矩阵 C<sub>ij</sub>的值是S<sub>i</sub>和S<sub>j</sub>之间的相关性，对角线元素始终为1（这也是S<sub>i</sub>的自相关）。

<!-- In our case, the value 0.53 indicates that there is some correlation between weight and height of a person. We can also make the scatter plot of one value against the other to see the relationship visually: -->
在我们的例子中，值 0.53 表明一个人的体重和身高之间存在某种相关性。我们还可以制作一个值相对于另一个值的散点图，以直观地看到其中的关系：


![Relationship between weight and height](images/weight-height-relationship.png)

<!-- > More examples of correlation and covariance can be found in [accompanying notebook](notebook.ipynb). -->
更多相关性和协方差的例子可以在随附的[notebook](notebook.ipynb)中找到。


## Conclusion

<!-- In this section, we have learnt: -->
在本节中，我们学习了：

* 数据的基本统计属性，例如均值、方差、众数和四分位数
* 随机变量的不同分布，包括正态分布
* 如何找到不同属性之间的相关性
* 如何使用健全的数学和统计学工具来证明一些假设，
* 如何计算给定数据样本的随机变量的置信区间


<!-- * basic statistical properties of data, such as mean, variance, mode and quartiles
* different distributions of random variables, including normal distribution
* how to find correlation between different properties
* how to use sound apparatus of math and statistics in order to prove some hypotheses, 
* how to compute confidence intervals for random variable given data sample -->

<!-- While this is definitely not exhaustive list of topics that exist within probability and statistics, it should be enough to give you a good start into this course. -->
虽然这绝对不是概率和统计中存在的主题的详尽列表，但它应该足以为您提供本课程的良好开端。

## 🚀 Challenge

<!-- Use the sample code in the notebook to test other hypothesis that: 
1. First basemen are older than second basemen
2. First basemen are taller than third basemen
3. Shortstops are taller than second basemen -->

使用笔记本中的示例代码来测试其他假设：

1. 一垒手比二垒手年龄大
2. 一垒手比三垒手高
3. 游击手比二垒手高

## [Post-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/7)

## Review & Self Study

<!-- Probability and statistics is such a broad topic that it deserves its own course. If you are interested to go deeper into theory, you may want to continue reading some of the following books: -->
概率和统计是一个如此广泛的话题，以至于它值得有自己的课程。如果您有兴趣更深入地了解理论，您可能需要继续阅读以下一些书籍：

1. [Carlos Fernandez-Granda](https://cims.nyu.edu/~cfgranda/) from New York University has great lecture notes [Probability and Statistics for Data Science](https://cims.nyu.edu/~cfgranda/pages/stuff/probability_stats_for_DS.pdf) (available online)
1. [Peter and Andrew Bruce. Practical Statistics for Data Scientists.](https://www.oreilly.com/library/view/practical-statistics-for/9781491952955/) [[sample code in R](https://github.com/andrewgbruce/statistics-for-data-scientists)]. 
1. [James D. Miller. Statistics for Data Science](https://www.packtpub.com/product/statistics-for-data-science/9781788290678) [[sample code in R](https://github.com/PacktPublishing/Statistics-for-Data-Science)]

## Assignment

<!-- [Small Diabetes Study](assignment.md) -->
[小型糖尿病研究](assignment.md)

## Credits

This lesson has been authored with ♥️ by [Dmitry Soshnikov](http://soshnikov.com)
