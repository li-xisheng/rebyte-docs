## What is ReByte?

> ReByte is an AI assistant for every member of your team. 

ReByte has two primary goals:

* **Instant Use**: There are lots of fancy AI technologies every week, even every day, some of them focus on developers, some of them just try to demonstrate the power of AI, most of them are lack of end user usability. ReByte tries to provide an AI assistant that can be instantly used by every member of your team, with very minimal setup.
* **Customization** Enterprise use cases are very different, customization is a **MUST** for enterprise AI assistant, there's no one-size-fits-all AI assistant for all companies. ReByte integrates a low-code platform for building AI tools to capture your proprietary workflow, which workflow can be seamlessly integrated into your team assistant.

Besides, ReByte has the following features:

* **Handle both unstructured and structured data** Most of the AI assistants can only handle unstructured data by using vector search engine, ReByte can also handle structured data, including csv, Excel, postgres, mysql, parquet, JSON, sqlite. Combine our structured data support, you can build a RAG system with super high precision compared to traditional vector search engine.
* **Multistep Plan and Execute** ReByte uses a plan and execute model to interact with tools. It first creates a plan, run the plan step by step, and then execute the plan. It can also correct itself if the plan is not executed as expected.
* **Model Agnostic** You can use any large language model, such as OpenAI, Gemini, Anthropic, Mistral, or any other OS models, even your private model.
* **Enterprise Data Sync** ReByte can auto sync data from various sources, such as Notion, Slack, Discord, Twitter, Google, Microsoft and more, those data can be used to build your own knowledge base.
* **Team Collaboration**, You can definitely use rebyte for your personal uses. However, rebyte is designed for enterprise use, you can create a team, invite your colleagues to join the team, and collaborate on the same knowledge/table/tool/assistant, also enforce access control.


![img](http://res.cloudinary.com/dfjwtidnh/image/upload/v1720449540/rebyte/api_uploaded_assets/26c4a4ce-328d-4291-a2c7-88c89428e757.png)


## Typical Use Cases

We expect ReByte can be useful in the following use cases:

* **Data Exploration** Data owner can create a virtual database with proper access control, and share it with other team members, everyone can then run the query independently on the shared database. 

Think about you have multiple sales data across Google, excel, local file csv, database etc. You want to find out which might be the best sales channel for your company, **Rebyte Table** let you combine your data in super flexible ways, and do the exploration.

* **Company knowledge base** You have a lot of knowledge scattered across different sources, such as Notion, Slack, Discord, Twitter, Google, Microsoft, etc. You want to build a unified knowledge base for your team, **Rebyte Knowledge** let you sync data from those sources, and build your own knowledge base.

You can ask things like "What's the company policy for remote work?" or "How many PTOS do I have left?"

* **Automate repetitive tasks** You have a lot of repetitive tasks, such as data cleaning, data transformation, data analysis, data visualization, those workflow are proprietary to your team, you want to automate those tasks, **Rebyte Tool** let you build your own tools to automate those tasks, every team member can use those tools just like using a normal AI assistant.


[//]: # (<figure><img src=".gitbook/assets/image &#40;9&#41;.png" alt=""><figcaption></figcaption></figure>)

[//]: # (## Rationale behind ReByte)

[//]: # ()
[//]: # (There are already many AI assistants on the market, many of which are made by very good companies. However, we believe that the team AI assistant will be significantly different from these AI assistants in the following ways:)

[//]: # ()
[//]: # (Providing customized processes that can be seamlessly integrated into team's assistant. Each team has its own unique business processes.)

[//]: # ()
[//]: # (Each team's knowledge base is vastly different, and the AI assistant needs more context to better serve each team member.)

[//]: # ()
[//]: # (All problems can be boiled down to providing more context to AI assistants, including the context of data and the context of business logic.)

[//]: # ()
[//]: # (ReByte provides the following features to address these issues, one is a low-code platform for building tools to capture proprietary workflow, and the other is a data integration platform to aggregate data from various sources.)

[//]: # ()
[//]: # (### No-Code Platform for Building Tools)

[//]: # ()
[//]: # (ReByte provides a low-code platform for customized tool build, similar to Langchain, for extending the capabilities of team assistants. As mentioned in this [cognitive architecture blog post by langchain]&#40;https://blog.langchain.dev/openais-bet-on-a-cognitive-architecture/&#41;&#41;, large language model tools can be divided into two categories: those driven by the reasoning capabilities of large language models, such as Chain of Thoughts, and those driven by "flow engineering," where developers design LLM tools that align with the team's workflow. ReByte provides a complete set of tools to support the development of such customized tools, while minimizing the programming requirements for developers. Our goal is to enable developers to build large language model tools with just an understanding of JSON.)

[//]: # ()
[//]: # (### Enterprise Data Integration)

[//]: # ()
[//]: # (ReByte will help to create a unified team knowledge base by integrating data from authorized sources with the team's permission. This comprehensive and integrated knowledge base is crucial for later processing by large language models. Initially, ReByte will integrate data from sources such as files, GitHub, Notion, web pages, and Twitter, and this list will continue to expand in the future.)

[//]: # ()
[//]: # ([//]: # &#40;Data security is a constant concern within enterprises, and this is also true for team assistants. ReByte has designed a role-based access control system that aims to provide enterprise IT personnel with the utmost flexibility in controlling which data can be accessed by whom.&#41;)
[//]: # ()
[//]: # ()
[//]: # (## Two Views)

[//]: # ()
[//]: # (ReByte contains two main parts:)

[//]: # ()
[//]: # (* **End User's view**: An AI Assistant for your team members. You can think of it as a private ChatGPT with access to your team's private knowledge and workflow.)

[//]: # (* **Builder's view**: Builder in your team can capture your team's proprietary knowledge and workflow, and make them available to your team member.)

[//]: # ()
[//]: # ()
[//]: # ()
[//]: # ()
[//]: # ([//]: # &#40;&#41;)
[//]: # ([//]: # &#40;### Builder Platform&#41;)
[//]: # ()
[//]: # ([//]: # &#40;&#41;)
[//]: # ([//]: # &#40;Only builders or admin in your team can access the builder platform. Those are main components in the builder platform:&#41;)
[//]: # ()
[//]: # ([//]: # &#40;&#41;)
[//]: # ([//]: # &#40;* **Actions**: represent a single unit of work that tool can perform, such as make a LLM call, read a file, or generate a document, run piece of code, call external services etc. Actions can be chained together to form a sequence of actions that the tool will perform.&#41;)
[//]: # ()
[//]: # ([//]: # &#40;* **Tools**: a no-code UI for capturing proprietary workflow, it represents a sequence of actions.&#41;)
[//]: # ()
[//]: # ([//]: # &#40;* **Knowledge** : a data pipeline for aggregating data from various enterprise sources, embedding them, and making them available to tools.&#41;)
[//]: # ()
[//]: # ([//]: # &#40;* **API**: all mentioned above can be accessed via API, so you can integrate ReByte with your existing systems.&#41;)
