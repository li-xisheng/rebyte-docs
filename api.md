ReByte provides a set of APIs to make it easy to integrate ReByte into your own applications.
There are three main APIs: File API, Tool API, and Thread API. 

* Tool API

Tool API allows you to call the tool you created on ReByte. It supports:

    * blocking and non-blocking calls
    * streaming
    * specifying a tool version
    * specify config of action within the tool 


* Thread API

Thread API allows you to create a conversation thread and add messages to the thread.

Combined with the Tool API, you can create a tool with memory without having your own backend.

* File API 
 
Allows you to upload files to ReByte. Uploaded files can be used in the agent's actions, such as `File Loader` action.


---

# Tool API

The Tool API allows you to call customized tools from your own applications. It provides a set of APIs to interact with the tool, such as sending messages, uploading files, and creating threads.

## Overview

A typical integration of the Tool API has the following flow:

1. Create a Tool on rebyte tool editor by defining its custom actions, such as `Model`, `Data`, `Utilities`, `Control Flow`, etc. Pick the model and parameters that you want to use.

2. Create a Thread when a user starts a conversation.

3. Add Messages to the Thread as the user asks questions.

4. Run the Tool on the Thread to generate a response.

## Step by step

1. Create a Tool.

Here, we'll just use this ["Chat with GPT3.5 tool"](https://rebyte.ai/p/21b2295005587a5375d8/callable/f4222f209267e5b24cda/editor) as an example. Remember to test your tool first and make sure it works as expected. Also, click "Deploy" to make it available for the API.

2. Create a thread

Before using the API, get your API key from the API console on the sidebar. You should use this key to authenticate your requests.


When creating a thread, you can append the messages to the thread when creating it.
You can also attach metadata to the thread. This can be useful for storing additional information about the object in a structured format.


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
            "role":"asistant",
            "content":"Hi, I am good. What about you? Is there anything I can help?"
        }
    ]
}'
```

In the response, you will find the thread id. You can use this thread id to add messages to the thread and run the tool on the thread.

* Example Response

```shell
{
    "id": "UHSHhnkWGElWShQS5ZtOa",
    "created_at": 1714050659
}
```

3. Add messages to the thread

```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages' \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $REBYTE_KEY" \
  -d '{
      "role": "user",
      "content": "How does AI work? Explain it in simple terms."
    }'
```

In the response, you can see the message information.

* Example Response

```shell
{
    "id": "u8YmkrO4lYZD8r8Nl5cFh",
    "created_at": 1714051597,
    "thread_id": "UHSHhnkWGElWShQS5ZtOa",
    "role": "user",
    "content": "Teach me how to make pancake."
}
```

4. Run the tool on the thread

In order to run the tool on the thread, you should get the url from deploying your tool and make a request to this url.

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

* When calling the tool, you should specify the thread id, and you will be able to get all the messages and metadata from the thread.

* You can also use "contentOnly:true" to get only the content of the messages.


5. Get the messages from the thread

```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}/messages'     \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $REBYTE_KEY" \
```

In the response, you will get the list of all messages on the thread.

* Example Response

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

### Blocking and Non-blocking calls
Add 'blocking' parameter to the request body to specify whether the call should be blocking or non-blocking. If 'blocking' is set to true, the call will wait for the response from the tool. If 'blocking' is set to false, the call will return immediately with a run_id, which can be used to check the status of the call later.

### Streaming
Add 'stream' parameter to the request body to specify whether the call should be streaming or not. If 'stream' is set to true, the call will return a stream of messages from the tool as they are generated. If 'stream' is set to false, the call will return the final response from the tool.


---

# Thread API

## Create thread

`POST https://rebyte.ai/api/sdk/threads`

Create a new thread.

**Request body**
* messages: An array of messages to start the thread with.
* metadata: Set of 16 key-value pairs that can be attached to an object. This can be useful for storing additional information about the object in a structured format. Keys can be a maximum of 64 characters long and values can be a maxium of 512 characters long.

**Example Request**

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

**Return**

A thread object.

**Example**
```json
{
    "id": "2hWVPNfrHv1IiVN7ia-4P",
    "created_at": 1710481773,
    "metadata": {
        "user": "abc123"
    }
}
```


### List threads

`GET https://rebyte.ai/api/sdk/threads`

Get list of threads.

**Query parameters**
* limit: An integer, with the maximum number of threads to return. Default is 20.
* order: A string, with the order to return the threads. Default is desc.
* before: A string, used as a cursor for use in pagination. after is an object ID that defines your place in the list.
* after: A string, used as a cursor for use in pagination. before is an object ID that defines your place in the list.



**Example Request**
```shell
curl  'https://rebyte.ai/api/sdk/threads?limit=10&order=desc' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer $REBYTE_KEY' \
-H 'Cookie: NEXT_LOCALE=en'
```

**Return**

A list of thread objects.


**Example**
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
### **Get thread**

`GET https://rebyte.ai/api/sdk/threads/{thread_id}`

Get a thread by id.

**Path parameters**
* thread_id(required): A string, with the ID of the thread to retrieve.

**Example Request**
```shell
curl 'https://rebyte.ai/api/sdk/threads/{thread_id}' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer $REBYTE_KEY' \
-H 'Cookie: NEXT_LOCALE=en'
```

**Returns**
The thread object matching the specified ID.

**Example**
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

### **Update thread**

`POST https://rebyte.ai/api/sdk/threads/{thread_id}`

Update a thread.

**Path parameters**
* thread_id(required): A string, with the ID of the thread to retrieve.

**Request body**
* metadata: Set of 16 key-value pairs that can be attached to an object. This can be useful for storing additional information about the object in a structured format. Keys can be a maximum of 64 characters long and values can be a maxium of 512 characters long.

**Example Request**
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

**Returns**
The modified thread object matching the specified ID.

**Example**
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

# File API

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
