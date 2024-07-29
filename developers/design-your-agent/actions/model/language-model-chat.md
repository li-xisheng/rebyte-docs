# 语言模型对话

## 用法

我们提供 `Language Model Chat` 动作以便轻松与大型语言模型聊天并创建复杂的用途。

要使用此动作，您只需编写您的规范并配置模型，大型语言模型将生成响应。

### 规范

<figure><img src="../../../../images/chat-spec.png" alt=""><figcaption></figcaption></figure>

**指令**

* 这是将发送到模型的消息。
* 在这里编写您的提示，告诉大型语言模型该做什么。
* 支持 [Tera](https://keats.github.io/tera/docs/) 格式。例如，您可以使用 `{{INPUT.messages[0].content}}` 获取代理输入的第一条消息的内容。

**消息**

* 这些是将发送到 LLM 的消息。
* 您可以在此处使用 Javascript 或 Tera 格式引用其他动作的输出。
* 消息可以是字符串列表或对象列表。如果它是对象列表，请确保每个对象都有一个 `role` 字段以及一个 `content` 字段：
  * `role` 字段指定消息的角色，允许的角色是 `user`、`assistant` 和 `system`。
  * `content` 包含将发送到模型的消息。
* 使用 **Javascript** 格式，例如，您可以使用 `env.state.INPUT.messages` 获取代理输入。
* **注意**：请确保返回一个数组。
* **注意**：如果您希望模型对话具有上下文，您应该使用 `Thread message loader` 动作来记录和加载历史消息。有关此动作的更多信息，请参见[此处](../tools/thread-message-loader.md)。

**函数**

* 函数调用允许您通过描述 API 调用中的函数将大型语言模型连接到外部工具，从而使模型能够智能地生成包含调用一个或多个函数的参数的 JSON 对象。
* 这种能力提供了一种从模型获取结构化数据的方法，使得可以创建与外部 API 交互的助手，并将自然语言转换为 API 调用。
* 使用 **Javascript** 格式。
* [此处](function-calling.md) 是一个详细的使用“函数”的示例。

### 配置

您可以通过点击模型名称选择要使用的模型，默认模型是 "gpt-3.5-turbo-1106"。

<figure><img src="../../../../images/chat-models.png" alt=""><figcaption></figcaption></figure>

点击 `Language Model Chat` 动作右下角的此按钮以打开配置面板。

<figure><img src="../../../../images/chat-config-button.jpg" alt=""><figcaption></figcaption></figure>

配置面板中有五个设置，如下所示。

<div align="center">

<figure><img src="../../../../images/chat-config-2.png" alt="" height="60%" width="60%"><figcaption></figcaption></figure>

</div>

**温度**

* “温度”控制模型输出的随机性。
* 模型温度越高，输出越随机。

**最大输出令牌**

* “最大输出令牌”指定要生成的最大令牌数。
* 可以使用最多 40,000 个令牌（模型的限制各不相同），包括提示和模型返回的内容。

**JSON 响应**

* "JSON Response" 按钮启用 JSON 模式，确保模型生成的消息为 JSON 格式。
* 注意：此功能是测试功能，目前仅支持 OpenAI 的 "gpt-4-1106-preview" 模型。
* 注意：使用此功能时，请确保上下文中包含“JSON”一词。否则，OpenAI 的 API 会抛出错误。

**种子**

* “种子”是在使用 `Language Model Chat` 和 `Language Model Completion` 动作时可以指定的参数。
* 它通过使系统确定性地采样，确保一致的输出，从而在使用相同种子和参数进行重复请求时产生相同的结果。
* 注意：此功能是测试功能，可能并非所有模型都支持。

**停止词**

* 停止词用于使模型在预期点停止，例如句子或列表的结尾。

在动作的右上角，还有两个可以配置的选项：“流模式”和“缓存模式”。

<figure><img src="../../../../images/stream-and-cache.jpg" alt=""><figcaption></figcaption></figure>

**流**

* 此选项允许您在生成部分聊天响应时接收它们，而不是等待整个完成后才接收响应。
* 通过设置流模式，您可以在收到完整响应之前开始处理或显示聊天的开头。

**缓存**

* 缓存涉及存储频繁访问的数据，以提高响应时间，而无需重复调用模型。
* 如果使用缓存模式，模型将缓存响应，并在再次发出相同请求时返回缓存的响应。这将使您的代理运行更快。

### 消息格式

ReByte 使用类似于 OpenAI 的消息格式。消息格式是一个包含以下字段的 JSON 对象：

* 角色：可以是 'user'、'system' 或 'assistant' 中的一个。
* 内容：此消息的内容。
* 名称（可选）：角色名称。
* 上下文（可选）：此消息的上下文。

**消息格式示例**

1. 简单消息

```json
{
    "content": "Hello, how are you?",
    "role": "user",
    "name": "meowoof",
    "context": {
        "files": [
            {
                "uuid": "f3610fef-f490-4675-81fe-df04735f5058",
                "name": "file1.pdf"
            },
            {
                "name": "f3610fef-f490-4675-81fe-df04735f5059",
                "content": "file2.txt"
            }   
        ]
    }
}
```

2. 消息列表

```json
[
    {
        "content": "You're talking to a chatbot!",
        "role": "system"
    },
    {
        "content": "Hello, how are you?",
        "role": "user",
        "name": "meowoof"
    },
    {
        "content": "I am fine, thank you.",
        "role": "assistant",
        "name": "rebyte"
    },
    {
        "content": "what's your plan today?",
        "role": "user",
        "name": "meowoof"
    }
]
```

## 示例工具

* [Language Model Chat](https://rebyte.ai/p/21b2295005587a5375d8/callable/719d2f31bf9fe977f699/editor)
