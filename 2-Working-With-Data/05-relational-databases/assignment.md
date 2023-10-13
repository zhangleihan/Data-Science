# Displaying airport data

<!-- You have been provided a [database](https://raw.githubusercontent.com/Microsoft/Data-Science-For-Beginners/main/2-Working-With-Data/05-relational-databases/airports.db) built on [SQLite](https://sqlite.org/index.html) which contains information about airports. The schema is displayed below. You will use the [SQLite extension](https://marketplace.visualstudio.com/items?itemName=alexcvzz.vscode-sqlite&WT.mc_id=academic-77958-bethanycheum) in [Visual Studio Code](https://code.visualstudio.com?WT.mc_id=academic-77958-bethanycheum) to display information about different cities' airports. -->
我们为您提供了一个基于[SQLite](https://sqlite.org/index.html)构建的[数据库](https://raw.githubusercontent.com/Microsoft/Data-Science-For-Beginners/main/2-Working-With-Data/05-relational-databases/airports.db)，其中包含有关机场的信息。该架构如下所示。您将使用Visual Studio Code中的[SQLite 扩展](https://code.visualstudio.com?WT.mc_id=academic-77958-bethanycheum)来显示有关不同城市机场的信息。

## Instructions

<!-- To get started with the assignment, you'll need to perform a couple of steps. You'll need to install a bit of tooling and download the sample database. -->
要开始分配，您需要执行几个步骤。您需要安装一些工具并下载示例数据库。

### Setup your system

<!-- You can use Visual Studio Code and the SQLite extension to interact with the database. -->
您可以使用 Visual Studio Code 和 SQLite 扩展与数据库进行交互。

<!-- 1. Navigate to [code.visualstudio.com](https://code.visualstudio.com?WT.mc_id=academic-77958-bethanycheum) and follow the instructions to install Visual Studio Code -->
1. 导航到[code.visualstudio.com](https://code.visualstudio.com?WT.mc_id=academic-77958-bethanycheum)并按照说明安装 Visual Studio Code
<!-- 2. Install the [SQLite extension](https://marketplace.visualstudio.com/items?itemName=alexcvzz.vscode-sqlite&WT.mc_id=academic-77958-bethanycheum) extension as instructed on the Marketplace page -->
2.按照 Marketplace 页面上的说明安装[SQLite 扩展](https://marketplace.visualstudio.com/items?itemName=alexcvzz.vscode-sqlite&WT.mc_id=academic-77958-bethanycheum)插件

### Download and open the database

<!-- Next you will download an open the database. -->
接下来您将下载一个打开的数据库。

1. Download the [database file from GitHub](https://raw.githubusercontent.com/Microsoft/Data-Science-For-Beginners/main/2-Working-With-Data/05-relational-databases/airports.db) and save it to a directory
1. Open Visual Studio Code
1. Open the database in the SQLite extension by selecting **Ctl-Shift-P** (or **Cmd-Shift-P** on a Mac) and typing `SQLite: Open database`
1. Select **Choose database from file** and open the **airports.db** file you downloaded previously
1. After opening the database (you won't see an update on the screen), create a new query window by selecting **Ctl-Shift-P** (or **Cmd-Shift-P** on a Mac) and typing `SQLite: New query`

<!-- Once open, the new query window can be used to run SQL statements against the database. You can use the command **Ctl-Shift-Q** (or **Cmd-Shift-Q** on a Mac) to run queries against the database. -->
打开后，新的查询窗口可用于针对数据库运行 SQL 语句。您可以使用命令Ctl-Shift-Q（或Mac 上的Cmd-Shift-Q ）对数据库运行查询。

<!-- > [!NOTE] For more information about the SQLite extension, you can consult the [documentation](https://marketplace.visualstudio.com/items?itemName=alexcvzz.vscode-sqlite&WT.mc_id=academic-77958-bethanycheum) -->

> [!NOTE] 有关 SQLite 扩展的更多信息，可以查阅[文档](https://marketplace.visualstudio.com/items?itemName=alexcvzz.vscode-sqlite&WT.mc_id=academic-77958-bethanycheum)

## Database schema

<!-- A database's schema is its table design and structure. The **airports** database as two tables, `cities`, which contains a list of cities in the United Kingdom and Ireland, and `airports`, which contains the list of all airports. Because some cities may have multiple airports, two tables were created to store the information. In this exercise you will use joins to display information for different cities. -->

数据库的模式是它的表设计和结构。机场数据库airports由两个表组成：其中`cities`包含英国和爱尔兰的城市列表；`airports`包含所有机场的列表。由于某些城市可能有多个机场，因此创建了两个表来存储信息。在本练习中，您将使用联接来显示不同城市的信息。

| Cities           |
| ---------------- |
| id (PK, integer) |
| city (text)      |
| country (text)   |

| Airports                         |
| -------------------------------- |
| id (PK, integer)                 |
| name (text)                      |
| code (text)                      |
| city_id (FK to id in **Cities**) |

## Assignment

<!-- Create queries to return the following information: -->
创建查询以返回以下信息：
1. `Cities`表中所有城市名称
1. `Cities`表中的所有城市 爱尔兰
1. 所有机场名称及其城市和国家
1. 伦敦, 英国 的所有机场
<!-- 
1. all city names in the `Cities` table
1. all cities in Ireland in the `Cities` table
1. all airport names with their city and country
1. all airports in London, United Kingdom -->

## Rubric

| Exemplary | Adequate | Needs Improvement |
| --------- | -------- | ----------------- |
