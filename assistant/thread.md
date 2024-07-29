# 线程

## 创建线程

`POST https://rebyte.ai/api/sdk/threads`

创建一个新线程。

**请求正文**
* messages：一个消息数组，用于启动线程。
* metadata：附加到对象的一组 16 个键值对。这对于以结构化格式存储有关对象的附加信息非常有用。键最长可为 64 个字符，值最长可为 512 个字符。

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

`GET https://rebyte.ai/api/sdk/threads`

获取线程列表。

**查询参数**
* limit：一个整数，返回的最大线程数。默认为 20。
* order：一个字符串，返回线程的顺序。默认为 desc。
* before：一个字符串，用作分页的游标。after 是一个对象 ID，定义您在列表中的位置。
* after：一个字符串，用作分页的游标。before 是一个对象 ID，定义您在列表中的位置。

**示例请求**
```shell
curl  'https://rebyte.ai/api/sdk/threads?limit=10&order=desc' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer $REBYTE_KEY' \
-H 'Cookie: NEXT_LOCALE=en'
```

**返回**

一个线程对象列表。

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

`GET https://rebyte.ai/api/sdk/threads/{thread_id}`

按 ID 获取线程。

**路径参数**
* thread_id（必需）：一个字符串，表示要检索的线程 ID。

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

`POST https://rebyte.ai/api/sdk/threads/{thread_id}`

更新一个线程。

**路径参数**
* thread_id（必需）：一个字符串，表示要检索的线程 ID。

**请求正文**
* metadata：附加到对象的一组 16 个键值对。这对于以结构化格式存储有关对象的附加信息非常有用。键最长可为 64 个字符，值最长可为 512 个字符。

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
