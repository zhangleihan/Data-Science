<!-- # Assignment for Data Processing in Python -->
## 使用Python进行数据分析

<!-- In this assignment, we will ask you to elaborate on the code we have started developing in our challenges. The assignment consists of two parts: -->
本次作业要求理解作业模版预留代码的基础上完成指定的任务，作业由两部分组成：

<!-- ## COVID-19 Spread Modelling -->
## COVID-19 传播建模

 <!-- - [ ] Plot *R<sub>t</sub>* graphs for 5-6 different countries on one plot for comparison, or using several plots side-by-side
 - [ ] See how the number of deaths and recoveries correlate with number of infected cases.
 - [ ] Find out how long a typical disease lasts by visually correlating infection rate and deaths rate and looking for some anomalies. You may need to look at different countries to find that out.
 - [ ] Calculate the fatality rate and how it changes over time. *You may want to take into account the length of the disease in days to shift one time series before doing calculations* -->

 - [ ] 将 5-6 个不同国家的 *R<sub>t</sub>* 图绘制在同一张图上进行比较，或并排使用多张图
 - [ ] 观察死亡和康复人数与感染病例数量之间的关系。
 - [ ] 通过直观地关联感染率和死亡率并寻找一些异常数值点来判断典型疾病的持续时间，需要观察不同国家的数据才能找到相对准确的答案。
 - [ ] 计算死亡率及其随时间的变化情况。在进行计算之前，需要考虑疾病持续时间（以天为单位）以移动一个时间序列

<!-- ## COVID-19 Papers Analysis -->
## COVID-19 论文分析

<!-- - [ ] Build co-occurrence matrix of different medications, and see which medications often occur together (i.e. mentioned in one abstract). You can modify the code for building co-occurrence matrix for medications and diagnoses.
- [ ] Visualize this matrix using heatmap.
- [ ] As a stretch goal, visualize the co-occurrence of medications using [chord diagram](https://en.wikipedia.org/wiki/Chord_diagram). [This library](https://pypi.org/project/chord/) may help you draw a chord diagram.
- [ ] As another stretch goal, extract dosages of different medications (such as **400mg** in *take 400mg of chloroquine daily*) using regular expressions, and build dataframe that shows different dosages for different medications. **Note**: consider numeric values that are in close textual vicinity of the medicine name. -->

- [ ] 建立不同药物的共现矩阵，并查看哪些药物经常一起出现（即在一个摘要中提及）。您可以修改用于建立药物和诊断的共现矩阵的代码。
- [ ] 使用热图可视化该矩阵。
- [ ] 作为延伸目标，使用弦图[chord diagram](https://en.wikipedia.org/wiki/Chord_diagram)可视化药物的共现。 [此库](https://pypi.org/project/chord/)可用于绘制弦图。
- [ ] 作为另一个延伸目标，使用正则表达式提取不同药物的剂量（例如每日服用**400mg**氯喹中的 400 毫克），并构建显示不同药物不同剂量的数据框。注意：考虑药品名称文本附近的数值。


## Rubric

Exemplary | Adequate | Needs Improvement
--- | --- | -- |
所有任务均已完成，并以图形方式说明和解释，包括两个延伸目标中的至少一个 | 已完成 4 项以上任务，未尝试任何延伸目标，或结果不明确 | 少于 4 个（但多于 2 个）任务已完成，但可视化无助于证明关键结论
