## What is ReByte?

Rebyte is an AI assistant that helps to boot your team's productivity.

Compare to other AI assistants on market, Rebyte has the following focus:

* **Unified Interface** A super assistant called **Revia**, it's an out of box AI assistant for most general use cases, such as base LLM, search engine integration, image understanding, RAG integration, process common file types, advance data analysis. **Revia** is available on all platforms, including web, mobile, and desktop.
* **Extensible** You can customize your own tool or assistant to fit your proprietary workflow, and seamlessly integrate them into **Revia**. For example, you can build a customer support assistant on your customer support data, **Revia** can magically help you to answer customer questions, or even solve customer problems.
* **Multistep Plan and Execute** Rebyte uses a plan and execute model to interact with tools. It first creates a plan, run the plan step by step, and then execute the plan. It can also correct itself if the plan is not executed as expected.
* **Model Agnostic** You can use any large language model, such as OpenAI, Gemini, Anthropic, Mistral, or any other OS models, even your private model.
* **Automatic Data Sync** Rebyte can auto sync data from various sources, such as Notion, Slack, Discord, Twitter, Google, Microsoft and more, those data can be used to build your own knowledge base.
* **Handle both unstructured and structured data** Most of the AI assistants can only handle unstructured data by using vector search engine, Rebyte can also handle structured data, including csv, excel, postgres, mysql, parquet, json, sqlite.
* **Team Collaboration**, You can definitely use rebyte for your personal uses, but rebyte is designed for enterprise use, you can create a team, invite your colleagues to join the team, and collaborate on the same knowledge/agent/assistant, also enforce access control.


![img](http://res.cloudinary.com/dfjwtidnh/image/upload/v1720449540/rebyte/api_uploaded_assets/26c4a4ce-328d-4291-a2c7-88c89428e757.png)



[//]: # (<figure><img src=".gitbook/assets/image &#40;9&#41;.png" alt=""><figcaption></figcaption></figure>)

## Rationale behind ReByte

There are already many AI assistants on the market, many of which are made by very good companies. However, we believe that the team AI assistant will be significantly different from these AI assistants in the following ways:

Providing customized processes that can be seamlessly integrated into team's assistant. Each team has its own unique business processes.

Each team's knowledge base is vastly different, and the AI assistant needs more context to better serve each team member.

All problems can be boiled down to providing more context to AI assistants, including the context of data and the context of business logic.

Rebyte provides the following features to address these issues, one is a low-code platform for building tools to capture proprietary workflow, and the other is a data integration platform to aggregate data from various sources.

### No-Code Platform for Building Tools

Rebyte provides a low-code platform, similar to Langchain, for extending the capabilities of team assistants. As mentioned this [cognitive architecture blog post by langchain](https://blog.langchain.dev/openais-bet-on-a-cognitive-architecture/)), large language model tools can be divided into two categories: those driven by the reasoning capabilities of large language models, such as Chain of Thoughts, and those driven by "flow engineering," where developers design LLM tools that align with the team's workflow. Rebyte provides a complete set of tools to support the development of such customized tools, while minimizing the programming requirements for developers. Our goal is to enable developers to build large language model tools with just an understanding of JSON.

### Enterprise Data Integration

Rebyte will help to create a unified team knowledge base by integrating data from authorized sources with the team's permission. This comprehensive and integrated knowledge base is crucial for subsequent processing by large language models. Initially, Rebyte will integrate data from sources such as files, GitHub, Notion, web pages, and Twitter, and this list will continue to expand in the future.

[//]: # (Data security is a constant concern within enterprises, and this is also true for team assistants. Rebyte has designed a role-based access control system that aims to provide enterprise IT personnel with the utmost flexibility in controlling which data can be accessed by whom.)


## Two Views

Rebyte contains two main components::

* **End User's view**: An AI Assistant for your team members. You can think of it as a private Chatgpt with access to your team's private knowledge and workflow.
* **Builder's view**: Builder in your team can capture your team's proprietary knowledge and workflow, and make them available to **Revia**.




[//]: # ()
[//]: # (### Builder Platform)

[//]: # ()
[//]: # (Only builders or admin in your team can access the builder platform. Those are main components in the builder platform:)

[//]: # ()
[//]: # (* **Actions**: represent a single unit of work that tool can perform, such as make a LLM call, read a file, or generate a document, run piece of code, call external services etc. Actions can be chained together to form a sequence of actions that the tool will perform.)

[//]: # (* **Tools**: a no-code UI for capturing proprietary workflow, it represents a sequence of actions.)

[//]: # (* **Knowledge** : a data pipeline for aggregating data from various enterprise sources, embedding them, and making them available to tools.)

[//]: # (* **API**: all mentioned above can be accessed via API, so you can integrate Rebyte with your existing systems.)
