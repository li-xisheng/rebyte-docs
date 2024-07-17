# Tool and Knowledge

## Tool

> Backend subroutine for Assistant.

In Rebyte, we define Tool as a serverless API that can be executed on cloud, usually tools will leverage AI models to perform some tasks to achieve its intelligence, but this is not required. An agent without any AI model is just like a normal serverless API, but we will focus on AI tools in this document.
Here are some typical examples of AI tools:
* Based on user's query, find most relevant information from user's knowledge base, and summarize the result and return summary to user.
* User describes a database query in natural language, agent will translate the query into SQL and execute the query on user's database to get results, then use LLM to generate a summary of the results and return to user.
* Help user to do professional translation between two languages, user can describe the translation task in natural language, agent will not only do the translation but also evaluate the translation quality, if the quality is not good enough, agent will iterate the translation process until the quality is good enough. 

### This is a typical tool workflow

<figure><img src="../.gitbook/assets/2.png" alt=""><figcaption></figcaption></figure>

* Tool is a piece of sequential actions that can be executed on the LLM serverless runtime. It is the core building block of ReByte, and the main way for end users to create their own tools. Rebyte provides a GUI builder for end users to create/edit their own LLM tools. Rebyte provides a list of pre-built actions for common use cases, also private SDK for _software engineer_ to build their own actions, and seamlessly integrate with the agent builder. Pre-built actions includes:
  * LLM Actions
    * Language Model Completion Interface
    * Language Model Chat Interface
  * Data Actions
    * Dataset Loader, load pre defined datasets for later processing
    * File Loader, extract/transform/load user's provided files
    * Semantic Search, search for similar content over user's knowledge base
  * Tools Actions
    * Search Engine, search for information on Google/Bing
    * Web Crawler, crawl web pages and extract information
    * Http Request Maker, make any http request to any public/private API
  * Control flow Actions
    * Loop Until, run actions until a condition is met
    * Parallel, execute multiple actions in parallel
    * Vanilla Javascript, execute any vanilla javascript code, useful for doing pure data transformation

## Knowledge - capture private data

> Ingredient for your Assistant.

* Knowledge is private data that is stored in rebyte managed vector database. Rebyte currently provides following connectors for end users to import their knowledge:
  * Local file, supported file types are:
    * "doc", "docx", "img", "epub", "jpeg", "jpg", "png", "xls", "xlsx", "ppt", "pptx", "md", "txt", "rtf", "rst", "pdf", "json", "html"
  * Notion
  * Discord
  * GitHub
  * More connectors are coming soon
* Knowledge can be used in LLM Agents to do semantic search, or to do data augmentation. A great example is to use knowledge to do semantic search on a user's private knowledge base, and use the search result to do data augmentation for a language model, aka **Retrieval Augmented Generation**.
