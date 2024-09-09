<!-- # Defining Data Science -->
# 数据挖掘（数据科学）概述

| ![ Sketchnote by [(@sketchthedocs)](https://sketchthedocs.dev) ](../../sketchnotes/01-Definitions.png) |
| :----------------------------------------------------------------------------------------------------: |
|              Defining Data Science - _Sketchnote by [@nitya](https://twitter.com/nitya)_               |

---

<!-- [![Defining Data Science Video](images/video-def-ds.png)](https://youtu.be/beZ7Mb_oz9I)

## [Pre-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/0) -->

## 什么是数据？
<!-- In our everyday life, we are constantly surrounded by data. The text you are reading now is data.  The list of phone numbers of your friends in your smartphone is data, as well as the current time displayed on your watch. As human beings, we naturally operate with data by counting the money we have or by writing letters to our friends. -->
在我们的日常生活中，我们无时无刻不在被数据包围。你现在正在阅读的文字就是数据。你智能手机中的朋友电话号码列表也是数据，手表上显示的当前时间也是数据。作为人类，我们很自然地会通过计算自己拥有的金钱或给朋友写信来处理数据。

<!-- However, data became much more critical with the creation of computers.  The primary role of computers is to perform computations, but they need data to operate on.  Thus, we need to understand how computers store and process data. -->
然而，随着计算机的出现，数据变得更加重要。计算机的主要作用是执行计算，但它们需要数据来操作。因此，我们需要了解计算机如何存储和处理数据。

<!-- With the emergence of the Internet, the role of computers as data handling devices increased.  If you think about it, we now use computers more and more for data processing and communication, rather than actual computations. When we write an e-mail to a friend or search for some information on the Internet - we are essentially creating, storing, transmitting, and manipulating data. -->

随着互联网的出现，计算机作为数据处理设备的作用日益增强。如果你仔细想想，我们现在越来越多地使用计算机进行数据处理和通信，而不是实际计算。当我们给朋友写电子邮件或在互联网上搜索某些信息时，我们本质上是在创建、存储、传输和操作数据。

<!-- > Can you remember the last time you have used computers to actually compute something?  -->

## 什么是数据科学？

<!-- In [Wikipedia](https://en.wikipedia.org/wiki/Data_science), **Data Science** is defined as *a scientific field that uses scientific methods to extract knowledge and insights from structured and unstructured data, and apply knowledge and actionable insights from data across a broad range of application domains*.  -->

在维基百科中，数据科学被定义为一门科学领域，它使用科学方法从结构化和非结构化数据中提取知识和见解，并将来自数据的知识和可操作的见解应用于广泛的应用领域。

<!-- This definition highlights the following important aspects of data science: -->
这个定义强调了数据科学的以下重要方面：

<!-- * The main goal of data science is to **extract knowledge** from data, in other words - to **understand** data, find some hidden relationships and build a **model**.
* Data science uses **scientific methods**, such as probability and statistics.  In fact, when the term *data science* was first introduced, some people argued that data science was just a new fancy name for statistics.  Nowadays it has become evident that the field is much broader.    
* Obtained knowledge should be applied to produce some **actionable insights**, i.e. practical insights that you can apply to real business situations.
* We should be able to operate on both **structured** and **unstructured** data.  We will come back to discuss different types of data later in the course.
* **Application domain** is an important concept, and data scientists often need at least some degree of expertise in the problem domain, for example: finance, medicine, marketing, etc. -->

* 数据科学的主要目标是从数据中提取知识，换句话说 -理解数据，找到一些隐藏的关系并建立模型。
* 数据科学使用科学方法，例如概率和统计。事实上，当数据科学这个术语首次出现时，有些人认为数据科学只是统计学的一个新奇名称。如今，很明显这个领域要广泛得多。
* 应该运用获得的知识来产生一些可行的见解，即可应用于实际业务情况的实用见解。
* 我们应该能够操作结构化和非结构化数据。我们将在课程的后面讨论不同类型的数据。
* 应用领域是一个重要的概念，数据科学家往往需要在问题领域至少具备一定程度的专业知识，例如：金融、医学、营销等。

<!-- > Another important aspect of Data Science is that it studies how data can be gathered, stored and operated upon using computers.  While statistics gives us mathematical foundations, data science applies mathematical concepts to actually draw insights from data. -->

> 数据科学的另一个重要方面是研究如何使用计算机收集、存储和操作数据。虽然统计学为我们提供了数学基础，但数据科学应用数学概念来从数据中得出真正的见解。

<!-- One of the ways (attributed to [Jim Gray](https://en.wikipedia.org/wiki/Jim_Gray_(computer_scientist))) to look at the data science is to consider it to be a separate paradigm of science: -->
看待数据科学的方法之一是将其视为一个独立的科学范式：
<!-- * **Empirical**, in which we rely mostly on observations and results of experiments
* **Theoretical**, where new concepts emerge from existing scientific knowledge
* **Computational**, where we discover new principles based on some computational experiments
* **Data-Driven**, based on discovering relationships and patterns in the data   -->

* 经验主义，我们主要依靠观察和实验结果
* 理论，新概念从现有科学知识中产生
* 计算，我们根据一些计算实验发现新的原理
* 数据驱动，基于发现数据中的关系和模式

<!-- ## Other Related Fields -->
## 其他相关领域

<!-- Since data is pervasive, data science itself is also a broad field, touching many other disciplines. -->
由于数据无处不在，数据科学本身也是一个广阔的领域，涉及许多其他学科。

<dl>
<dt>Databases</dt>
<dd>
<!-- A critical consideration is **how to store** the data, i.e. how to structure it in a way that allows faster processing.  There are different types of databases that store structured and unstructured data, which <a href="../../2-Working-With-Data/README.md">we will consider in our course</a>. -->
一个关键的考虑因素是**如何存储**数据，即如何以允许更快处理的方式构造数据。有不同类型的数据库用于存储结构化和非结构化数据，我们将在课程中讨论这些内容。
</dd>
<dt>Big Data</dt>
<dd>
<!-- Often we need to store and process very large quantities of data with a relatively simple structure.  There are special approaches and tools to store that data in a distributed manner on a computer cluster, and process it efficiently. -->
我们经常需要存储和处理大量结构相对简单的数据。有特殊的方法和工具可以将这些数据以分布式方式存储在计算机集群上，并进行高效处理。

</dd>
<dt>Machine Learning</dt>
<dd>
<!-- One way to understand data is to **build a model** that will be able to predict a desired outcome.  Developing models from data is called **machine learning**. You may want to have a look at our <a href="https://aka.ms/ml-beginners">Machine Learning for Beginners</a> Curriculum to learn more about it. -->
理解数据的一种方法是**建立一个能够预测期望结果的模型**。从数据中开发模型称为**机器学习**。您可能想查看我们的机器学习初学者课程以了解更多信息。
</dd>
<dt>Artificial Intelligence</dt>
<dd>
<!-- An area of machine learning known as artificial intelligence (AI) also relies on data, and it involves building high complexity models that mimic human thought processes.  AI methods often allow us to turn unstructured data (e.g. natural language) into structured insights.  -->
机器学习的一个领域被称为人工智能 (AI)，它同样依赖于数据，它涉及构建模仿人类思维过程的高复杂度模型。AI 方法通常允许我们将非结构化数据（例如自然语言）转化为结构化见解。
</dd>
<dt>Visualization</dt>
<dd>
<!-- Vast amounts of data are incomprehensible for a human being, but once we create useful visualizations using that data, we can make more sense of the data, and draw some conclusions. Thus, it is important to know many ways to visualize information - something that we will cover in <a href="../../3-Data-Visualization/README.md">Section 3</a> of our course. Related fields also include **Infographics**, and **Human-Computer Interaction** in general.  -->
人类无法理解大量的数据，但一旦我们利用这些数据创建有用的可视化效果，我们就可以更好地理解数据并得出一些结论。因此，了解可视化信息的多种方法非常重要 - 我们将在课程的第 3 部分中介绍这一点。相关领域还包括**信息图表**和一般的**人机交互**。
</dd>
</dl>

<!-- ## Types of Data -->
## 数据类型

<!-- As we have already mentioned, data is everywhere.  We just need to capture it in the right way!  It is useful to distinguish between **structured** and **unstructured** data. The former is typically represented in some well-structured form, often as a table or number of tables, while the latter is just a collection of files.  Sometimes we can also talk about **semi-structured** data, that have some sort of a structure that may vary greatly. -->
正如我们已经提到的，数据无处不在。我们只需要以正确的方式捕获它！区分结构化数据和非结构化数据很有用。前者通常以某种结构良好的形式表示，通常是表格或多个表格，而后者只是文件的集合。有时我们也可以谈论半结构化数据，这种数据具有某种可能差异很大的结构。

| Structured（结构化）                                                                   | Semi-structured（半结构化）                                                                                  | Unstructured（非结构化）                              |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | --------------------------------------- |
| 人名、电话号码                                      | 电商平台商品介绍网页                                                                     | 百科文档        |
| 过去 20 年内建筑物内所有房间每分钟的温度 | JSON 格式的科学论文集合，包含作者、出版日期和摘要 | 学术论文     |
| 进入大楼的所有人员的年龄和性别数据                 | 互联网网页                                                                                  | 监控视频的视频流 |

## 从哪里获取数据

常见的数据来源:

* **结构化**
  - **Internet of Things** (IoT), 物联网(IoT) 包括来自不同传感器（如温度或压力传感器）的数据，可提供大量有用数据。例如，如果办公楼配备了物联网传感器，我们可以自动控制供暖和照明，以最大限度地降低成本。
  - **Surveys** 我们要求用户在购买后或访问网站后完成的调查。
  - **Analysis of behavior** 行为分析可以帮助我们了解用户进入网站的深度，以及离开网站的典型原因。.
  
* **Unstructured**
  - **Texts** 文本可以成为丰富的见解的来源，例如整体情绪分数，或提取关键字和语义含义。
  - **Images** or **Video**. 图像或视频。监控摄像机的视频可用于估计道路交通状况，并告知人们潜在的交通堵塞情况。
  - Web server **Logs** Web 服务器日志可用于了解我们网站哪些页面访问次数最多以及访问时间有多长。
* Semi-structured
  - **Social Network** 社交网络图谱可以成为有关用户个性和传播信息的潜在有效性的重要数据来源。
  - **Group Dynamics** 当我们从聚会中收集到大量照片时，我们可以尝试通过构建人们互相拍照的图表来提取群体动力学数据。

## 使用数据可以做哪些事情？

在数据挖掘或数据科学中，完整的任务包含以下几个方面:

<dl>
<dt>1) 数据采集</dt>
<dd>
第一步是收集数据。虽然在许多情况下，这可能是一个简单的过程，例如数据从 Web 应用程序传输到数据库，但有时我们需要使用特殊技术。例如，来自 IoT 传感器的数据可能非常庞大，因此，在进一步处理之前，最好使用缓冲端点（如 IoT Hub）收集所有数据。
</dd>
<dt>2) 数据存储</dt>
<dd>
存储数据可能具有挑战性，尤其是当我们谈论大数据时。在决定如何存储数据时，预测未来查询数据的方式是有意义的。有几种存储数据的方法：
<ul>
<li>关系数据库存储一组表，并使用一种称为 SQL 的特殊语言来查询它们。通常，表被组织成称为模式的不同组。在许多情况下，我们需要将数据从原始形式转换为适合模式的形式。</li>
<li>NoSQL数据库（例如MongoDB）不会强制执行数据架构，并允许存储更复杂的数据，例如分层 JSON 文档或图形。但是，NoSQL 数据库不具备 SQL 的丰富查询功能，也无法强制执行引用完整性，即有关数据在表中的结构以及如何管理表之间的关系的规则。</li>
<li>数据湖存储用于存储原始、非结构化形式的大量数据。数据湖通常用于大数据，因为所有数据无法放在一台机器上，必须由一组服务器存储和处理。Parquet是通常与大数据结合使用的数据格式。</li> 
</ul>
</dd>
<dt>3) 数据处理</dt>
<dd>
这是数据旅程中最令人兴奋的部分，涉及将数据从其原始形式转换为可用于可视化/模型训练的形式。在处理文本或图像等非结构化数据时，我们可能需要使用一些 AI 技术从数据中提取**特征**，从而将其转换为结构化形式。
</dd>
<dt>4) 可视化/人类洞察</dt>
<dd>
通常，为了理解数据，我们需要将其可视化。我们的工具箱中有许多不同的可视化技术，我们可以找到正确的视图来获得洞察力。通常，数据科学家需要“玩数据”，多次可视化并寻找一些关系。此外，我们可以使用统计技术来测试假设或证明不同数据之间的相关性。  
</dd>
<dt>5) 训练预测模型</dt>
<dd>
由于数据科学的最终目标是能够根据数据做出决策，我们可能希望使用机器学习技术来构建预测模型。然后，我们可以使用该模型使用具有类似结构的新数据集进行预测。
</dd>
</dl>

当然，根据实际数据的不同，可能会缺少某些步骤（例如，当我们在数据库中已经有数据时，或者当我们不需要模型训练时），或者某些步骤可能会重复几次（例如数据处理）。

## 数字化与数字化转型

在过去十年中，许多企业开始认识到数据在制定业务决策时的重要性。要将数据科学原理应用于业务运营，首先需要收集一些数据，即将业务流程转换为数字形式。这被称为数字化。将数据科学技术应用于这些数据以指导决策可以显著提高生产力（甚至是业务转型），这被称为数字化转型。

## 课堂练习

[网页数据采集、解析与分析](./solution/assignment.md)