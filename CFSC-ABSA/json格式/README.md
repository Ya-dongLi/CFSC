# CFSC-ABSA JSON版
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
数据集为列表形式，列表中的一个元素就是一条JSON格式的数据。`"sentence"`为语句文本，`"Level 1 aspect"`为该条文本的所属分类(Corporate、Stock、Economy、Market)，`"term"`为方面词，`"polarity"`为情感极性(positive、neutral、negative)，`"from"`为方面词开始位置，`"to"`为方面词结束位置。
```
[{
"sentence": "6月，我国高新技术产品出口607.6亿美元，进口537.3亿美元。\n", 
"Level 1 aspect": "Economy", 
"term": "高新技术产品出口", 
"polarity": "neutral", 
"from": 5, 
"to": 13
},{
"sentence": "法媒关注：印度卢比跌至历史新低\n", 
"Level 1 aspect": "Economy", 
"term": "印度卢比", 
"polarity": "negative", 
"from": 5, 
"to": 9
}]
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
