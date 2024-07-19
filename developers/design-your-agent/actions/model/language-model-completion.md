# Language Model Completion

We provide `Language Model Completion` action to let the language model complete your prompt.

## Usage

* Add a `Language Model Completion` action to your agent.
* Configure the action with specifications and parameters.

### Specification

<figure><img src="../../../../images/completion.png" alt=""><figcaption></figcaption></figure>

**Prompt**

* This is the prompt that will be sent to the model.
* The model will complete your prompt and respond with the completed content.

### Configuration

The configuration is the same as [Language Model Chat](language-model-chat.md).

You can choose the model you want to use by clicking the model's name, the default model is "gpt-3.5-turbo-1106".

<figure><img src="../../../../images/chat-models.png" alt=""><figcaption></figcaption></figure>

&#x20;

Click this button in the bottom right corner of the `Language Model Completion` action to open the configuration panel.

<figure><img src="../../../../images/chat-config-button.jpg" alt=""><figcaption></figcaption></figure>

&#x20;

There are five settings in the configuration panel, as shown below.

<figure><img src="../../../../images/chat-config-2.png" alt=""><figcaption></figcaption></figure>

**Temperature**

* "Temperature" controls the randomness of the model's output.
* The higher the model temperature, the more random the output is.

**Maximum Output Tokens**

* "Maximum Output tokens" specifies the maximum number of tokens to generate.
* Can use up to 40,000 tokens(the limit for models vary), including prompt and model returned content.

**JSON Response**

* "JSON Response" button enable JSON mode, which guarantees the messages the model generate are in JSON format.
* NOTE: This feature is a beta feature and only supported by OpenAI's "gpt-4-1106-preview" model now.
* NOTE: When you use this feature, make sure the word "JSON" is in the context. Otherwise, the OpenAI's API will throw an error.

**Seed**

* The "Seeds" is a parameter that can be specified when using the `Language Model Completion` and `Language Model Completion` actions.
* It helps to ensure consistent outputs by making the system sample deterministically, resulting in the same result for repeated requests with the same seed and parameters.
* NOTE: This feature is a beta feature and only supported by OpenAI's model.

**Stop Words**

* Stop words are used to make the model stop at a desired point, such as the end of a sentence or a list.

On the top right of the action, there are two more things to configure: "Stream Mode" and "Cache Mode".

<figure><img src="../../../../images/stream-and-cache.jpg" alt=""><figcaption></figcaption></figure>

**Stream**

* This option allows you to receive partial chat responses as they are being generated, rather than waiting for the entire completion to be finished before receiving a response.
* By setting stream mode, you can start processing or displaying the beginning of the chat before the full response is received.

**Cache**

* Caching involves storing frequently accessed data to improve response times without making repeated calls to a model.
* If you use the cache mode, the model will cache the response and return the cached response when the same request is made again. This will make your agent run faster.

### Message Format

ReByte uses a similar message format as OpenAI. The message format is a JSON object with the following fields:

* Role: could be one from 'user', 'system', or 'assistant'.
* Content: content of this message.
* Name(optional): name of role.
* Context(optional): context of this message.

&#x20;

**Message Format Examples**

1.Prompt Example

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

## Example Tool

* [Language Model Completion](https://rebyte.ai/p/21b2295005587a5375d8/callable/719d2f31bf9fe977f699/editor)
