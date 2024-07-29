ReByte 提供了一组 API，使得将 ReByte 集成到您自己的应用程序中变得容易。
主要有三个 API：文件 API、工具 API 和线程 API。

* 工具 API

工具 API 允许您调用在 ReByte 上创建的工具。它支持：

    * 阻塞和非阻塞调用
    * 流式处理
    * 指定工具版本
    * 指定工具内动作的配置


* 线程 API

线程 API 允许您创建一个对话线程并向线程添加消息。

结合工具 API，您可以创建一个具有记忆功能的工具，而无需拥有自己的后端。

* 文件 API 

允许您将文件上传到 ReByte。上传的文件可以在代理的动作中使用，例如 `File Loader` 动作。

---

# 工具 API

工具 API 允许您从自己的应用程序调用自定义工具。它提供了一组与工具交互的 API，例如发送消息、上传文件和创建线程。

## 概述

工具 API 的典型集成流程如下：

1. 在 ReByte 工具编辑器中创建一个工具，定义其自定义动作，例如 `Model`、`Data`、`Utilities`、`Control Flow` 等。选择您要使用的模型和参数。

2. 在用户开始对话时创建一个线程。

3. 在用户提问时向线程添加消息。

4. 在线程上运行工具以生成响应。

## 步骤详解

1. 创建一个工具。

在这里，我们将使用此 ["Chat with GPT3.5 工具"](https://rebyte.ai/p/21b2295005587a5375d8/callable/f4222f209267e5b24cda/editor) 作为示例。请务必先测试您的工具并确保其按预期工作。另外，点击“Deploy”使其可用于 API。

2. 创建一个线程

在使用 API 之前，从侧栏的 API 控制台获取您的 API 密钥。您应该使用此密钥来验证您的请求。

创建线程时，您可以在创建时将消息附加到线程中。
您还可以将元数据附加到线程中。这对于以结构化格式存储有关对象的附加信息非常有用。

```shell
curl 'https://rebyte.ai/api/sdk/threads' \
--H 'Content-Type: application/json' \
--H 'Authorization: Bearer $REBYTE_KEY' \
--H 'Cookie: NEXT_LOCALE=en' \
--d '{
     "metadata": {
        "user": "abc123"
      },
    "messages":[
        {
            "role":"user",
            "content":"Hi, how are you?"
        },
        {
            "role":"assistant",
            "content":"Hi, I am good. What about you? Is there anything I can help?"
        }
    ]
}'
```

在响应中，您将找到线程 ID。您可以使用此线程 ID 向线程添加消息并在线程上运行工具。

* 示例响应

```shell
{
    "id": "UHSHhnkWGElWShQS5ZtOa",
    "created_at": 1714050659
}
```

3. 向线程添加消息

```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages' \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $REBYTE_KEY" \
  -d '{
      "role": "user",
      "content": "How does AI work? Explain it in simple terms."
    }'
```

在响应中，您可以看到消息信息。

* 示例响应

```shell
{
    "id": "u8YmkrO4lYZD8r8Nl5cFh",
    "created_at": 1714051597,
    "thread_id": "UHSHhnkWGElWShQS5ZtOa",
    "role": "user",
    "content": "Teach me how to make pancake."
}
```

4. 在线程上运行工具

要在线程上运行工具，您应该从部署您的工具中获取 URL 并向该 URL 发出请求。

```shell
curl -L https://rebyte.ai/api/sdk/p/21b2295005587a5375d8/a/f4222f209267e5b24cda/r \
    -H "Authorization: Bearer $REBYTE_KEY" \
    -H "Content-Type: application/json" \
    -d '{
    "version": 1,\
    "config": {
        "MODEL_CALL": {
            "provider_id": "openai",
            "model_id": "gpt-3.5-turbo-1106",
            "use_cache": true,
            "use_stream": false,
            "seed": null,
            "response_format": null
        }
    },
    "thread_id":"UHSHhnkWGElWShQS5ZtOa",
    "blocking": true,\
    "inputs": []
    }'
```

* 调用工具时，您应指定线程 ID，这样您就可以获取线程中的所有消息和元数据。

* 您还可以使用 "contentOnly:true" 仅获取消息的内容。

5. 从线程获取消息

```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages'     \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

在响应中，您将获得线程上所有消息的列表。

* 示例响应

```shell
{
    "list": [
        {
            "id": "u8YmkrO4lYZD8r8Nl5cFh",
            "created_at": 1714051597,
            "thread_id": "UHSHhnkWGElWShQS5ZtOa",
            "role": "user",
            "content": "Teach me how to make pancake."
        },
        {
            "id": "pJWH0zkmgnQONAHr6bnA4",
            "created_at": 1714050770,
            "thread_id": "UHSHhnkWGElWShQS5ZtOa",
            "role": "assistant",
            "content": "Bitcoin is a decentralized digital currency, often referred to as a cryptocurrency. It was created in 2009 by an unknown person using the pseudonym Satoshi Nakamoto. Bitcoin transactions are recorded on a public ledger called a blockchain, and it operates without the need for a central authority or government. Bitcoin can be used for online transactions, as an investment, or as a store of value. It is also known for its potential to provide financial privacy and security.",
            "agent_id": "297c5b234e770dd73713",
            "name": "chat_with_gpt3_5",
            "run_id": "4ed010c66458a2ac738932d950830218a2224e7ba22e12718ad66872be6832e7"
        },
        {
            "id": "iEw3QFJys-zpacEbNgsF1",
            "created_at": 1714050764,
            "thread_id": "UHSHhnkWGElWShQS5ZtOa",
            "role": "user",
            "content": "What is bitcoin?"
        },
        {
            "id": "xNQZdrCSJkYhM13b25Mhp",
            "created_at": 1714050764,
            "thread_id": "UHSHhnkWGElWShQS5ZtOa",
            "role": "assistant",
            "content": "Hi, how are you?"
        },
        {
            "id": "tfSLCfLflDquhQ7680j8z",
            "created_at": 1714050764,
            "thread_id": "UHSHhnkWGElWShQS5ZtOa",
            "role": "user",
            "content": "Hello!"
        }
    ]
}
```

### 阻塞和非阻塞调用

在请求体中添加 'blocking' 参数以指定调用是阻塞还是非阻塞。如果 'blocking' 设置为 true，则调用将等待工具的响应。如果 'blocking' 设置为 false，则调用将立即返回一个 run_id，稍后可以使用该 run_id 检查调用状态。

### 流式处理

在请求体中添加 'stream' 参数以指定调用是否为流式处理。如果 'stream' 设置为 true，则调用将返回工具生成的消息流。如果 'stream' 设置为 false，则调用将返回工具的最终响应。

---

# 线程 API

## 创建线程

`POST https://rebyte.ai/api/sdk/threads`

创建一个新线程。

**请求体**
* messages：用于启动线程的消息数组。
* metadata：可以附加到对象上的 16 对键值对。对于以结构化格式存储有关对象的附加信息非常有用。键的最大长度为 64 个字符，值的最大长度为 512 个字符。

**示例请求**

```shell
curl 'https://rebyte.ai/api/sdk/threads' \
--H 'Content-Type: application/json' \
--H 'Authorization: Bearer $REBYTE_KEY' \
--H 'Cookie: NEXT_LOCALE=en' \
--data '{
     "metadata": {
        "user": "abc123"
      }
}'
```

**返回**

一个线程对象。

**示例**

```json
{
    "id": "2hWVPNfrHv1IiVN7ia-4P",
    "created_at": 1710481773,
    "metadata": {
        "user": "abc123"
    }
}
```

### 列出线程

`GET https://rebyte.ai/api/sdk/threads`

获取线程列表。

**查询参数**
* limit：一个整数，返回的最大线程数。默认值为 20。
* order：一个字符串，返回线程的顺序。默认值为 desc。
* before：一个字符串，用作分页中的游标。before 是定义您在列表中位置的对象 ID。
* after：一个字符串，用作分页中的游标。after 是定义您在列表中位置的对象 ID。

**示例请求**

```shell
curl  'https://rebyte.ai/api/sdk/threads?limit=10&order=desc' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer $REBYTE_KEY' \
-H 'Cookie: NEXT_LOCALE=en'
```

**返回**

一个线程对象的列表。

**示例**

```json
{
    "list": [
        {
            "id": "2hWVPNfrHv1IiVN7ia-4P",
            "created_at": 1710481773,
            "metadata": {
                "user": "abc123"
            }
        },
        {
            "id": "NGXTNrg-34seXYc-PCVFu",
            "created_at": 1710415453,
            "metadata": {
                "user": "abc123"
            }
        },
        {
            "id": "MRlX-SOAo5gAx1mxBe7S4",
            "created_at": 1710407916
        }
    ]
}
```

### 获取线程

`GET https://rebyte.ai/api/sdk/threads/{thread_id}`

通过 ID 获取线程。

**路径参数**
* thread_id（必填）：一个字符串，要检索的线程的 ID。

**示例请求**

```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer $REBYTE_KEY' \
-H 'Cookie: NEXT_LOCALE=en'
```

**返回**
与指定 ID 匹配的线程对象。

**示例**

```json
{
    "id": "cB1-_3wh5ZWtUPJU4xIuU",
    "created_at": 1710415223,
    "metadata": {
        "user": "czy",
        "modified": "true"
    }
}
```

### 更新线程

`POST https://rebyte.ai/api/sdk/threads/{thread_id}`

更新线程。

**路径参数**
* thread_id（必填）：一个字符串，要检索的线程的 ID。

**请求体**
* metadata：可以附加到对象上的 16 对键值对。对于以结构化格式存储有关对象的附加信息非常有用。键的最大长度为 64 个字符，值的最大长度为 512 个字符。

**示例请求**

```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer $REBYTE_KEY' \
-H 'Cookie: NEXT_LOCALE=en' \
--data ' {
    "metadata": 
    {
        "modified": "true",
        "user": "czy"
    }
 }'
```

**返回**
与指定 ID 匹配的修改后的线程对象。

**示例**

```json
{
    "id": "cB1-_3wh5ZWtUPJU4xIuU",
    "created_at": 1710415223,
    "metadata": {
        "modified": "true",
        "user": "czy"
    }
}
```
---

# 文件 API

## 上传文件

`POST https://rebyte.ai/api/sdk/files`

上传可在各种端点中使用的文件。

**请求体**

* file（必填）：要上传的文件对象。

**示例请求**

```shell
curl 'https://rebyte.ai/api/sdk/files' \
  -H "Authorization: Bearer $REBYTE_KEY" \
  -F file="@mydata.jsonl"
```

**返回**

返回包含消息、fileId 和路径的对象。

**响应**

```json
{
    "message": "upload file success",
    "fileId": "09343664-****-****-a4e5-02aa25d15b54",
    "path": "1b242a2dea62c6******/09343664-****-4d43-a4e5-02aa25d15b54"
}
```

## 列出文件

`GET https://rebyte.ai/api/sdk/files`

获取文件列表。

**示例请求**

```shell
curl 'https://rebyte.ai/api/sdk/files' \
  -H "Authorization: Bearer $REBYTE_KEY"
```

**返回**

返回文件列表。

**响应**

```json
{
    "files": [
        {
            "uuid": "d723538c-d188-4c24-80f6-71b27b43a76e",
            "name": "api_data.json",
            "mimeType": "application/json",
            "size": 18119,
            "projectId": 160,
            "createdAt": "2024-03-14T11:26:15.240Z"
        },
        {
            "uuid": "2b3dc1e9-634d-4bd5-b9d7-94a9b4a0662c",
            "name": "每日推特.txt",
            "mimeType": "text/plain",
            "size": 1589,
            "projectId": 160,
            "createdAt": "2023-12-28T07:17:24.733Z"
        }
    ]
}
```

## 检索文件

`GET https://rebyte.ai/api/sdk/files/{fileId}`

通过 fileId 检索文件。

**示例请求**

```shell
curl 'https://rebyte.ai/api/sdk/files/{fileId}' \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

**返回**

返回文件对象。

**响应**

```json
{
    "file": {
        "name": "api_data.json",
        "uuid": "ac1722a6-76cb-45d3-bcfe-7117939e0f52",
        "projectId": 160,
        "createdAt": "2024-03-14T11:15:56.257Z",
        "mimeType": "application/json",
        "size": 18119
    }
}
```

## 检索文件内容

`GET https://rebyte.ai/api/sdk/files/{fileId}/content`

通过 fileId 检索文件内容。

**示例请求**

```shell
curl 'https://rebyte.ai/api/sdk/files/{fileId}/content' \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

**返回**

返回文件内容。

**响应**

```json
文件内容...
```

## 删除文件

`DELETE https://rebyte.ai/api/sdk/files/{fileId}`

通过 fileId 删除文件。

**示例请求**

```shell
curl --location --request DELETE 'https://rebyte.ai/api/sdk/files/{file_id}' \
--H 'Authorization: Bearer $REBYTE_KEY'
```

**返回**

返回消息对象。

**响应**

```json
{
    "message": "deleted",
    "fileId": "09343664-ddb2-4d43-a4e5-02aa25d15b54"
}
```
