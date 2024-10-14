<!-- # Visualizing Quantities -->
# 数值可视化

|![ Sketchnote by [(@sketchthedocs)](https://sketchthedocs.dev) ](../../sketchnotes/09-Visualizing-Quantities.png)|
|:---:|
| Visualizing Quantities - _Sketchnote by [@nitya](https://twitter.com/nitya)_ |

<!-- In this lesson you will explore how to use one of the many available Python libraries to learn how to create interesting visualizations all around the concept of quantity. Using a cleaned dataset about the birds of Minnesota, you can learn many interesting facts about local wildlife.  -->
本节将探索如何使用众多可用的Python 库来学习如何围绕数值概念创建有趣的可视化。使用关于明尼苏达州鸟类的清理数据集，可以了解有关当地野生动物的许多有趣事实。

<!-- ## [Pre-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/16) -->

<!-- ## Observe wingspan with Matplotlib -->
## 使用 Matplotlib 观察鸟类翼展

<!-- An excellent library to create both simple and sophisticated plots and charts of various kinds is [Matplotlib](https://matplotlib.org/stable/index.html). In general terms, the process of plotting data using these libraries includes identifying the parts of your dataframe that you want to target, performing any transforms on that data necessary, assigning its x and y axis values, deciding what kind of plot to show, and then showing the plot. Matplotlib offers a large variety of visualizations, but for this lesson, let's focus on the ones most appropriate for visualizing quantity: line charts, scatterplots, and bar plots. -->

Matplotlib是一个出色的库，可用于创建各种简单和复杂的图表。一般来说，使用这些库绘制数据的过程包括确定要定位的数据框部分、对数据执行必要的转换、分配其 x 和 y 轴值、决定要显示的图表类型，然后显示图表。Matplotlib 提供了各种各样的可视化效果，但在本课中，我们将重点介绍最适合可视化数量的那些：折线图、散点图和条形图。

<!-- > ✅ Use the best chart to suit your data's structure and the story you want to tell. 
> - To analyze trends over time: line
> - To compare values: bar, column, pie, scatterplot
> - To show how parts relate to a whole: pie
> - To show distribution of data: scatterplot, bar
> - To show trends: line, column
> - To show relationships between values: line, scatterplot, bubble -->

> -分析随时间变化的趋势：线
> -比较值：条形图、柱状图、饼图、散点图
> -显示部分与整体的关系：饼图
> -显示数据分布：散点图、条形图
> -显示趋势：线、柱
> -显示值之间的关系：线、散点图、气泡图

<!-- If you have a dataset and need to discover how much of a given item is included, one of the first tasks you have at hand will be to inspect its values.  -->

如果有一个数据集并且需要发现其中包含多少给定项目，那么要做的首要任务之一就是检查其值。

<!-- ✅ There are very good 'cheat sheets' available for Matplotlib [here](https://matplotlib.org/cheatsheets/cheatsheets.pdf). -->

<!-- ## Build a line plot about bird wingspan values -->

## 建立鸟类翼展值的线图

<!-- Open the `notebook.ipynb` file at the root of this lesson folder and add a cell. -->
打开`notebook.ipynb`本课程文件夹根目录下的文件并添加一个单元格。

<!-- > Note: the data is stored in the root of this repo in the `/data` folder. -->
> 注意：数据存储在该 repo 的`/data`文件夹中。

```python
import pandas as pd
import matplotlib.pyplot as plt
birds = pd.read_csv('../../data/birds.csv')
birds.head()
```
<!-- This data is a mix of text and numbers: -->
这些数据是文本和数字的混合：


|      | Name                         | ScientificName         | Category              | Order        | Family   | Genus       | ConservationStatus | MinLength | MaxLength | MinBodyMass | MaxBodyMass | MinWingspan | MaxWingspan |
| ---: | :--------------------------- | :--------------------- | :-------------------- | :----------- | :------- | :---------- | :----------------- | --------: | --------: | ----------: | ----------: | ----------: | ----------: |
|    0 | Black-bellied whistling-duck | Dendrocygna autumnalis | Ducks/Geese/Waterfowl | Anseriformes | Anatidae | Dendrocygna | LC                 |        47 |        56 |         652 |        1020 |          76 |          94 |
|    1 | Fulvous whistling-duck       | Dendrocygna bicolor    | Ducks/Geese/Waterfowl | Anseriformes | Anatidae | Dendrocygna | LC                 |        45 |        53 |         712 |        1050 |          85 |          93 |
|    2 | Snow goose                   | Anser caerulescens     | Ducks/Geese/Waterfowl | Anseriformes | Anatidae | Anser       | LC                 |        64 |        79 |        2050 |        4050 |         135 |         165 |
|    3 | Ross's goose                 | Anser rossii           | Ducks/Geese/Waterfowl | Anseriformes | Anatidae | Anser       | LC                 |      57.3 |        64 |        1066 |        1567 |         113 |         116 |
|    4 | Greater white-fronted goose  | Anser albifrons        | Ducks/Geese/Waterfowl | Anseriformes | Anatidae | Anser       | LC                 |        64 |        81 |        1930 |        3310 |         130 |         165 |

<!-- Let's start by plotting some of the numeric data using a basic line plot. Suppose you wanted a view of the maximum wingspan for these interesting birds. -->
首先，用基本的线图绘制一些数值数据。假设你想了解这些有趣的鸟类的最大翼展。

```python
wingspan = birds['MaxWingspan'] 
wingspan.plot()
```
![Max Wingspan](images/max-wingspan-02.png)

<!-- What do you notice immediately? There seems to be at least one outlier - that's quite a wingspan! A 2300 centimeter wingspan equals 23 meters - are there Pterodactyls roaming Minnesota? Let's investigate.

While you could  do a quick sort in Excel to find those outliers, which are probably typos, continue the visualization process by working from within the plot.

Add labels to the x-axis to show what kind of birds are in question: -->
你立即注意到了什么？似乎至少有一个异常值 - 翼展相当长！2300 厘米的翼展相当于 23 米 - 明尼苏达州有翼手龙Pterodactyls吗？让我们调查一下。

虽然您可以在 Excel 中快速排序以查找那些可能是拼写错误的异常值，但可以通过在图内进行操作来继续可视化过程。

在 x 轴上添加标签来显示所讨论的鸟类种类：


```
plt.title('Max Wingspan in Centimeters')
plt.ylabel('Wingspan (CM)')
plt.xlabel('Birds')
plt.xticks(rotation=45)
x = birds['Name'] 
y = birds['MaxWingspan']

plt.plot(x, y)

plt.show()
```
![wingspan with labels](images/max-wingspan-labels-02.png)

<!-- Even with the rotation of the labels set to 45 degrees, there are too many to read. Let's try a different strategy: label only those outliers and set the labels within the chart. You can use a scatter chart to make more room for the labeling: -->
即使将标签旋转设置为 45 度，标签数量也太多了，无法阅读。让我们尝试不同的策略：只标记那些异常值，并在图表内设置标签。可以使用散点图来为标签腾出更多空间：

```python
plt.title('Max Wingspan in Centimeters')
plt.ylabel('Wingspan (CM)')
plt.tick_params(axis='both',which='both',labelbottom=False,bottom=False)

for i in range(len(birds)):
    x = birds['Name'][i]
    y = birds['MaxWingspan'][i]
    plt.plot(x, y, 'bo')
    if birds['MaxWingspan'][i] > 500:
        plt.text(x, y * (1 - 0.05), birds['Name'][i], fontsize=12)
    
plt.show()
```
What's going on here? You used `tick_params` to hide the bottom labels and then created a loop over your birds dataset. Plotting the chart with small round blue dots by using `bo`, you checked for any bird with a maximum wingspan over 500 and displayed their label next to the dot if so. You offset the labels a little on the y axis (`y * (1 - 0.05)`) and used the bird name as a label.

这是怎么回事？过去常常tick_params隐藏底部标签，然后在鸟类数据集上创建一个循环。使用`bo`绘制带有小圆蓝点的图表，检查了最大翼展超过 500 的任何鸟类，并在点旁边显示它们的标签（如果是）在 y 轴上稍微偏移标签（`y * (1 - 0.05)`），并使用鸟类名称作为标签。

<!-- What did you discover? -->
你发现了什么？

![outliers](images/labeled-wingspan-02.png)
<!-- ## Filter your data -->
## 过滤数据

<!-- Both the Bald Eagle and the Prairie Falcon, while probably very large birds, appear to be mislabeled, with an extra `0` added to their maximum wingspan. It's unlikely that you'll meet a Bald Eagle with a 25 meter wingspan, but if so, please let us know! Let's create a new dataframe without those two outliers: -->

白头鹰和草原猎鹰虽然可能都是非常大的鸟类，但似乎被错误地标记，它们的最大翼展被多加了一个0。通常不可能遇到翼展为25米的白头鹰！让我们创建一个没有这两个异常值的新数据框：

```python
plt.title('Max Wingspan in Centimeters')
plt.ylabel('Wingspan (CM)')
plt.xlabel('Birds')
plt.tick_params(axis='both',which='both',labelbottom=False,bottom=False)
for i in range(len(birds)):
    x = birds['Name'][i]
    y = birds['MaxWingspan'][i]
    if birds['Name'][i] not in ['Bald eagle', 'Prairie falcon']:
        plt.plot(x, y, 'bo')
plt.show()
```

<!-- By filtering out outliers, your data is now more cohesive and understandable. -->
通过过滤异常值，数据现在更加具有凝聚力和易于理解。



![scatterplot of wingspans](images/scatterplot-wingspan-02.png)

<!-- Now that we have a cleaner dataset at least in terms of wingspan, let's discover more about these birds. -->

现在我们至少在翼展方面有了更清晰的数据集，让我们来进一步了解这些鸟类。

<!-- While line and scatter plots can display information about data values and their distributions, we want to think about the values inherent in this dataset. You could create visualizations to answer the following questions about quantity: -->
虽然线图和散点图可以显示有关数据值及其分布的信息，但我们希望考虑此数据集中固有的值。可以创建可视化来回答有关数量的以下问题：


> How many categories of birds are there, and what are their numbers?
> How many birds are extinct, endangered, rare, or common?
> How many are there of the various genus and orders in Linnaeus's terminology?

> 鸟类有多少种，数量有多少？
> 有多少种鸟类已经灭绝、濒临灭绝、稀有或常见？
> 林奈术语Linnaeus's terminology中各种属和目有多少种？

<!-- ## Explore bar charts -->
## 探索柱状图

<!-- Bar charts are practical when you need to show groupings of data. Let's explore the categories of birds that exist in this dataset to see which is the most common by number.

In the notebook file, create a basic bar chart

✅ Note, you can either filter out the two outlier birds we identified in the previous section, edit the typo in their wingspan, or leave them in for these exercises which do not depend on wingspan values.

If you want to create a bar chart, you can select the data you want to focus on. Bar charts can be created from raw data: -->
当需要显示数据分组时，柱状图非常实用。让我们探索此数据集中存在的鸟类类别，看看哪种鸟类数量最多。

在笔记本文件中，创建一个基本柱状图

✅ 注意，可以过滤掉我们在上一节中确定的两只异常鸟类，编辑它们翼展中的拼写错误，或者将它们保留在这些不依赖翼展值的练习中。

如果要创建柱状图，可以选择要关注的数据。柱状图可以从原始数据创建：


```python
birds.plot(x='Category',
        kind='bar',
        stacked=True,
        title='Birds of Minnesota')

```
![full data as a bar chart](images/full-data-bar-02.png)

<!-- This bar chart, however, is unreadable because there is too much non-grouped data. You need to select only the data that you want to plot, so let's look at the length of birds based on their category. 

Filter your data to include only the bird's category. 

✅ Notice that you use Pandas to manage the data, and then let Matplotlib do the charting.

Since there are many categories, you can display this chart vertically and tweak its height to account for all the data: -->

但是，这个柱状图难以阅读，因为非分组数据太多。只需选择要绘制的数据，因此让我们根据鸟类的类别查看它们的长度。

过滤您的数据以仅包含鸟类的类别。

✅ 注意，你使用 Pandas 来管理数据，然后让 Matplotlib 来绘制图表。

由于类别很多，可以垂直显示此图表并调整其高度以显示所有数据：


```python
category_count = birds.value_counts(birds['Category'].values, sort=True)
plt.rcParams['figure.figsize'] = [6, 12]
category_count.plot.barh()
```
![category and length](images/category-counts-02.png)

<!-- This bar chart shows a good view of the number of birds in each category. In a blink of an eye, you see that the largest number of birds in this region are in the Ducks/Geese/Waterfowl category. Minnesota is the 'land of 10,000 lakes' so this isn't surprising!

✅ Try some other counts on this dataset. Does anything surprise you? -->

此条形图清楚地显示了每个类别的鸟类数量。一目了然就就可以发现该地区鸟类数量最多的是鸭子/鹅/水禽类别。明尼苏达州是“万湖之国”，所以这并不奇怪！

✅ 尝试在这个数据集上进行一些其他计数。有什么让你感到惊讶的吗？


<!-- ## Comparing data -->
## 对比数据

<!-- You can try different comparisons of grouped data by creating new axes. Try a comparison of the MaxLength of a bird, based on its category: -->
可以通过创建新轴来尝试对分组数据进行不同的比较。尝试根据鸟类的类别比较其最大长度：

```python
maxlength = birds['MaxLength']
plt.barh(y=birds['Category'], width=maxlength)
plt.rcParams['figure.figsize'] = [6, 12]
plt.show()
```
![comparing data](images/category-length-02.png)

<!-- Nothing is surprising here: hummingbirds have the least MaxLength compared to Pelicans or Geese. It's good when data makes logical sense!

You can create more interesting visualizations of bar charts by superimposing data. Let's superimpose Minimum and Maximum Length on a given bird category: -->

这里没有什么令人惊讶的：与鹈鹕或鹅相比，蜂鸟的最大长度最小。当数据合乎逻辑时，这很好！

可以通过叠加数据来创建更有趣的柱状图可视化效果。让我们在给定的鸟类类别上叠加最小长度和最大长度：

```python
minLength = birds['MinLength']
maxLength = birds['MaxLength']
category = birds['Category']

plt.barh(category, maxLength)
plt.barh(category, minLength)

plt.show()
```
<!-- In this plot, you can see the range per bird category of the Minimum Length and Maximum length. You can safely say that, given this data, the bigger the bird, the larger its length range. Fascinating! -->

在此图中，可以看到每个鸟类类别的最小长度和最大长度范围。现在可以肯定地说，根据这些数据，鸟越大，其长度范围就越大。太有趣了！

![superimposed values](images/superimposed-02.png)

<!-- ## 🚀 Challenge

This bird dataset offers a wealth of information about different types of birds within a particular ecosystem. Search around the internet and see if you can find other bird-oriented datasets. Practice building charts and graphs around these birds to discover facts you didn't realize.
## [Post-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/17) -->

## Review & Self Study

<!-- This first lesson has given you some information about how to use Matplotlib to visualize quantities. Do some research around other ways to work with datasets for visualization. [Plotly](https://github.com/plotly/plotly.py) is one that we won't cover in these lessons, so take a look at what it can offer. -->
本节课提供了有关如何使用 Matplotlib 可视化数量的一些信息。研究一下使用数据集进行可视化的其他方法。[Plotly](https://github.com/plotly/plotly.py)是我们不会在这些课程中介绍的，因此请查看它能提供哪些功能。

## Assignment

[Lines, Scatters, and Bars](assignment.md)
