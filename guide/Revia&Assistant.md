# Rebyte User Guide

## Available Platform

[Desktop](https://rebyte.ai) | [Mobile]("https://apps.apple.com/app/rebyte-your-team-assistant/id6466730972")

## Unified Assistant Interface For Your Team

**Revia** is a universal user interface that can be used by all team members to interact with the AI assistant. This interface is designed to handle various types of tasks, such as data retrieval, question and answer, document generation, and data analysis, and more advanced tasks such as interactive chart and table, form filling and more.

Besides Revia, team admin can build other assistants specific to some use cases, for example, a customer support assistant, a sales assistant, a marketing assistant, etc.

The relationship between **Revia** and **Other Assistants** is like the relationship between **Team ChatGpt** and **Team Specific Gpts**.

In terms of functionality, **Revia** is no different from other assistants, the only difference is that **Revia** is always shown on the top of the assistant list, and it's available for all team members.

## Configure Team Assistant
Only builders or admin in your team can configure the team assistant. 

Each assistant, including **Revia**, contains:
* **Planner**: can plan and execute a sequence of tools to achieve a specific goal.
* **Code Sandbox**: Handle arbitrary code execution, such as data analysis, data visualization, etc. 
* **List of Rebyte Tools**: a list of Rebyte Tools that can be used by the assistant. Tool can be built by your team or by other tool builders, or by Rebyte team.

**Planner** and **Code Sandbox** can be optional, in that case, user has to ask specific tool to perform a specific task.

## Use Team Assistant

### Interacts with Revia

* **Directly Ask Questions**: You can ask questions to Revia, such as "What is the sales number of last year?" or "How many employees do we have in the company?".
* **@specific tool**: A noval way to interact with Rebyte, you can @mention a specific tool to perform a specific task, for example, "@image_generator generate an image of a cat".
* **/command**: You can use slash commands to invoke other assistants, for example, "/customer_support"

### Attachment files
* You can attach files to your message, we support various file types, such as csv, xlsx, pdf, docx, png, jpg, etc. Rebyte will automatically parse the file and extract the content for further processing.

### Reasoning Steps
Hallucination is a common issue in AI assistants,Rebyte tries to solve this issue by providing reasoning steps as detail as possible, user can see the reasoning steps of each tool. Builder can also see the actual tool running log to debug if there's any issue.

### Code Sandbox
Rebyte provides a code sandbox for users to run python code, you can use this feature to run some custom code, such as data analysis, data visualization, etc. Each code execution is isolated, so you don't need to worry about the security issue.

