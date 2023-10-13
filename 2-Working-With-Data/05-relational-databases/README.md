# Working with Data: Relational Databases

|![ Sketchnote by [(@sketchthedocs)](https://sketchthedocs.dev) ](../../sketchnotes/05-RelationalData.png)|
|:---:|
| Working With Data: Relational Databases - _Sketchnote by [@nitya](https://twitter.com/nitya)_ |

<!-- Chances are you have used a spreadsheet in the past to store information. You had a set of rows and columns, where the rows contained the information (or data), and the columns described the information (sometimes called metadata). A relational database is built upon this core principle of columns and rows in tables, allowing you to have information spread across multiple tables. This allows you to work with more complex data, avoid duplication, and have flexibility in the way you explore the data. Let's explore the concepts of a relational database. -->
您过去很可能使用电子表格来存储信息。您有一组行和列，其中行包含信息（或数据），列描述信息（有时称为元数据）。关系数据库是基于表中的列和行的核心原则构建的，允许您将信息分布在多个表中。这使您可以处理更复杂的数据，避免重复，并灵活地探索数据。让我们探讨一下关系数据库的概念。

## [Pre-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/8)

## It all starts with tables

<!-- A relational database has at its core tables. Just as with the spreadsheet, a table is a collection of columns and rows. The row contains the data or information we wish to work with, such as the name of a city or the amount of rainfall. The columns describe the data they store. -->
关系数据库的核心是表。就像电子表格一样，表格是列和行的集合。该行包含我们希望使用的数据或信息，例如城市名称或降雨量。这些列描述了它们存储的数据。

<!-- Let's begin our exploration by starting a table to store information about cities. We might start with their name and country. You could store this in a table as follows: -->
让我们通过创建一个表来存储有关城市的信息来开始我们的探索。我们可以从他们的名字和国家开始。您可以将其存储在表中，如下所示：

| City     | Country       |
| -------- | ------------- |
| Tokyo    | Japan         |
| Atlanta  | United States |
| Auckland | New Zealand   |

<!-- Notice the column names of **city**, **country** and **population** describe the data being stored, and each row has information about one city. -->
请注意，城市、国家和人口的列名描述了存储的数据，每一行都有一个城市的信息。

## The shortcomings of a single table approach

<!-- Chances are, the table above seems relatively familiar to you. Let's start to add some additional data to our burgeoning database - annual rainfall (in millimeters). We'll focus on the years 2018, 2019 and 2020. If we were to add it for Tokyo, it might look something like this: -->
您可能对上表比较熟悉。让我们开始向我们不断发展的数据库添加一些额外的数据 - 年降雨量（以毫米为单位）。我们将重点关注 2018 年、2019 年和 2020 年。如果我们为东京添加它，它可能看起来像这样：

| City  | Country | Year | Amount |
| ----- | ------- | ---- | ------ |
| Tokyo | Japan   | 2020 | 1690   |
| Tokyo | Japan   | 2019 | 1874   |
| Tokyo | Japan   | 2018 | 1445   |

<!-- What do you notice about our table? You might notice we're duplicating the name and country of the city over and over. That could take up quite a bit of storage, and is largely unnecessary to have multiple copies of. After all, Tokyo has just the one name we're interested in. -->
您可能会注意到我们的表格一遍又一遍地重复城市的名称和国家/地区。这可能会占用相当多的存储空间，并且基本上没有必要拥有多个副本。毕竟，东京只有一个我们感兴趣的名字。

<!-- OK, let's try something else. Let's add new columns for each year: -->
让我们为每年添加新列：

| City     | Country       | 2018 | 2019 | 2020 |
| -------- | ------------- | ---- | ---- | ---- |
| Tokyo    | Japan         | 1445 | 1874 | 1690 |
| Atlanta  | United States | 1779 | 1111 | 1683 |
| Auckland | New Zealand   | 1386 | 942  | 1176 |

<!-- While this avoids the row duplication, it adds a couple of other challenges. We would need to modify the structure of our table each time there's a new year. Additionally, as our data grows having our years as columns will make it trickier to retrieve and calculate values. -->
虽然这避免了行重复，但它增加了一些其他挑战。每次新的一年到来时，我们都需要修改表的结构。此外，随着数据的增长，列的年数将使检索和计算值变得更加困难。

<!-- This is why we need multiple tables and relationships. By breaking apart our data we can avoid duplication and have more flexibility in how we work with our data. -->
这就是为什么我们需要多个表和关系。通过分解数据，我们可以避免重复，并在处理数据的方式上拥有更大的灵活性。

## The concepts of relationships

<!-- Let's return to our data and determine how we want to split things up. We know we want to store the name and country for our cities, so this will probably work best in one table. -->
让我们回到我们的数据并确定我们想要如何分割数据。我们知道我们想要存储城市的名称和国家/地区，因此这可能在一张表中效果最好。

| City     | Country       |
| -------- | ------------- |
| Tokyo    | Japan         |
| Atlanta  | United States |
| Auckland | New Zealand   |

<!-- But before we create the next table, we need to figure out how to reference each city. We need some form of an identifier, ID or (in technical database terms) a primary key. A primary key is a value used to identify one specific row in a table. While this could be based on a value itself (we could use the name of the city, for example), it should almost always be a number or other identifier. We don't want the id to ever change as it would break the relationship. You will find in most cases the primary key or id will be an auto-generated number. -->
但在创建下一个表之前，我们需要弄清楚如何引用每个城市。我们需要某种形式的标识符、ID 或（在技术数据库术语中）主键。主键是用于标识表中的一个特定行的值。虽然这可以基于值本身（例如，我们可以使用城市的名称），但它几乎应该始终是数字或其他标识符。我们不希望 id 发生改变，因为这会破坏关系。您会发现在大多数情况下主键或 id 将是自动生成的数字。

> ✅ Primary key is frequently abbreviated as PK

### cities

| city_id | City     | Country       |
| ------- | -------- | ------------- |
| 1       | Tokyo    | Japan         |
| 2       | Atlanta  | United States |
| 3       | Auckland | New Zealand   |

<!-- > ✅ You will notice we use the terms "id" and "primary key" interchangeably during this lesson. The concepts here apply to DataFrames, which you will explore later. DataFrames don't use the terminology of "primary key", however you will notice they behave much in the same way. -->
> ✅ 您会注意到，在本课程中，我们交替使用术语“id”和“主键”。这里的概念适用于 DataFrame，您稍后将探讨它。DataFrame 不使用“主键”术语，但是您会注意到它们的行为方式大致相同。

<!-- With our cities table created, let's store the rainfall. Rather than duplicating the full information about the city, we can use the id. We should also ensure the newly created table has an *id* column as well, as all tables should have an id or primary key. -->
创建城市表后，让我们存储降雨量。我们可以使用 id，而不是复制有关城市的完整信息。我们还应该确保新创建的表也有一个id列，因为所有表都应该有一个 id 或主键。

### rainfall

| rainfall_id | city_id | Year | Amount |
| ----------- | ------- | ---- | ------ |
| 1           | 1       | 2018 | 1445   |
| 2           | 1       | 2019 | 1874   |
| 3           | 1       | 2020 | 1690   |
| 4           | 2       | 2018 | 1779   |
| 5           | 2       | 2019 | 1111   |
| 6           | 2       | 2020 | 1683   |
| 7           | 3       | 2018 | 1386   |
| 8           | 3       | 2019 | 942    |
| 9           | 3       | 2020 | 1176   |

<!-- Notice the **city_id** column inside the newly created **rainfall** table. This column contains values which reference the IDs in the **cities** table. In technical relational data terms, this is called a **foreign key**; it's a primary key from another table. You can just think of it as a reference or a pointer. **city_id** 1 references Tokyo. -->
请注意新创建的降雨量表中的city_id列。此列包含引用城市表中的 ID 的值。在技​​术关系数据术语中，这称为外键；它是另一个表的主键。您可以将其视为引用或指针。city_id 1 引用东京。

> [!NOTE] Foreign key is frequently abbreviated as FK

## Retrieving the data

<!-- With our data separated into two tables, you may be wondering how we retrieve it. If we are using a relational database such as MySQL, SQL Server or Oracle, we can use a language called Structured Query Language or SQL. SQL (sometimes pronounced sequel) is a standard language used to retrieve and modify data in a relational database. -->
由于我们的数据分为两个表，您可能想知道我们如何检索它。如果我们使用 MySQL、SQL Server 或 Oracle 等关系数据库，我们可以使用一种称为结构化查询语言或 SQL 的语言。SQL（有时发音为sequel）是一种用于检索和修改关系数据库中的数据的标准语言。

<!-- To retrieve data you use the command `SELECT`. At its core, you **select** the columns you want to see **from** the table they're contained in. If you wanted to display just the names of the cities, you could use the following: -->
要检索数据，请使用命令SELECT。其核心是，您可以从包含的表中选择要查看的列。如果您只想显示城市的名称，可以使用以下命令：

```sql
SELECT city
FROM cities;

-- Output:
-- Tokyo
-- Atlanta
-- Auckland
```

<!-- `SELECT` is where you list the columns, and `FROM` is where you list the tables. -->
SELECT是列出列的位置，FROM也是列出表的位置。

<!-- > [NOTE] SQL syntax is case-insensitive, meaning `select` and `SELECT` mean the same thing. However, depending on the type of database you are using the columns and tables might be case sensitive. As a result, it's a best practice to always treat everything in programming like it's case sensitive. When writing SQL queries common convention is to put the keywords in all upper-case letters. -->
> [NOTE] SQL语法不区分大小写，含义select和SELECT意思是一样的。但是，根据您使用的数据库类型，列和表可能区分大小写。因此，最佳实践是始终将编程中的所有内容视为区分大小写。编写 SQL 查询时，常见的约定是将关键字全部大写。

<!-- The query above will display all cities. Let's imagine we only wanted to display cities in New Zealand. We need some form of a filter. The SQL keyword for this is `WHERE`, or "where something is true". -->
上面的查询将显示所有城市。假设我们只想显示新西兰的城市。我们需要某种形式的过滤器。其 SQL 关键字是WHERE, 或“某事为真”。

```sql
SELECT city
FROM cities
WHERE country = 'New Zealand';

-- Output:
-- Auckland
```

## Joining data

<!-- Until now we've retrieved data from a single table. Now we want to bring the data together from both **cities** and **rainfall**. This is done by *joining* them together. You will effectively create a seam between the two tables, and match up the values from a column from each table. -->
到目前为止，我们已经从单个表中检索数据。现在我们想要将城市和降雨量的数据整合在一起。这是通过将它们连接在一起来完成的。您将有效地在两个表之间创建一个连接，并匹配每个表的列中的值。

<!-- In our example, we will match the **city_id** column in **rainfall** with the **city_id** column in **cities**. This will match the rainfall value with its respective city. The type of join we will perform is what's called an *inner* join, meaning if any rows don't match with anything from the other table they won't be displayed. In our case every city has rainfall, so everything will be displayed. -->
在我们的示例中，我们将降雨量中的city_id列与城市中的city_id列进行匹配。这将使降雨量值与其各自的城市相匹配。我们将执行的联接类型称为内部联接，这意味着如果任何行与其他表中的任何内容不匹配，则它们将不会显示。在我们的例子中，每个城市都有降雨，所以一切都会显示出来。

<!-- Let's retrieve the rainfall for 2019 for all our cities. -->
让我们检索所有城市 2019 年的降雨量。

<!-- We're going to do this in steps. The first step is to join the data together by indicating the columns for the seam - **city_id** as highlighted before. -->
我们将分步骤进行。第一步是通过指示接缝的列 - city_id（如之前突出显示的那样）将数据连接在一起。

```sql
SELECT cities.city
    rainfall.amount
FROM cities
    INNER JOIN rainfall ON cities.city_id = rainfall.city_id
```

<!-- We have highlighted the two columns we want, and the fact we want to join the tables together by the **city_id**. Now we can add the `WHERE` statement to filter out only year 2019. -->
我们突出显示了我们想要的两列，以及我们想要通过city_id将表连接在一起的事实。现在我们可以添加WHERE语句来仅过滤掉 2019 年。



```sql
SELECT cities.city
    rainfall.amount
FROM cities
    INNER JOIN rainfall ON cities.city_id = rainfall.city_id
WHERE rainfall.year = 2019

-- Output

-- city     | amount
-- -------- | ------
-- Tokyo    | 1874
-- Atlanta  | 1111
-- Auckland |  942
```

## Summary

<!-- Relational databases are centered around dividing information between multiple tables which is then brought back together for display and analysis. This provides a high degree of flexibility to perform calculations and otherwise manipulate data. You have seen the core concepts of a relational database, and how to perform a join between two tables. -->
关系数据库的核心是在多个表之间划分信息，然后将这些信息重新组合在一起进行显示和分析。这为执行计算和以其他方式操作数据提供了高度的灵活性。您已经了解了关系数据库的核心概念，以及如何在两个表之间执行联接。

## 🚀 Challenge

<!-- There are numerous relational databases available on the internet. You can explore the data by using the skills you've learned above. -->
互联网上有许多可用的关系数据库。您可以使用上面学到的技能来探索数据。

## Post-Lecture Quiz

## [Post-lecture quiz](https://purple-hill-04aebfb03.1.azurestaticapps.net/quiz/9)

## Review & Self Study

There are several resources available on [Microsoft Learn](https://docs.microsoft.com/learn?WT.mc_id=academic-77958-bethanycheum) for you to continue your exploration of SQL and relational database concepts

- [Describe concepts of relational data](https://docs.microsoft.com//learn/modules/describe-concepts-of-relational-data?WT.mc_id=academic-77958-bethanycheum)
- [Get Started Querying with Transact-SQL](https://docs.microsoft.com//learn/paths/get-started-querying-with-transact-sql?WT.mc_id=academic-77958-bethanycheum) (Transact-SQL is a version of SQL)
- [SQL content on Microsoft Learn](https://docs.microsoft.com/learn/browse/?products=azure-sql-database%2Csql-server&expanded=azure&WT.mc_id=academic-77958-bethanycheum)

## Assignment

[Assignment Title](assignment.md)
