# 函数调用

## 示例 1

这是如何使用“函数”功能的简单演示。

* 首先，取消注释“函数”部分的代码。

<figure><img src="../../../../images/openai-functions.png"></figure>

* 这是一个天气 API 的详细描述。您可以使用此 API 获取城市的天气信息。

* 对于任何给定的输入，模型将查看是否需要调用您的函数。

* 如果需要，它将给出调用函数所需的参数的 JSON。

<figure><img src="../../../../images/openai-functions-1.png"></figure>

* 否则，它将像正常聊天机器人一样响应。

<figure><img src="../../../../images/openai-functions-2.png"></figure>

* **注意**：如果您使用“函数”功能，您应该使用另一个动作来调用实际的函数 API。语言模型只会给出调用函数 API 所需的参数。

## 示例 2

这是如何使用“函数”功能的更复杂示例。

我将向您展示如何使用“函数”功能以及如何将“函数”功能的结果连接到“Http Request Maker”以调用实际的函数 API。
