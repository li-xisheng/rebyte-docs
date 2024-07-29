# 消息

## 插入消息

`POST https://rebyte.ai/api/sdk/threads/{threadId}/messages`

在线程中创建一条新消息。

**路径参数**
* thread_id（必需）：一个字符串，表示要为其创建消息的线程 ID。

**请求正文**
* role（必需）：一个字符串，包含创建消息的实体的角色。目前仅支持用户。
* content（必需）：一个包含消息内容的字符串。
* file_ids：消息应使用的文件 ID 列表。每条消息最多可以附加 10 个文件。对于检索和代码解释器等工具非常有用，可以访问和使用文件。
* metadata：附加到对象的一组 16 个键值对。这对于以结构化格式存储有关对象的附加信息非常有用。键最长可为 64 个字符，值最长可为 512 个字符。

**示例请求**
```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages' \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $REBYTE_KEY" \
  -d '{
      "role": "user",
      "content": "How does AI work? Explain it in simple terms."
    }'
```

**返回**

一个消息对象。

**示例**
```json
{
    "id": "W_DPv1bwUQ50PC52f44Uo",
    "created_at": 1710415825,
    "thread_id": "p_DFiNmczwUWZjcl47U9X",
    "role": "user",
    "content": "How does AI work? Explain it in simple terms.",
    "metadata": {
        "user": "czy1"
    }
}
```

## 列出消息

`GET https://rebyte.ai/api/sdk/threads/{threadId}/messages`

获取线程中的消息列表。

**路径参数**
* thread_id（必需）：一个字符串，表示要为其创建消息的线程 ID。

**查询参数**

* limit：一个整数，默认为 20。要返回的对象数量限制。限制范围为 1 到 100，默认值为 20。

* order：一个字符串，默认为 desc。按对象的 created_at 时间戳排序。asc 表示升序，desc 表示降序。

* after：一个字符串，用于分页的游标。after 是一个对象 ID，定义您在列表中的位置。例如，如果您进行列表请求并接收到 100 个对象，以 obj_foo 结束，您可以在后续调用中包含 after=obj_foo 以获取列表的下一页。

* before：一个字符串，用于分页的游标。before 是一个对象 ID，定义您在列表中的位置。例如，如果您进行列表请求并接收到 100 个对象，以 obj_foo 结束，您可以在后续调用中包含 before=obj_foo 以获取列表的上一页。

**示例请求**
```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages'     \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

**返回**

返回消息列表。

**示例**
```json
{
    "list": [
        {
            "id": "W_DPv1bwUQ50PC52f44Uo",
            "created_at": 1710415825,
            "thread_id": "p_DFiNmczwUWZjcl47U9X",
            "role": "user",
            "content": "How does AI work? Explain it in simple terms.",
            "metadata": {
                "user": "czy4"
            }
        }
    ]
}
```

## 获取消息

`GET https://rebyte.ai/api/sdk/threads/{threadId}/messages/{messageId}`

按 ID 获取消息。

**路径参数**

* thread_id（必需）：一个字符串，表示此消息所属的线程 ID。

* message_id（必需）：一个字符串，表示要检索的消息的 ID。

**示例请求**
```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages/{message_id}' \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $REBYTE_KEY" 
```

**返回**

返回一个消息对象。

**示例**
```json
{
    "id": "W_DPv1bwUQ50PC52f44Uo",
    "created_at": 1710415825,
    "thread_id": "p_DFiNmczwUWZjcl47U9X",
    "role": "user",
    "content": "How does AI work? Explain it in simple terms.",
    "metadata": {
        "user": "czy4"
    }
}
```

## 更新消息 

`POST https://rebyte.ai/api/sdk/threads/{threadId}/messages/{messageId}`

按 ID 更新消息。

**路径参数**

* thread_id（必需）：一个字符串，表示此消息所属的线程 ID。

* message_id（必需）：一个字符串，表示要检索的消息的 ID。

**请求正文**

* metadata：一个映射。附加到对象的一组 16 个键值对。这对于以结构化格式存储有关对象的附加信息非常有用。键最长可为 64 个字符，值最长可为 512 个字符。

**示例请求**
```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages/{message_id}' \
  -H 'Content-Type: application/json' \
  -H "Authorization: Bearer REBYTE_KEY" \
  -d '{
     "role": "user",
      "content": "Updated on 14th March,2024. Happy valentine'\''s day!",
      "metadata":{
        "user":"czy4"
      }
}'
```

**返回**

返回修改后的消息对象。

**示例**
```json
{
    "id": "W_DPv1bwUQ50PC52f44Uo",
    "created_at": 1710415825,
    "thread_id": "p_DFiNmczwUWZjcl47U9X",
    "role": "user",
    "content": "How does AI work? Explain it in simple terms.",
    "metadata": {
        "user": "czy4"
    }
}
```
