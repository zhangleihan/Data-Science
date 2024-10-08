<!-- # Working with Data: Python and the Pandas Library -->
# 使用python和pandas处理数据
| ![ Sketchnote by [(@sketchthedocs)](https://sketchthedocs.dev) ](../../sketchnotes/07-WorkWithPython.png) |
| :-------------------------------------------------------------------------------------------------------: |
|                 Working With Python - _Sketchnote by [@nitya](https://twitter.com/nitya)_                 |

[![Intro Video](images/video-ds-python.png)](https://youtu.be/dZjWOGbsN4Y)
<!-- 
While databases offer very efficient ways to store data and query them using query languages, the most flexible way of data processing is writing your own program to manipulate data. In many cases, doing a database query would be a more effective way. However in some cases when more complex data processing is needed, it cannot be done easily using SQL. 

Data processing can be programmed in any programming language, but there are certain languages that are higher level with respect to working with data. Data scientists typically prefer one of the following languages: -->

虽然数据库提供了非常有效的方法来存储数据并使用查询语言查询数据，但最灵活的数据处理方法是编写自己的程序来操作数据。在许多情况下，执行数据库查询是一种更有效的方法。但是，在某些情况下，当需要更复杂的数据处理时，使用 SQL 无法轻松完成。数据处理可以用任何编程语言进行编程，但有些语言在处理数据方面更高级。数据科学家通常更喜欢以下语言之一：

<!-- * **[Python](https://www.python.org/)**, a general-purpose programming language, which is often considered one of the best options for beginners due to its simplicity. Python has a lot of additional libraries that can help you solve many practical problems, such as extracting your data from ZIP archive, or converting picture to grayscale. In addition to data science, Python is also often used for web development. 
* **[R](https://www.r-project.org/)** is a traditional toolbox developed with statistical data processing in mind. It also contains large repository of libraries (CRAN), making it a good choice for data processing. However, R is not a general-purpose programming language, and is rarely used outside of data science domain.
* **[Julia](https://julialang.org/)** is another language developed specifically for data science. It is intended to give better performance than Python, making it a great tool for scientific experimentation. -->

* Python是一种通用编程语言，由于其简单性，通常被认为是初学者的最佳选择之一。Python 有很多附加库，可以帮助您解决许多实际问题，例如从ZIP存档中提取数据，或将图片转换为灰度。除了数据科学，Python也经常用于Web开发。
* R语言是一款专为统计数据处理而开发的传统工具箱。它还包含大量库 (CRAN)，是数据处理的理想选择。然而，R语言不是一种通用编程语言，在数据科学领域之外很少使用。
* Julia是另一种专门为数据科学开发的语言。它旨在提供比 Python 更好的性能，使其成为科学实验的绝佳工具。

<!-- In this lesson, we will focus on using Python for simple data processing. We will assume basic familiarity with the language. If you want a deeper tour of Python, you can refer to one of the following resources:

* [Learn Python in a Fun Way with Turtle Graphics and Fractals](https://github.com/shwars/pycourse) - GitHub-based quick intro course into Python Programming
* [Take your First Steps with Python](https://docs.microsoft.com/en-us/learn/paths/python-first-steps/?WT.mc_id=academic-77958-bethanycheum) Learning Path on [Microsoft Learn](http://learn.microsoft.com/?WT.mc_id=academic-77958-bethanycheum) -->

本章节将重点介绍如何使用 Python 进行简单的数据处理。假设你对Python语言有基本的了解，如果想更深入地掌握Python，可以参考以下资源进行练习：

* 使用 Turtle Graphics 和 Fractals 以有趣的方式学习 Python - 基于 GitHub 的 Python 编程快速入门课程
* 使用Microsoft Learn上的 Python 学习路径迈出第一步

数据有多种形式。在本课中，我们将讨论三种数据形式 -表格数据、文本和图像。

接下来将介绍几个数据处理示例，展示pandas在数据处理方面的若干用法。

<!-- Data can come in many forms. In this lesson, we will consider three forms of data - **tabular data**, **text** and **images**.

We will focus on a few examples of data processing, instead of giving you full overview of all related libraries. This would allow you to get the main idea of what's possible, and leave you with understanding on where to find solutions to your problems when you need them. -->

<!-- > **Most useful advice**. When you need to perform certain operation on data that you do not know how to do, try searching for it in the internet. [Stackoverflow](https://stackoverflow.com/) usually contains a lot of useful code sample in Python for many typical tasks.  -->

- ** 提示 ** 互联网及大模型工具能帮助提供很多有用的处理数据的代码示例，在此基础上进行修改往往能够起到事半功倍的效果。


<!-- ## [Pre-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/12) -->

<!-- ## Tabular Data and Dataframes -->

## 表格数据与Dataframes

<!-- You have already met tabular data when we talked about relational databases. When you have a lot of data, and it is contained in many different linked tables, it definitely makes sense to use SQL for working with it. However, there are many cases when we have a table of data, and we need to gain some **understanding** or **insights** about this data, such as the distribution, correlation between values, etc. In data science, there are a lot of cases when we need to perform some transformations of the original data, followed by visualization. Both those steps can be easily done using Python. -->

当讨论关系数据库时，就涉及到了表格数据。对于大量数据，并且这些数据包含在许多不同的链接表中时，使用 SQL 来处理这些数据绝对是有意义的。然而，在很多情况下，我们需要处理的是单个的数据表，需要对这些数据有一些了解或见解，例如分布、值之间的相关性等。在数据科学中，很多情况下我们需要对原始数据进行一些转换，然后进行可视化。这两个步骤都可以轻松使用Python完成。

<!-- There are two most useful libraries in Python that can help you deal with tabular data:
* **[Pandas](https://pandas.pydata.org/)** allows you to manipulate so-called **Dataframes**, which are analogous to relational tables. You can have named columns, and perform different operations on row, columns and dataframes in general. 
* **[Numpy](https://numpy.org/)** is a library for working with **tensors**, i.e. multi-dimensional **arrays**. Array has values of the same underlying type, and it is simpler than dataframe, but it offers more mathematical operations, and creates less overhead. -->

Python 中有两个最有用的库可以帮助您处理表格数据：

* Pandas允许你操作所谓的Dataframes，它类似于关系表。你可以命名列，并通常对行、列和数据框执行不同的操作。
* Numpy是一个用于处理张量（即多维数组）的库。数组具有相同底层类型的值，它比数据框更简单，但它提供更多的数学运算，并且开销更少。

<!-- There are also a couple of other libraries you should know about:
* **[Matplotlib](https://matplotlib.org/)** is a library used for data visualization and plotting graphs
* **[SciPy](https://www.scipy.org/)** is a library with some additional scientific functions. We have already come across this library when talking about probability and statistics -->
此外，还应该了解其他一些库：

* Matplotlib是一个用于数据可视化和绘制图形的库
* SciPy是一个具有一些附加科学函数的库。我们在讨论概率和统计时已经遇到过这个库。


<!-- Here is a piece of code that you would typically use to import those libraries in the beginning of your Python program: -->

以下是在 Python 程序开始时通常用来导入这些库的一段代码：

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import ... # you need to specify exact sub-packages that you need
``` 

<!-- Pandas is centered around a few basic concepts. -->
Pandas的核心基本概念包括series， dataframe。

### Series 

<!-- **Series** is a sequence of values, similar to a list or numpy array. The main difference is that series also has an **index**, and when we operate on series (eg., add them), the index is taken into account. Index can be as simple as integer row number (it is the index used by default when creating a series from list or array), or it can have a complex structure, such as date interval. -->

**Series**是一系列值，类似于列表或 numpy 数组。主要区别在于系列还具有索引，当我们对系列进行操作（例如，添加它们）时，会考虑索引。索引可以像整数行号一样简单（它是从列表或数组创建系列时默认使用的索引），也可以具有复杂的结构，例如日期间隔。

<!-- > **Note**: There is some introductory Pandas code in the accompanying notebook [`notebook.ipynb`](notebook.ipynb). We only outline some the examples here, and you are definitely welcome to check out the full notebook. -->

> **注意**：随附的笔记本中有一些介绍性的 Pandas 代码[`notebook.ipynb`](notebook.ipynb)。

<!-- Consider an example: we want to analyze sales of our ice-cream spot. Let's generate a series of sales numbers (number of items sold each day) for some time period: -->
考虑一个例子：我们想分析冰淇淋店的销售情况。让我们生成一段时间内的一系列销售数字（每天售出的商品数量）：

```python
start_date = "Jan 1, 2020"
end_date = "Mar 31, 2020"
idx = pd.date_range(start_date,end_date)
print(f"Length of index is {len(idx)}")
items_sold = pd.Series(np.random.randint(25,50,size=len(idx)),index=idx)
items_sold.plot()
```
![Time Series Plot](images/timeseries-1.png)

<!-- Now suppose that each week we are organizing a party for friends, and we take additional 10 packs of ice-cream for a party. We can create another series, indexed by week, to demonstrate that: -->
现在假设我们每周都会为朋友组织一次聚会，并且会为聚会额外带 10 包冰淇淋。我们可以创建另一个按周索引的系列来证明这一点：

```python
additional_items = pd.Series(10,index=pd.date_range(start_date,end_date,freq="W"))
```
<!-- When we add two series together, we get total number: -->
当我们将两个系列加在一起时，我们得到总数：


```python
total_items = items_sold.add(additional_items,fill_value=0)
total_items.plot()
```
![Time Series Plot](images/timeseries-2.png)

<!-- > **Note** that we are not using simple syntax `total_items+additional_items`. If we did, we would have received a lot of `NaN` (*Not a Number*) values in the resulting series. This is because there are missing values for some of the index point in the `additional_items` series, and adding `Nan` to anything results in `NaN`. Thus we need to specify `fill_value` parameter during addition. -->
> 请注意，我们没有使用简单语法total_items+additional_items。如果这样做，我们将在结果系列中收到很多NaN（非数字）值。这是因为系列中的某些索引点缺少值additional_items，并且添加Nan到任何值都会导致NaN。因此我们需要fill_value在添加过程中指定参数。

<!-- With time series, we can also **resample** the series with different time intervals. For example, suppose we want to compute mean sales volume monthly. We can use the following code: -->
对于时间序列，我们还可以用不同的时间间隔对序列进行重新采样。例如，假设我们要计算每月的平均销售量。我们可以使用以下代码：

```python
monthly = total_items.resample("1M").mean()
ax = monthly.plot(kind='bar')
```
![Monthly Time Series Averages](images/timeseries-3.png)

### DataFrame

<!-- A DataFrame is essentially a collection of series with the same index. We can combine several series together into a DataFrame: -->
DataFrame 本质上是具有相同索引的系列的集合。我们可以将多个系列组合成一个 DataFrame：

```python
a = pd.Series(range(1,10))
b = pd.Series(["I","like","to","play","games","and","will","not","change"],index=range(0,9))
df = pd.DataFrame([a,b])
```
<!-- This will create a horizontal table like this: -->
这段代码将创建1个表：

|     | 0   | 1    | 2   | 3   | 4      | 5   | 6      | 7    | 8    |
| --- | --- | ---- | --- | --- | ------ | --- | ------ | ---- | ---- |
| 0   | 1   | 2    | 3   | 4   | 5      | 6   | 7      | 8    | 9    |
| 1   | I   | like | to  | use | Python | and | Pandas | very | much |

<!-- We can also use Series as columns, and specify column names using dictionary: -->
我们还可以使用 Series 作为列，并使用字典指定列名：

```python
df = pd.DataFrame({ 'A' : a, 'B' : b })
```
<!-- This will give us a table like this: -->
这将给产生如下的表格：

|     | A   | B      |
| --- | --- | ------ |
| 0   | 1   | I      |
| 1   | 2   | like   |
| 2   | 3   | to     |
| 3   | 4   | use    |
| 4   | 5   | Python |
| 5   | 6   | and    |
| 6   | 7   | Pandas |
| 7   | 8   | very   |
| 8   | 9   | much   |

<!-- **Note** that we can also get this table layout by transposing the previous table, eg. by writing  -->
**请注意**，也可以通过转置前一个表格来获得此表格布局，例如通过以下代码

```python
df = pd.DataFrame([a,b]).T..rename(columns={ 0 : 'A', 1 : 'B' })
```
<!-- Here `.T` means the operation of transposing the DataFrame, i.e. changing rows and columns, and `rename` operation allows us to rename columns to match the previous example. -->
这里的`.T`意思是转置DataFrame的操作，即改变行和列，并且`rename`操作允许我们重命名列以匹配前面的示例。

<!-- Here are a few most important operations we can perform on DataFrames: -->
以下是我们可以在 DataFrames 上执行的一些最重要的操作：

<!-- **Column selection**. We can select individual columns by writing `df['A']` - this operation returns a Series. We can also select a subset of columns into another DataFrame by writing `df[['B','A']]` - this return another DataFrame. -->

**列选择**。我们可以通过写入来选择单个列`df['A']`- 此操作返回一个 Series。我们还可以通过写入来选择列的子集放入另一个 DataFrame `df[['B','A']]`- 这将返回另一个 DataFrame。

<!-- **Filtering** only certain rows by criteria. For example, to leave only rows with column `A` greater than 5, we can write `df[df['A']>5]`. -->

**Filtering**根据条件过滤某些行。例如，为了仅保留列A大于 5 的行，我们可以这样写`df[df['A']>5]`。

<!-- > **Note**: The way filtering works is the following. The expression `df['A']<5` returns a boolean series, which indicates whether expression is `True` or `False` for each element of the original series `df['A']`. When boolean series is used as an index, it returns subset of rows in the DataFrame. Thus it is not possible to use arbitrary Python boolean expression, for example, writing `df[df['A']>5 and df['A']<7]` would be wrong. Instead, you should use special `&` operation on boolean series, writing `df[(df['A']>5) & (df['A']<7)]` (*brackets are important here*). -->

> 注意：过滤的工作方式如下。表达式`df['A']<5`返回一个布尔series，表示对于原始系列的每个元素，其取值是`True`或`False`。当布尔series用作索引时，它返回 DataFrame 中的行子集。因此，不能使用任意的 Python 布尔表达式，例如，写成`df[df['A']>5 and df['A']<7]`是错误的。相反，应该对布尔series使用特殊操作，写成`df[(df['A']>5) & (df['A']<7)]`（括号在这里很重要）。

<!-- **Creating new computable columns**. We can easily create new computable columns for our DataFrame by using intuitive expression like this: -->
创建新的可计算列。我们可以使用如下表达式轻松地为 DataFrame 创建新的可计算列：

```python
df['DivA'] = df['A']-df['A'].mean() 
``` 
<!-- This example calculates divergence of A from its mean value. What actually happens here is we are computing a series, and then assigning this series to the left-hand-side, creating another column. Thus, we cannot use any operations that are not compatible with series, for example, the code below is wrong: -->
此示例计算特征A与其平均值的散度。通过计算一个series，然后将该系列分配到dataframe的右侧，从而创建另一列。因此，我们不能使用任何与series不兼容的运算，例如，下面的代码是错误的：

```python
# Wrong code -> df['ADescr'] = "Low" if df['A'] < 5 else "Hi"
df['LenB'] = len(df['B']) # <- Wrong result
``` 
<!-- The latter example, while being syntactically correct, gives us wrong result, because it assigns the length of series `B` to all values in the column, and not the length of individual elements as we intended. -->
后一个例子虽然在语法上是正确的，但却给了我们错误的结果，因为它将series的长度分配`B`给列中的所有值，而不是我们想要的单个元素的长度。

<!-- If we need to compute complex expressions like this, we can use `apply` function. The last example can be written as follows: -->
如果需要计算复杂表达式，可以使用apply函数。上一个示例可以写成如下形式：
```python
df['LenB'] = df['B'].apply(lambda x : len(x))
# or 
df['LenB'] = df['B'].apply(len)
```

<!-- After operations above, we will end up with the following DataFrame: -->
经过上述操作，我们将得到以下DataFrame：

|     | A   | B      | DivA | LenB |
| --- | --- | ------ | ---- | ---- |
| 0   | 1   | I      | -4.0 | 1    |
| 1   | 2   | like   | -3.0 | 4    |
| 2   | 3   | to     | -2.0 | 2    |
| 3   | 4   | use    | -1.0 | 3    |
| 4   | 5   | Python | 0.0  | 6    |
| 5   | 6   | and    | 1.0  | 3    |
| 6   | 7   | Pandas | 2.0  | 6    |
| 7   | 8   | very   | 3.0  | 4    |
| 8   | 9   | much   | 4.0  | 4    |

<!-- **Selecting rows based on numbers** can be done using `iloc` construct. For example, to select first 5 rows from the DataFrame: -->
可以使用iloc指定行索引选择行。例如，要从 DataFrame 中选择前 5 行：

```python
df.iloc[:5]
```

<!-- **Grouping** is often used to get a result similar to *pivot tables* in Excel. Suppose that we want to compute mean value of column `A` for each given number of `LenB`. Then we can group our DataFrame by `LenB`, and call `mean`: -->
**Grouping**通常用于获得类似于Excel 中的数据透视表的结果。假设我们要计算A给定数量的列的平均值LenB。然后我们可以根据对 DataFrame 进行分组LenB，然后调用mean：

```python
df.groupby(by='LenB').mean()
```
<!-- If we need to compute mean and the number of elements in the group, then we can use more complex `aggregate` function: -->
如果我们需要计算平均值和组中元素的数量，那么我们可以使用更复杂的aggregate函数：

```python
df.groupby(by='LenB') \
 .aggregate({ 'DivA' : len, 'A' : lambda x: x.mean() }) \
 .rename(columns={ 'DivA' : 'Count', 'A' : 'Mean'})
```
<!-- This gives us the following table: -->
由此我们得到下表：

| LenB | Count | Mean     |
| ---- | ----- | -------- |
| 1    | 1     | 1.000000 |
| 2    | 1     | 3.000000 |
| 3    | 2     | 5.000000 |
| 4    | 3     | 6.333333 |
| 6    | 2     | 6.000000 |

<!-- ### Getting Data -->
### 读写数据

<!-- We have seen how easy it is to construct Series and DataFrames from Python objects. However, data usually comes in the form of a text file, or an Excel table. Luckily, Pandas offers us a simple way to load data from disk. For example, reading CSV file is as simple as this: -->
我们已经看到了从 Python 对象构建 Series 和 DataFrames的简洁与灵活。但是，数据通常以文本文件或 Excel 表的形式出现。相应的，Pandas 为提供了一种从磁盘加载数据的简单方法。例如，读取 CSV 文件非常简单：

```python
df = pd.read_csv('file.csv')
```
<!-- We will see more examples of loading data, including fetching it from external web sites, in the "Challenge" section -->
在“挑战”部分，我们将看到更多加载数据的示例，包括从外部网站获取数据


<!-- ### Printing and Plotting -->
### 打印和绘图
<!-- A Data Scientist often has to explore the data, thus it is important to be able to visualize it. When DataFrame is big, many times we want just to make sure we are doing everything correctly by printing out the first few rows. This can be done by calling `df.head()`. If you are running it from Jupyter Notebook, it will print out the DataFrame in a nice tabular form.

We have also seen the usage of `plot` function to visualize some columns. While `plot` is very useful for many tasks, and supports many different graph types via `kind=` parameter, you can always use raw `matplotlib` library to plot something more complex. We will cover data visualization in detail in separate course lessons.

This overview covers most important concepts of Pandas, however, the library is very rich, and there is no limit to what you can do with it! Let's now apply this knowledge for solving specific problem. -->

数据科学家经常需要探索数据，因此能够将其可视化非常重要。当 DataFrame 很大时，很多时候我们只想通过打印出前几行来确保我们所做的一切都正确无误。这可以通过调用来完成df.head()。如果从 Jupyter Notebook 运行它，它将以漂亮的表格形式打印出 DataFrame。

我们还看到了函数的用法，plot用于可视化一些列。虽然plot它对于许多任务非常有用，并且通过kind=参数支持许多不同的图形类型，但始终可以使用原始matplotlib库来绘制更复杂的图形。我们将在单独的课程中详细介绍数据可视化。

本概述涵盖了 Pandas 的大多数重要概念，但是，该库非常丰富，可以用它做任何事情！现在让我们应用这些知识来解决具体问题。


<!-- ## 🚀 Challenge 1: Analyzing COVID Spread -->
## 挑战1，分析COVID传播数据

<!-- First problem we will focus on is modelling of epidemic spread of COVID-19. In order to do that, we will use the data on the number of infected individuals in different countries, provided by the [Center for Systems Science and Engineering](https://systems.jhu.edu/) (CSSE) at [Johns Hopkins University](https://jhu.edu/). Dataset is available in [this GitHub Repository](https://github.com/CSSEGISandData/COVID-19). -->
我们将重点关注的第一个问题是 COVID-19 疫情传播的建模。为此，我们将使用约翰霍普金斯大学[Johns Hopkins University](https://jhu.edu/)系统科学与工程中心[Center for Systems Science and Engineering](https://systems.jhu.edu/) (CSSE)提供的不同国家感染人数的数据。数据集可在[GitHub Repository](https://github.com/CSSEGISandData/COVID-19)存储库中找到。

由于我们想演示如何处理数据，因此需要在本地编译环境参考[`notebook-covidspread.ipynb`](notebook-covidspread.ipynb)。可以执行单元格代码，并完成预留的一些挑战。


<!-- Since we want to demonstrate how to deal with data, we invite you to open [`notebook-covidspread.ipynb`](notebook-covidspread.ipynb) and read it from top to bottom. You can also execute cells, and do some challenges that we have left for you at the end. -->

![COVID Spread](images/covidspread.png)

<!-- > If you do not know how to run code in Jupyter Notebook, have a look at [this article](https://soshnikov.com/education/how-to-execute-notebooks-from-github/). -->
> 如果不清楚如何在jupyter notebook中运行代码，可以查看[这个教程](https://soshnikov.com/education/how-to-execute-notebooks-from-github/)。

<!-- ## Working with Unstructured Data -->
## 处理非机构化数据

<!-- While data very often comes in tabular form, in some cases we need to deal with less structured data, for example, text or images. In this case, to apply data processing techniques we have seen above, we need to somehow **extract** structured data. Here are a few examples: -->
虽然数据通常以表格形式出现，但在某些情况下，我们需要处理结构化程度较低的数据，例如文本或图像。在这种情况下，要应用上面看到的数据处理技术，我们需要以某种方式提取结构化数据。以下是几个例子：

* 从文本中提取关键字，并查看这些关键词出现的频率
* 使用神经网络提取图片上物体的信息
* 通过摄像机获取人们的情绪信息
<!-- * Extracting keywords from text, and seeing how often those keywords appear
* Using neural networks to extract information about objects on the picture
* Getting information on emotions of people on video camera feed -->

<!-- ## 🚀 Challenge 2: Analyzing COVID Papers -->
## 挑战 2：分析COVID论文
<!-- In this challenge, we will continue with the topic of COVID pandemic, and focus on processing scientific papers on the subject. There is [CORD-19 Dataset](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge) with more than 7000 (at the time of writing) papers on COVID, available with metadata and abstracts (and for about half of them there is also full text provided). -->
将继续讨论 COVID 大流行这一主题，并专注于处理有关该主题的科学论文。[CORD-19 数据集](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge)包含 7000 多篇（截至撰写本文时）有关 COVID 的论文，并提供元数据和摘要（其中约一半还提供全文）。

[这篇博文](https://soshnikov.com/science/analyzing-medical-papers-with-azure-and-text-analytics-for-health/)描述了使用健康认知服务的文本分析来分析该数据集的完整示例。我们将讨论此分析的简化版本。

<!-- A full example of analyzing this dataset using [Text Analytics for Health](https://docs.microsoft.com/azure/cognitive-services/text-analytics/how-tos/text-analytics-for-health/?WT.mc_id=academic-77958-bethanycheum) cognitive service is described [in this blog post](https://soshnikov.com/science/analyzing-medical-papers-with-azure-and-text-analytics-for-health/). We will discuss simplified version of this analysis. -->

<!-- > **NOTE**: We do not provide a copy of the dataset as part of this repository. You may first need to download the [`metadata.csv`](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge?select=metadata.csv) file from [this dataset on Kaggle](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge). Registration with Kaggle may be required. You may also download the dataset without registration [from here](https://ai2-semanticscholar-cord-19.s3-us-west-2.amazonaws.com/historical_releases.html), but it will include all full texts in addition to metadata file. -->

注意：我们不提供数据集的副本作为此存储库的一部分。您可能首先需要[`metadata.csv`](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge?select=metadata.csv)从Kaggle 上的此数据集下载文件。可能需要在 Kaggle 上注册。您也可以从[此处](https://ai2-semanticscholar-cord-19.s3-us-west-2.amazonaws.com/historical_releases.html)下载无需注册的数据集，但除了元数据文件外，它还将包含所有全文。

<!-- Open [`notebook-papers.ipynb`](notebook-papers.ipynb) and read it from top to bottom. You can also execute cells, and do some challenges that we have left for you at the end. -->
打开[`notebook-papers.ipynb`](notebook-papers.ipynb)并从上到下阅读。还可以执行单元格，并完成我们预留的一些挑战。

![Covid Medical Treatment](images/covidtreat.png)

<!-- ## Processing Image Data -->
## 处理图像数据

<!-- Recently, very powerful AI models have been developed that allow us to understand images. There are many tasks that can be solved using pre-trained neural networks, or cloud services. Some examples include: -->
最近，很多非常强大的AI模型被研发出来，使得理解图像变得更加用以。许多任务都可以使用预先训练的神经网络模型、大模型或云服务来解决。以下是一些示例：

<!-- * **Image Classification**, which can help you categorize the image into one of the pre-defined classes. You can easily train your own image classifiers using services such as [Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/?WT.mc_id=academic-77958-bethanycheum)
* **Object Detection** to detect different objects in the image. Services such as [computer vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/?WT.mc_id=academic-77958-bethanycheum) can detect a number of common objects, and you can train [Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/?WT.mc_id=academic-77958-bethanycheum) model to detect some specific objects of interest.
* **Face Detection**, including Age, Gender and Emotion detection. This can be done via [Face API](https://azure.microsoft.com/services/cognitive-services/face/?WT.mc_id=academic-77958-bethanycheum). -->

* **Image Classification**图像分类，可以帮助将图像归类到预定义的类别之一。可以使用[Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/?WT.mc_id=academic-77958-bethanycheum)等服务轻松训练自己的图像分类器
* **Object Detection**对象检测用于检测图像中的不同对象。[computer vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/?WT.mc_id=academic-77958-bethanycheum)等服务可以检测许多常见对象，您可以训练自定义视觉模型[Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/?WT.mc_id=academic-77958-bethanycheum)来检测一些感兴趣的特定对象。
* **Face Detection**人脸检测，包括年龄、性别和情绪检测。这可以通过[Face API](https://azure.microsoft.com/services/cognitive-services/face/?WT.mc_id=academic-77958-bethanycheum)完成。

所有这些云服务都可以使用[Python SDKs](https://docs.microsoft.com/samples/azure-samples/cognitive-services-python-sdk-samples/cognitive-services-python-sdk-samples/?WT.mc_id=academic-77958-bethanycheum)调用，从而可以轻松地纳入您的数据探索工作流程中。

以下是探索来自图像数据源的数据的一些示例：

<!-- All those cloud services can be called using [Python SDKs](https://docs.microsoft.com/samples/azure-samples/cognitive-services-python-sdk-samples/cognitive-services-python-sdk-samples/?WT.mc_id=academic-77958-bethanycheum), and thus can be easily incorporated into your data exploration workflow. 

Here are some examples of exploring data from Image data sources: -->
<!-- * In the blog post [How to Learn Data Science without Coding](https://soshnikov.com/azure/how-to-learn-data-science-without-coding/) we explore Instagram photos, trying to understand what makes people give more likes to a photo. We first extract as much information from pictures as possible using [computer vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/?WT.mc_id=academic-77958-bethanycheum), and then use [Azure Machine Learning AutoML](https://docs.microsoft.com/azure/machine-learning/concept-automated-ml/?WT.mc_id=academic-77958-bethanycheum) to build interpretable model.
* In [Facial Studies Workshop](https://github.com/CloudAdvocacy/FaceStudies) we use [Face API](https://azure.microsoft.com/services/cognitive-services/face/?WT.mc_id=academic-77958-bethanycheum) to extract emotions on people on photographs from events, in order to try to understand what makes people happy.  -->

* 在博客文章《如何在没有编码的情况下学习数据科学》[How to Learn Data Science without Coding](https://soshnikov.com/azure/how-to-learn-data-science-without-coding/)中，我们探索了 Instagram 照片，试图了解是什么让人们对照片给予更多的赞。我们首先使用[computer vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/?WT.mc_id=academic-77958-bethanycheum)从图片中提取尽可能多的信息，然后使用[Azure Machine Learning AutoML](https://docs.microsoft.com/azure/machine-learning/concept-automated-ml/?WT.mc_id=academic-77958-bethanycheum) 构建可解释的模型。
* 在人脸识别研究研讨会[Facial Studies Workshop](https://github.com/CloudAdvocacy/FaceStudies) we use [Face API](https://azure.microsoft.com/services/cognitive-services/face/?WT.mc_id=academic-77958-bethanycheum)上，使用Face API提取事件照片中人物的情绪，以便尝试了解什么能让人们快乐。

<!-- ## Conclusion -->
## 总结

<!-- Whether you already have structured or unstructured data, using Python you can perform all steps related to data processing and understanding. It is probably the most flexible way of data processing, and that is the reason the majority of data scientists use Python as their primary tool. Learning Python in depth is probably a good idea if you are serious about your data science journey! -->

无论你已经拥有结构化或非结构化数据，使用 Python 都可以执行与数据处理和理解相关的所有步骤。它可能是最灵活的数据处理方式，这就是大多数数据科学家使用 Python 作为主要工具的原因。


<!-- ## [Post-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/13) -->

<!-- ## Review & Self Study -->
## 复习与自学

**Books**
* [Wes McKinney. Python for Data Analysis: Data Wrangling with Pandas, NumPy, and IPython](https://www.amazon.com/gp/product/1491957662)

**Online Resources**
* Official [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html) tutorial
* [Documentation on Pandas Visualization](https://pandas.pydata.org/pandas-docs/stable/user_guide/visualization.html)

**Learning Python**
* [Learn Python in a Fun Way with Turtle Graphics and Fractals](https://github.com/shwars/pycourse)
* [Take your First Steps with Python](https://docs.microsoft.com/learn/paths/python-first-steps/?WT.mc_id=academic-77958-bethanycheum) Learning Path on [Microsoft Learn](http://learn.microsoft.com/?WT.mc_id=academic-77958-bethanycheum)

## Assignment
[针对上述挑战进行更详细的数据研究](assignment.md)
<!-- [Perform more detailed data study for the challenges above](assignment.md) -->

<!-- ## Credits -->

<!-- This lesson has been authored with ♥️ by [Dmitry Soshnikov](http://soshnikov.com) -->
