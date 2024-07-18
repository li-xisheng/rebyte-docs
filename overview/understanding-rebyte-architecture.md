## What is a Tool?

> Backend subroutine for Assistant.

In Rebyte, we define Tool as a serverless API that can be executed on cloud, usually tools will leverage AI models to perform some tasks to achieve its intelligence, but this is not required. A Tool without any AI model is just like a normal serverless API, but we will focus on AI tools in this document.
Here are some typical examples of AI tools:
* Based on user's query, find the most relevant information from the user's knowledge base, and summarize the result and return the summary to the user.
* User describes a database query in natural language, agent will translate the query into SQL and execute the query on user's database to get results, then use LLM to generate a summary of the results and return to user.
* Help user to do professional translation between two languages, user can describe the translation task in natural language, agent will not only do the translation but also evaluate the translation quality, if the quality is not good enough, agent will iterate the translation process until the quality is good enough. 

### This is a typical tool workflow

<figure><img src="../.gitbook/assets/2.png" alt=""><figcaption></figcaption></figure>

   
## How to build a Tool?





### Action
* Tool is a piece of sequential actions that can be executed on the LLM serverless runtime. It is the core building block of ReByte, and the main way for end users to create their own tools. Rebyte provides a GUI builder for end users to create/edit their own LLM tools. Rebyte provides a list of pre-built actions for common use cases, also private SDK for _software engineer_ to build their own actions, and seamlessly integrate with the agent builder. Pre-built actions include:
  * LLM Actions
    * Language Model Interface
  * Data Actions
    * Dataset Loader, load pre defined datasets for later processing
    * File Loader, extract/transform/load user's provided files
    * Table Query, translate user's natural language query into SQL and execute the query on user's database
    * Semantic Search, search for similar content over user's knowledge base
  * Tools Actions
    * Search Engine, search for information on Google/Bing
    * Web Crawler, crawl web pages and extract information
    * Http Request Maker, make any http request to any public/private API
  * Control flow Actions
    * Loop Until, run actions until a condition is met
    * Parallel, execute multiple actions in parallel
    * Vanilla Javascript, execute any vanilla javascript code, useful for doing pure data transformation

### Dataset
* Dataset is a collection of JSON data that actions can use, the most important dataset is the tool input test dataset, which is the data that used to run the tool everything you run tool from tool builder UI, think about input dataset as the test case for your tool, it should cover all possible scenarios that your tool will face in production. 

### Lifecycle of a Tool
LLM is naturally unpredictable, it's hard to predict what LLM will do in a specific scenario. The typical lifecycle of a tool is:
1. Define test dataset, this is the data that you will use to test your tool, it should cover all possible scenarios that your tool will face in production.
2. Design your tool. This is the process of creating a sequence of actions that LLM will execute.
3. Run to test your tool, this is the process of running your tool with the test dataset, and see if the result is as expected.
4. Loop previous steps until you are satisfied with the result.
5. Deploy your tool to production. This is the process of making your tool available to end users.

## Tool Version
Every Deployment of a tool triggers a new version, starting from 1.
There are two special version strings:
'latest' always points to the newest version of the tool.
'Live': You can manually promote a version to live, this is the version that end users will use.

The best practice is to always use 'latest' in your development environment,
and use 'live' in your production environment. 

## Tool Observability
Rebyte records everything that happens during the execution of a tool,
including the input data, the output data, the reasoning steps, and the execution log.
We call this information a **Tool Run**.
**Tool Run** is crucial for debugging and improving the tool.
You can access this information in the tool builder UI. 

[//]: # (## Knowledge - capture private data)

[//]: # ()
[//]: # (> Ingredient for your Assistant.)

[//]: # ()
[//]: # (* Knowledge is private data that is stored in rebyte managed vector database. Rebyte currently provides following connectors for end users to import their knowledge:)

[//]: # (  * Local file, supported file types are:)

[//]: # (    * "doc", "docx", "img", "epub", "jpeg", "jpg", "png", "xls", "xlsx", "ppt", "pptx", "md", "txt", "rtf", "rst", "pdf", "json", "html")

[//]: # (  * Notion)

[//]: # (  * Discord)

[//]: # (  * GitHub)

[//]: # (  * More connectors are coming soon)

[//]: # (* Knowledge can be used in LLM Agents to do semantic search, or to do data augmentation. A great example is to use knowledge to do semantic search on a user's private knowledge base, and use the search result to do data augmentation for a language model, aka **Retrieval Augmented Generation**.)
