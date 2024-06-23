# Welcome to Rebyte

## What is ReByte?

Rebyte is an AI assistant that helps to boot your team's productivity.

Compare to other AI assistants on market, Rebyte has the following focus:
* A super assistant called **Revia**, it's an out of box AI assistant for most general use cases, such as base LLM, search engine integration, image understanding, RAG integration, process common file types, advance data analysis.
* You can customize your own tool or assistant to fit your proprietary workflow, and seamlessly integrate them into **Revia**.
* Model agnostic, you can use any large language model, such as OpenAI, Gemini, Anthropic, Mistral, or any other OS models, even your private model.
* Data auto sync, Rebyte can auto sync data from various sources, such as Notion, Slack, Discord, Twitter, Google, Microsoft and more, those data can be used to build your own knowledge base.
* You can definitely use rebyte for your personal uses, but rebyte is designed for enterprise use, you can create a team, invite your colleagues to join the team, and collaborate on the same knowledge/agent/assistant, also enforce access control.


[//]: # (|                          | Rebyte        | ChatGpt For Team                                           |)

[//]: # (|--------------------------|---------------|------------------------------------------------------------|)

[//]: # (| Super Assistant          | Revia         | ChatGpt                                                    |)

[//]: # (| other assistants         | Assistants    | Gpts                                                       |)

[//]: # (| LLM                      | OpenAI/Gemini/Anthropic/Mistral/Other OS Models | Only OpenAI                                                |)

[//]: # (| Tools Used by Assistants | Any complex workflow, workflow will be run by Rebyte Workflow Runtime | By selecting Code interpreter/Browser/RAG/external API etc |)

[//]: # (| Data Integration         | Notion/Slack/Discord/Twitter... auto sync handled automatically | No Data Integration                                        |)

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## Rationale behind ReByte

There are already many AI assistants on the market, many of which are made by very good companies. However, we believe that the team AI assistant will be significantly different from these AI assistants in the following ways:

Providing customized processes that can be seamlessly integrated into team's assistant. Each team has its own unique business processes.

Each team's knowledge base is vastly different, and the AI assistant needs more context to better serve each team member.

All problems can be boiled down to providing more context to AI assistants, including the context of data and the context of business logic.

In order to address these challenges, we have designed a platform called Rebyte, which focuses on the following key areas:

### Universal User Interface

We provide a universal user interface called **Revia** that can be used by all team members to interact with the AI assistant. This interface is designed to handle various types of tasks, such as data retrieval, question and answer, document generation, and data analysis, and more advanced tasks such as interactive chart and table, form filling and more.

**Revia** will be available on all platforms, including web, mobile, and desktop.

### Flow Engineering

Rebyte provides a low-code platform, similar to Langchain, for extending the capabilities of team assistants. As mentioned this [cognitive architecture blog post by langchain](https://blog.langchain.dev/openais-bet-on-a-cognitive-architecture/)), large language model tools can be divided into two categories: those driven by the reasoning capabilities of large language models, such as Chain of Thoughts, and those driven by "flow engineering," where developers design LLM tools that align with the team's workflow. Rebyte provides a complete set of tools to support the development of such customized tools, while minimizing the programming requirements for developers. Our goal is to enable developers to build large language model tools with just an understanding of JSON.

### Plan and Execute

ReByte Assistant uses a plan and execute model to interact with tools. It first creates a plan, run the plan step by step, and then execute the plan. For data analysis tasks, assistant can write python code itself, and then execute the code. Assistant is also self reflective and can correct itself if the plan is not executed as expected.

### Enterprise Data Integration

Rebyte will help to create a unified team knowledge base by integrating data from authorized sources with the team's permission. This comprehensive and integrated knowledge base is crucial for subsequent processing by large language models. Initially, Rebyte will integrate data from sources such as files, GitHub, Notion, web pages, and Twitter, and this list will continue to expand in the future.

### Access control

Data security is a constant concern within enterprises, and this is also true for team assistants. Rebyte has designed a role-based access control system that aims to provide enterprise IT personnel with the utmost flexibility in controlling which data can be accessed by whom.
