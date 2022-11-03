# CFSC-ABSA 单字分词版
该项目提供了15446条中文金融新闻语句，总共包含方面词41496个，以一个方面词作为一条数据。训练集样本为33184条，测试集样本为8312条(8:2)。每条数据都由语句文本、方面词位置、方面词、方面极性组成，句子最大长度不超过512，情感极性分为积极、中立、消极。

### CFSC-ABSA数据集情感分布情况(详)
---
|类别|积极(train)|积极(test)|中立(train)|中立(test)|消极(train)|消极(test)|合计|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|公司(Corporate)|2970|711|2629|696|1220|323|8549|
|股票(Stock)|6667|1691|321|52|3236|770|12737|
|市场(Market)|5385|1363|454|103|2131|526|9946|
|经济(Economy)|5363|1369|824|181|1984|527|10264|

## Example
---
数据中每三行为一条数据，第一行为语句文本，其中方面词所在位置为`$T$`，第二行是方面词，第三行是该方面词的情感极性，1为积极，0为中立，-1为消极。
```
$T$ 开 盘 跌 0 . 2 % 。
富 时 中 国 A 5 0 指 数 期 货
-1
```

## Reference
****
如果您要使用这些数据，请做如下引用。

Shen Li, Zhe Zhao, Renfen Hu, Wensi Li, Tao Liu, Xiaoyong Du, Analogical Reasoning on Chinese Morphological and Semantic Relations, ACL 2018.
```
@InProceedings{P18-2023,
  author =  "Li, Shen
    and Zhao, Zhe
    and Hu, Renfen
    and Li, Wensi
    and Liu, Tao
    and Du, Xiaoyong",
  title =   "Analogical Reasoning on Chinese Morphological and Semantic Relations",
  booktitle =   "Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 2: Short Papers)",
  year =  "2018",
  publisher =   "Association for Computational Linguistics",
  pages =   "138--143",
  location =  "Melbourne, Australia",
  url =   "http://aclweb.org/anthology/P18-2023"
}
```
