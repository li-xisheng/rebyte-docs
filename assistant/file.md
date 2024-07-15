# Files

## Upload file

`POST https://rebyte.ai/api/sdk/files`

Upload a file that can be used across various endpoints.

**Request Body**

* file(required): File object to be uploaded.

**Example Request**
```shell
curl 'https://rebyte.ai/api/sdk/files' \
  -H "Authorization: Bearer $REBYTE_KEY" \
  -F file="@mydata.jsonl"
```

**Return**

Returns an object with message, fileId and path.

**Response**
```json
{
    "message": "upload file success",
    "fileId": "09343664-****-****-a4e5-02aa25d15b54",
    "path": "1b242a2dea62c6******/09343664-****-4d43-a4e5-02aa25d15b54"
}
```

## List files 

`GET https://rebyte.ai/api/sdk/files`

Get list of files.

**Example Request**
```shell
curl 'https://rebyte.ai/api/sdk/files' \
  -H "Authorization: Bearer $REBYTE_KEY"
```

**Return**

Returns a list of files.

**Response**
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

## Retrieve file

`GET https://rebyte.ai/api/sdk/files/{fileId}`

Retrieve file by fileId.

**Example Request**
```shell
curl 'https://rebyte.ai/api/sdk/files/{fileId}' \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

**Return**

Returns a file object.

**Response**
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

## Retrieve file content

`GET https://rebyte.ai/api/sdk/files/{fileId}/content`

Retrieve file content by fileId.

**Example Request**
```shell
curl 'https://rebyte.ai/api/sdk/files/{fileId}/content' \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

**Return**

Returns the content of the file.

**Response**
```json
content of the file...
```

## Delete file

`DELETE https://rebyte.ai/api/sdk/files/{fileId}`

Delete file by fileId.

**Example Request**
```shell
curl --location --request DELETE 'https://rebyte.ai/api/sdk/files/{file_id}' \
--H 'Authorization: Bearer $REBYTE_KEY'
```

**Return**

Returns a message object.

**Response**
```json
{
    "message": "deleted",
    "fileId": "09343664-ddb2-4d43-a4e5-02aa25d15b54"
}
```
