# 文件

## 上传文件

`POST https://rebyte.ai/api/sdk/files`

上传一个可以在各种端点之间使用的文件。

**请求正文**

* file（必需）：要上传的文件对象。

**示例请求**
```shell
curl 'https://rebyte.ai/api/sdk/files' \
  -H "Authorization: Bearer $REBYTE_KEY" \
  -F file="@mydata.jsonl"
```

**返回**

返回一个包含消息、fileId 和路径的对象。

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
        },
    ]
}
```

## 检索文件

`GET https://rebyte.ai/api/sdk/files/{fileId}`

按 fileId 检索文件。

**示例请求**
```shell
curl 'https://rebyte.ai/api/sdk/files/{fileId}' \
  -H "Authorization: Bearer $REBYTE_KEY" \
```
**返回**

返回一个文件对象。

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

按 fileId 检索文件内容。

**示例请求**
```shell
curl 'https://rebyte.ai/api/sdk/files/{fileId}/content' \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

**返回**

返回文件的内容。

**响应**
```json
文件的内容...
```

## 删除文件

`DELETE https://rebyte.ai/api/sdk/files/{fileId}`

按 fileId 删除文件。

**示例请求**
```shell
curl --location --request DELETE 'https://rebyte.ai/api/sdk/files/{file_id}' \
--H 'Authorization: Bearer $REBYTE_KEY'
```

**返回**

返回一个消息对象。

**响应**
```json
{
    "message": "deleted",
    "fileId": "09343664-ddb2-4d43-a4e5-02aa25d15b54"
}
```
