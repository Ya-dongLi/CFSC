- [CFSC数据集](#cfsc数据集)
      - [数据集分布情况](#数据集分布情况)
  - [CFSC-ABSA](#cfsc-absa)
      - [CFSC-ABSA数据集情感分布情况](#cfsc-absa数据集情感分布情况)
    - [Example](#example)
  - [CFSC-NER](#cfsc-ner)
      - [CFSC-NER数据集金融实体类别分布情况](#cfsc-ner数据集金融实体类别分布情况)
    - [Example](#example-1)
      - [原始数据](#原始数据)
      - [BIO标注数据](#bio标注数据)
  - [Reference](#reference)
# CFSC数据集
CFSC数据集总共包含用于情感分析的CFSC-ABSA和用于命名实体识别的CFSC-NER两个子数据集。

#### 数据集分布情况(语句数量)
|数据集|公司(Corporate)|股票(Stock)|市场(Market)|经济(Economy)|合计|实体数|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|CFSC-ABSA|5303|2826|3378|3939|15446|41496|
|CFSC-NER|2667|2666|2297|3037|10667|29181|

## CFSC-ABSA
该数据集提供了15446条中文金融新闻语句，总共包含方面词41496个，以一个方面词作为一条数据。训练集样本为33184条，测试集样本为8312条(8:2)。每条数据都由语句文本、方面词位置、方面词、方面极性组成，句子最大长度不超过512，情感极性分为积极、中立、消极。除了所有数据以外，我们额外提供了[json格式](/CFSC-ABSA/json格式)、[词语分词](/CFSC-ABSA/词语分词)、[单字分词](/CFSC-ABSA/单字分词)、[未分词](/CFSC-ABSA/未分词)四种形式且划分了训练集和测试集的数据。

#### CFSC-ABSA数据集情感分布情况
|类别|积极(positive)|中立(neutral)|消极(negative)|合计|
|:-:|:-:|:-:|:-:|:-:|
|公司(Corporate)|3681|3325|1543|8549|
|股票(Stock)|8358|373|4006|12737|
|市场(Market)|6732|557|2657|9946|
|经济(Economy)|6748|1005|2511|10264|

### Example
CFSC-ABSA-Alldata.json文件包含了所有数据。数据集为列表形式，列表中的一个元素就是一条JSON格式的数据。`"sentence"`为语句文本，`"Level 1 aspect"`为该条文本的所属分类(Corporate、Stock、Economy、Market)，`"term"`为方面词，`"polarity"`为情感极性(positive、neutral、negative)，`"from"`为方面词开始位置，`"to"`为方面词结束位置。
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

## CFSC-NER
该数据集提供了10667条中文金融新闻语句，总共包含金融实体29181个，以单一句子作为一条数据。训练集样本数为8533，验证集样本为1067，测试集样本为1067(8:1:1)。每条数据都由语句文本、金融实体位置、金融实体、金融实体的类别构成，句子的最大长度不超过`x`，金融实体的类别分为Corporate(公司)、Stock(股票)、Market(市场)、Economy(经济)。除了所有数据以外，我们额外提供了划分了训练集、验证集和测试集的数据以及[BIO标注](/CFSC-NER/BIO)数据。

#### CFSC-NER数据集金融实体类别分布情况
| 金融实体类别 | 公司(Corporate) | 股票(Stock) | 市场(Market) | 经济(Economy) |   合计  |
| :----: | :-----------: | :-------: | :--------: | :---------: | :---: |
|  实体数量  |      3841     |   11113   |    6621    |     7606    | 29181 |

### Example
#### 原始数据
CFSC-NER-Alldata.json包含所有数据，json格式文件夹下包含划分好训练集、验证集和测试集的数据。原始数据集为列表形式，列表中每个元素都是一条JSON格式的数据。`"text"`为语句文本，`"labels"`为JSON内部的一个列表，列表内包含若干字典，每个字典包含了语句中金融实体的信息，其中`"text"`为金融实体文本，`"Level 1 Aspect"`为金融实体类别，`"from"`为该实体在语句中的起止位置，`"to"`为该实体在句中的结束位置。
```
[
  {
    "text": "联想集团2022财年第四季度营收166.9亿美元，预估176亿美元，净利润4.12亿美元，预估3.536亿美元。",
    "labels": [
      {
        "text": "联想集团",
        "Level 1 Aspect": "Corporate",
        "from": 0,
        "to": 4
      }
    ]
  },
  {
    "text": "指数低开高走，沪指拉升涨逾1%，深成指涨1.49%，创业板指涨2.92%。",
    "labels": [
      {
        "text": "沪指",
        "Level 1 Aspect": "Stock",
        "from": 7,
        "to": 9
      },
      {
        "text": "深成指",
        "Level 1 Aspect": "Stock",
        "from": 16,
        "to": 19
      },
      {
        "text": "创业板指",
        "Level 1 Aspect": "Stock",
        "from": 26,
        "to": 30
      }
    ]
  }
]
```
#### BIO标注数据
通过代码对原始数据集进行处理，输出BIO标注格式数据，可直接进入支持BIO标注的模型进行训练。
```
实	B-Corporate
丰	I-Corporate
文	I-Corporate
化	I-Corporate
公	O
告	O
，	O
公	O
司	O
与	O
中	B-Corporate
科	I-Corporate
翎	I-Corporate
碳	I-Corporate
签	O
订	O
了	O
《	O
战	O
略	O
合	O
作	O
·
·
·
```

## Reference
如果您要使用这些数据，请做如下引用。

aaa
```
aaa
```
