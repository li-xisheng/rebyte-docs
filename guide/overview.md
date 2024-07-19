# Overview

## What is ReByte?

ReByte is an AI-powered platform leveraging GPT4, Claude, Gemini, and Mistral to enhance team collaboration and productivity. Utilize AI assistants to gain deeper insights into any subject, streamline work processes, and boost overall efficiency. Whether you need assistance with company-related inquiries, drafting documents, or simplifying complex tasks, ReByte's AI assistants have you covered. Create personalized assistants or collaborate with your team on shared assistants tailored to your specific needs.


<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

## General concepts

### Assistants

ReByte assistants are AI-powered tools that can do planning, reasoning, and execution. They can help with a wide range of tasks, from answering questions to creating documents specific to company's data. Assistants can leverage customized tools built by your team to provide more tailored responses.

Here are some typical tasks that assistants can help with:

* Answering questions about your company, for example, financial data or company policies.
* Drafting documents, such as memos or reports, based on your company's data as well as public information.
* Providing insights into customer behavior or market trends, extract data from your company's data sources, and plot graphs or tables based on the data.
* Professional Translation, translate document to target language with multiple rounds of proofreading and editing.

If you are familiar with the concept of chatgpt, ReByte assistants are similar to GPTs but with more focus on team productivity and collaboration.

### Agents

Agents are building blocks for assistants. They can be customized to perform specific tasks, such as data retrieval, document generation, or data analysis, main idea behind agent is to capture proprietary knowledge and automate repetitive tasks within your organization.

Here are some example tools:

* Answering questions about your company's financial data from a predefined xlsx file
* Analyzing market trends from some Twitter accounts
* Call internal APIs to retrieve data from your company's database

You can think of tools as a way to encapsulate your company's knowledge and processes into reusable components that can be used by your assistants. Tool concept is similar to the concept of "skills" or "tools" in other AI assistant platforms, or flow engineering.

### Actions

Action is a building block of an agent. Action is a single unit of work that an agent can perform, such as make a LLM call, read a file, or generate a document, run piece of code, etc. Actions can be chained together to form a sequence of actions that the agent will perform.

Here are builtin actions that ReByte supports:

* Call LLM
* Internet Search
* Load History messages
* Load Dataset
* Knowledge Search over vector database
* Parse file to structured data
* Run JS code
* Loop until
* If-else
* Map-Reduce for parallel processing

With extension API, you can create your own actions to perform custom tasks that are specific to your organization.

### Knowledge

Knowledge is the data that your tools and assistants can access. It can be your company's data, such as Notion pages, Google Drive files, or local files, as well as public data sources like Wikipedia or news websites. Knowledge is the foundation for your tools and assistants to provide accurate and relevant information.

Currently, ReByte supports the following data sources:

* Local files
* Web pages
* Discord
* Twitter
* Notion
* Google Drive
* GitHub

ReByte use LLM embeddings to convert data into a format that can be used by tools and assistants. Currently, ReByte supports the two following embedding providers:

* OpenAI embeddings
* Voyager embeddings

### Team

The team is a group of users who collaborate on ReByte. Each team has its own space where members can create and share assistants, tools, and knowledge. Team members can have different roles, such as admin, builder, or user, with varying permissions to manage and access the workspace.

