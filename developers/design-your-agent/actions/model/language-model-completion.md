# 语言模型完成

我们提供 `Language Model Completion` 动作，让语言模型完成您的提示。

## 用法

* 向您的代理添加一个 `Language Model Completion` 动作。
* 使用规范和参数配置该动作。

### 规范

<figure><img src="../../../../images/completion.png" alt=""><figcaption></figcaption></figure>

**提示**

* 这是将发送到模型的提示。
* 模型将完成您的提示并以完成的内容进行响应。

### 配置

配置与 [语言模型对话](language-model-chat.md) 相同。

您可以通过点击模型名称选择要使用的模型，默认模型是 "gpt-3.5-turbo-1106"。

<figure><img src="../../../../images/chat-models.png" alt=""><figcaption></figcaption></figure>

点击 `Language Model Completion` 动作右下角的此按钮以打开配置面板。

<figure><img src="../../../../images/chat-config-button.jpg" alt=""><figcaption></figcaption></figure>

配置面板中有五个设置，如下所示。

<figure><img src="../../../../images/chat-config-2.png" alt=""><figcaption></figcaption></figure>

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

* “种子”是在使用 `Language Model Completion` 和 `Language Model Completion` 动作时可以指定的参数。
* 它通过使系统确定性地采样，确保一致的输出，从而在使用相同种子和参数进行重复请求时产生相同的结果。
* 注意：此功能是测试功能，目前仅支持 OpenAI 的模型。

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

1. 提示示例

```xml
Your role is that of a text editor. 
You are expected to peruse the texts provided to you, comprehending them fully, and then distill and summarize them for me. The summary should encapsulate the main theme and essential details of the original text. It should be succinct and expressed in your own words. 
The contents that need to be summarized will be enclosed within three single quotation marks.

The summary should be conducted in accordance with the following regulations:
1. Thematic Statement: Succinctly summarize the main theme or key point of the original text. 
2. Key Details: Enumerate the crucial details or facts from the original text that support the main theme or point. 
3. Overall Conclusion: Distill the conclusion of the original text or the position of the author.

Please organize the summary according to the following structure and reply me:
Introduction: Introduce the main theme or background of the original text.(New line)
Body Paragraph: List and explain the key details and arguments from the original text, summarizing them in your own words. (New line)
Conclusion: Summarize the main points of the original text or present the author's conclusion.(New line)

This is the content that requires summarization:

please reply to me with the phrase: "I apologize for being unable to retrieve content from the URL you provided. Please verify the correctness of the web address"

{{CODE_1.content}}
```

## 示例工具

* [语言模型完成](https://rebyte.ai/p/21b2295005587a5375d8/callable/719d2f31bf9fe977f699/editor)
