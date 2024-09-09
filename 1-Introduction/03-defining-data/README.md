<!-- # Defining Data -->
# 数据定义

|![ Sketchnote by [(@sketchthedocs)](https://sketchthedocs.dev) ](../../sketchnotes/03-DefiningData.png)|
<!-- |:---:|
|Defining Data - _Sketchnote by [@nitya](https://twitter.com/nitya)_ | -->

<!-- Data is facts, information, observations and measurements that are used to make discoveries and to support informed decisions. A data point is a single unit of data with in a dataset, which is collection of data points. Datasets may come in different formats and structures, and will usually be based on its source, or where the data came from. For example, a company's monthly earnings might be in a spreadsheet but hourly heart rate data from a smartwatch may be in [JSON](https://stackoverflow.com/a/383699) format. It's common for data scientists to work with different types of data within a dataset.  -->
数据是事实、信息、观察和测量，用于发现和支持明智的决策。数据点是数据集中的单个数据单元，数据集是数据点的集合。数据集可能有不同的格式和结构，通常基于其来源或数据来源。例如，公司的月收入可能在电子表格中，但智能手表的每小时心率数据可能采用JSON格式。数据科学家通常会处理数据集中的不同类型的数据。

<!-- This lesson focuses on identifying and classifying data by its characteristics and its sources. -->
本节内容重点介绍根据数据的特征和来源识别和分类数据。

<!-- ## [Pre-Lecture Quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/4) -->
？
## 如何描述数据
<!-- **Raw data** is data that has come from its source in its initial state and has not been analyzed or organized. In order to make sense of what is happening with a dataset, it needs to be organized into a format that can be understood by humans as well as the technology they may use to analyze it further. The structure of a dataset describes how it's organized and can be classified at structured, unstructured and semi-structured. These types of structure will vary, depending on the source but will ultimately fit in these three categories.  -->
**原始数据**是来自其来源的初始状态的数据，尚未经过分析或组织。为了理解数据集的情况，需要将其组织成人类可以理解的格式以及他们可能用来进一步分析的技术。数据集的结构描述了它的组织方式，可以分为结构化、非结构化和半结构化。这些类型的结构会有所不同，具体取决于来源，但最终都属于这三个类别。
<!-- ### Quantitative Data -->
### 定论数据
<!-- Quantitative data is numerical observations within a dataset and can typically be analyzed, measured and used mathematically. Some examples of quantitative data are: a country's population, a person's height or a company's quarterly earnings. With some additional analysis, quantitative data could be used to discover seasonal trends of the Air Quality Index (AQI) or estimate the probability of rush hour traffic on a typical work day. -->
定量数据是数据集中的数值观测值，通常可以通过数学方法进行分析、测量和使用。定量数据的一些示例包括：一个国家的人口、一个人的身高或一家公司的季度收益。通过一些额外的分析，定量数据可用于发现空气质量指数 (AQI) 的季节性趋势或估计典型工作日高峰时段交通的概率。

<!-- ### Qualitative Data -->
### 定性数据
<!-- Qualitative data, also known as categorical data is data that cannot be measured objectively like observations of quantitative data. It's generally various formats of subjective data that captures the quality of something, such as a product or process. Sometimes, qualitative data is numerical and wouldn't be typically used mathematically, like phone numbers or timestamps. Some examples of qualitative data are: video comments, the make and model of a car or your closest friends' favorite color. Qualitative data could be used to understand which products consumers like best or identifying popular keywords in job application resumes. -->
定性数据，也称为分类数据，是无法像定量数据的观察结果那样客观测量的数据。它通常是各种格式的主观数据，用于捕捉某事物（例如产品或流程）的质量。有时，定性数据是数字，通常不会以数学形式使用，例如电话号码或时间戳。定性数据的一些示例包括：视频评论、汽车的品牌和型号或您最亲密的朋友最喜欢的颜色。定性数据可用于了解消费者最喜欢哪些产品或识别求职简历中的热门关键词。

<!-- ### Structured Data -->
### 结构化数据
<!-- Structured data is data that is organized into rows and columns, where each row will have the same set of columns. Columns represent a value of a particular type and will be identified with a name describing what the value represents, while rows contain the actual values. Columns will often have a specific set of rules or restrictions on the values, to ensure that the values accurately represent the column. For example imagine a spreadsheet of customers where each row must have a phone number and the phone numbers never contain alphabetical characters. There may be rules applied on the phone number column to make sure it's never empty and only contains numbers.  -->
结构化数据是按行和列组织的数据，其中每行都具有相同的列集。列表示特定类型的值，并将使用描述该值所代表内容的名称进行标识，而行则包含实际值。列通常会对值有一组特定的规则或限制，以确保值准确地表示列。例如，想象一个客户电子表格，其中每行都必须有一个电话号码，并且电话号码绝不能包含字母字符。电话号码列上可能应用了一些规则，以确保它永远不会为空并且只包含数字。

<!-- A benefit of structured data is that it can be organized in such a way that it can be related to other structured data. However, because the data is designed to be organized in a specific way, making changes to its overall structure can take a lot of effort to do. For example, adding an email column to the customer spreadsheet that cannot be empty means you'll need figure out how you'll add these values to the existing rows of customers in the dataset.  -->
结构化数据的一个优点是，它可以以某种方式组织，以便与其他结构化数据相关联。但是，由于数据被设计为以特定方式组织，因此更改其整体结构可能需要花费大量精力。例如，在客户电子表格中添加不能为空的电子邮件列意味着您需要弄清楚如何将这些值添加到数据集中现有的客户行中。

<!-- Examples of structured data: spreadsheets, relational databases, phone numbers, bank statements -->
结构化数据的示例：电子表格、关系数据库、电话号码、银行对账单

<!-- ### Unstructured Data -->
### 非结构化数据

<!-- Unstructured data typically cannot be categorized into rows or columns and doesn't contain a format or set of rules to follow. Because unstructured data has less restrictions on its structure it's easier to add new information in comparison to a structured dataset. If a sensor capturing data on barometric pressure every 2 minutes has received an update that now allows it to measure and record temperature, it doesn't require altering the existing data if it's unstructured. However, this may make analyzing or investigating this type of data take longer. For example, a scientist who wants to find the average temperature of the previous month from the sensors data, but discovers that the sensor recorded an "e" in some of its recorded data to note that it was broken instead of a typical number, which means the data is incomplete. -->
非结构化数据通常无法归类为行或列，并且不包含要遵循的格式或规则集。由于非结构化数据的结构限制较少，因此与结构化数据集相比，添加新信息更容易。如果每 2 分钟捕获一次气压数据的传感器收到更新，现在可以测量和记录温度，则无需更改现有数据（如果数据是非结构化的）。但是，这可能会使分析或调查此类数据花费更长时间。例如，一位科学家想从传感器数据中找到上个月的平均温度，但发现传感器在其记录的一些数据中记录了一个“e”，表示它坏了，而不是一个典型数字，这意味着数据不完整。

<!-- Examples of unstructured data: text files, text messages, video files -->
非结构化数据的示例：文本文件、短信、视频文件

<!-- ### Semi-structured -->
### 半结构化
<!-- Semi-structured data has features that make it a combination of structured and unstructured data. It doesn't typically conform to a format of rows and columns but is organized in a way that is considered structured and may follow a fixed format or set of rules. The structure will vary between sources, such as a well defined hierarchy to something more flexible that allows for easy integration of new information. Metadata are indicators that help decide how the data is organized and stored and will have various names, based on the type of data. Some common names for metadata are tags, elements, entities and attributes. For example, a typical email message will have a subject, body and a set of recipients and can be organized by whom or when it was sent.  -->
半结构化数据具有使其成为结构化数据和非结构化数据组合的特征。它通常不遵循行和列的格式，而是以被认为是结构化的方式组织，并且可能遵循固定格式或规则集。结构会因来源而异，例如明确定义的层次结构，或者更灵活，可以轻松集成新信息。元数据是帮助决定如何组织和存储数据的指标，根据数据类型，元数据具有各种名称。元数据的一些常用名称是标签、元素、实体和属性。例如，一封典型的电子邮件将有主题、正文和一组收件人，可以按发送人或发送时间进行组织。

<!-- Examples of semi-structured data: HTML, CSV files, JavaScript Object Notation (JSON) -->

半结构化数据的示例：HTML、CSV 文件、JavaScript 对象表示法 (JSON)

<!-- ## Sources of Data  -->
## 数据来源

<!-- A data source is the initial location of where the data was generated, or where it "lives" and will vary based on how and when it was collected. Data generated by its user(s) are known as primary data while secondary data comes from a source that has collected data for general use. For example, a group of scientists collecting observations in a rainforest would be considered primary and if they decide to share it with other scientists it would be considered secondary to those that use it.  -->
数据源是数据生成的初始位置，或数据“存在”的位置，会根据数据收集方式和时间而变化。用户生成的数据称为原始数据，而次要数据则来自收集用于一般用途的数据的来源。例如，一组科学家在雨林中收集观察结果，这被视为原始数据，如果他们决定与其他科学家分享，则对使用它的人来说，这被视为次要数据。


<!-- Databases are a common source and rely on a database management system to host and maintain the data where users use commands called queries to explore the data. Files as data sources can be audio, image, and video files as well as spreadsheets like Excel. Internet sources are a common location for hosting data, where databases as well as files can be found. Application programming interfaces, also known as APIs allow programmers to create ways to share data with external users through the internet, while the process of web scraping extracts data from a web page. The [lessons in Working with Data](/2-Working-With-Data) focus on how to use various data sources.  -->
数据库是一种常见的数据来源，依靠数据库管理系统来托管和维护数据，用户使用称为查询的命令来探索数据。作为数据源的文件可以是音频、图像和视频文件，也可以是 Excel 等电子表格。互联网源是托管数据的常见位置，数据库和文件都可以在这里找到。应用程序编程接口（也称为 API）允许程序员创建通过互联网与外部用户共享数据的方法，而网络抓取过程则从网页中提取数据。使用数据中的课程重点介绍如何使用各种数据源。

<!-- ## Conclusion

In this lesson we have learned:

- What data is
- How data is described
- How data is classified and categorized
- Where data can be found -->
<!-- 
## 🚀 Challenge

Kaggle is an excellent source of open datasets. Use the [dataset search tool](https://www.kaggle.com/datasets) to find some interesting datasets and classify 3-5 datasets with this criteria:

- Is the data quantitative or qualitative?
- Is the data structured, unstructured, or semi-structured?

## [Post-Lecture Quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/5)



## Review & Self Study

- This Microsoft Learn unit, titled [Classify your Data](https://docs.microsoft.com/en-us/learn/modules/choose-storage-approach-in-azure/2-classify-data) has a detailed breakdown of structured, semi-structured, and unstructured data.

## Assignment

[Classifying Datasets](assignment.md) -->
