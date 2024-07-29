# 输入

* `输入动作` 用于将输入信息发送到工具。其他动作基于输入信息执行相应的操作。

* 工具中的第一个动作必须是 `输入动作`，您不能删除或复制它。

* 在设计模式中，您可以指定一个数据集作为输入，每个数据中的每一行将被视为代理的单独输入，所有输入将并行运行。每行数据将收到一个单独的线程 ID。

* 在生产模式中，输入通过代理 API 传递。

* ReByte 定义了一种通用的数据结构来处理传递到代理中的消息，强烈建议使用此格式，以便使您的代理能够与助手/线程 API 无缝配合。

## 通用消息格式

不同的 LLM 具有不同的消息格式，但 ReByte 定义了一种通用的消息格式来处理传递到代理中的消息，我们将在内部处理所有兼容性问题。

**文本消息**

```json
{
  "role": "role of this message, for example user, assistant",
  "content": "content string of this messages"
}
```

**带图片 URL 的消息**

```json
{
  "role": "user",
  "content": "content string of this messages",
  "parts": [
    {
      "type": "image_url",
      "image_url": {
        "url": "url of this image"
      }
    }
  ]
}
```

**带图片数据的消息**

```json
{
  "role": "user",
  "content": "content string of this messages",
  "parts": [
    {
      "type": "blob",
      "blob": {
        "mime_type": "image/png",
        "url": "base64 encoded image data"
      }
    }
  ]
}
```

**带文件的消息**

```json
{
  "role": "role of this message, for example user, assistant",
  "content": "content string of this messages",
  "parts": [
    {
      "type": "file",
      "file": {
        "id": "uuid of this file",
        "name": "name of this file, with extension"
      }
    }
  ]
}
```

**多条消息**

```json
{
  "messages": [
    {
      "role": "",
      "content": "",
      "parts": []
    },
    {
      "role": "",
      "content": "",
      "parts": []
    }
  ]
}
```

**重要提示**
只有符合此格式的消息才会自动保存到线程，其他消息将被忽略。

## 用法

您可以在指令中使用 `{{INPUT.message}}` 变量或在代码编辑器中使用 `env.state.INPUT.messages` 变量来使用输入。

<figure><img src="../../../images/input-action.png"></figure>

## 数据格式

* 在代理页面中使用时，输入是从预定义的数据集中提取的。

* 连接到应用程序时，输入来自应用程序用户的输入和对话历史。默认情况下，我们会将最后 10 条消息发送到代理。

* 输入数据格式如下：

    ```json
    {
    "messages":[{
            "role": "user",
            "content": "The content."
        },
        {
            "role": "assistant",
            "content": "The content."
        }]
    }
    ```
