# 数据集

设计完代理后，您可以使用数据集对其进行测试。

您可以使用“运行测试用例”来运行数据集，并观察代理的响应，可能会根据需要进行故障排除。

## 数据集创建

* 导航到顶部的 `Datasets` 标签。

* 点击 `Create Dataset`。

* 使用“Add Column”添加新字段到数据集中。使用“Add Row”添加新的数据集项。

<figure><img src="../../images/datasets.png" alt=""><figcaption></figcaption></figure>

## 支持的数据类型

我们支持以下数据类型：

* String
* Number
* Boolean
* JSON Object

## 用法

数据集可以通过两种方式使用：

#### 1.加载数据以供后续操作使用

加载的数据集可以被后续操作使用。

当数据集中包含用于 few-shots 提示的示例数据时，这非常有用。

#### 2.确定代理的输入形状

`Input` 操作的数据集确定整个代理的输入形状。
