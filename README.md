# 2023美赛c题

2023美赛只有c题提供了相关数据，为了避免在数据挖掘中出现问题，我们也从众选择了c。Wordle是一个猜字游戏，他的相关算法及其解决方案在GitHub上面已有很多大佬进行了分享，他们的相关算法也对我们的解题提供了宝贵的idea。

### 问题1

在我们观察excel的时候发现存在数据记录错误的问题，如四字的异常单词clen，明显少了的Number of  reported results等，由于数据很少，我们就在twitter上找到了对应的数据进行更新。

思路：1.基于现有数据使用**ARIMA模型**建立报告结果数的时间序列回归模型，预测2023年3月1日的报告结果数。结果以当天的 95% 置信区间进行预测。使用**基于生命周期形状提取的分段线性回归**方法提取模型的形状，然后进行聚类，将它识别时间序列模型分为四个阶段来解释Number of  reported results的变化趋势。

2.寻找能够描述单词的具体属性，判断这些属性是正向或是负向性并进行归一化之后建立以属性作为自变量，困难模式下报告的各自占比作为因变量列7个回归方程进行预测，这些方程之间也有相应关系，相加之后接近100%。

### 问题2

本题是对于一个**给定的未来日期的解字**建立一个预测模型，我们使用偏最小二乘回归模型由单词属性计算报告占比。由于离散数据较多，本文采用**Apriori算法**建立变量与单词难度的相关规则，并根据其规则的置信度建立混合指标。回归模型中的自变量包括单词出现频率、正交数、字母重复数和混合指数（混合了单词词性、是否属于外来词和是否具有学科专业性三个指标）。最终的预测结果为（**1=0%, 2=2%, 3=15%, 4=33%, 5=30%, 6=16%, X=4%**）。不确定因素有社交媒体、当代新闻、全球流行病等。

### 问题3

为了建立一个难度分类模型，我们通过**系统聚类**的肘部法则将难度分为三类，即为难、中、易，使用簇识别思想根据聚类结果给出分类的相关属性识别，并找出簇中心，以便使用**欧式距离**进行单词难度划分。准确性方面，我们使用**判别分析-回判法**得出类判别矩阵，并根据矩阵得出模型准确性。将eerie的相关属性带入到欧式距离中得出它的难度等级为易。

### 问题4

在数据集中挖掘有趣的特征。

参考了如下网址： http://www.neuro.mcw.edu/mcword/（单词正交型数量）

​								https://www.english-corpora.org/coca/（COCA语料库）

~~一次数模。终身受益；十次数模，痛哭流涕。~~
最终获得了此次美赛的H奖，感谢我的数模队友。也将本次心路历程作为一个纪念放在这里，也许会有人看到，也许不会。