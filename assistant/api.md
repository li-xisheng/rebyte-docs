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

