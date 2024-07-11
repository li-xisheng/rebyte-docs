# Introduction to Key Concepts

In the Rebyte system, there are the following key concepts:

## Revia

We have preset a personalized assistant for every individual and team: Revia. We have fixed it at the top left corner of the page, making it convenient for you to click and use it whenever you want. Revia is a special Assistant that is automatically created when you create an account based on the information you provide. We have configured it with various tools such as web search, knowledge base query, code interpreter, etc.

### How to Use

In the input box in the middle of the page, you can directly enter your questions to chat with Revia.

You can directly ask about the information you provided when creating your account or team, such as X, notion, **websites, the materials you uploaded.**

You can also use the @ function to designate a specific tool for a particular task, such as: @**Internet Search, help me check the GDP of all countries last year. You can even @ multiple tools at the same time for complex tasks like:** @browser Get the positions of this website, [https://rebyte.ai](https://rebyte.ai/) <@chat_with_llm> and summarize what talents this company mainly recruits.

You can also send images and files (selected from Google Drive) and ask targeted questions.

When the Assistant responds to your message, you can see the process of Revia's operation. After the operation is complete, you will see the final response message. If you are interested in the process, you can click the "Took steps" button to expand the process information and view it.

## Assistant

In addition to Revia, you can configure other functional types of Assistants for yourself and your team. You can customize them for specific tasks or themes by combining commands, knowledge, and functions. They can be as simple or complex as needed, solving any problem from language learning to technical support. Configured Assistants will be displayed in "More Team Assistants." In "More Team Assistants," we also provide Assistants that solve problems in various fields for you to use.

### Configuration Items

Assistants include the following configurable items:

- **Basic Information:** The name and avatar of the Assistant. Give it an intuitive name and avatar. Revia is the name and avatar we have given to your team assistant, so it cannot be changed.
- **Who can use:** We provide permission settings, including public, team public, private, and unlisted permissions, corresponding to public use, team use, team editing only, link access, and team internal editing.
- **Instruction:** The commands of the Assistant. This content will be used for the Assistant's work. ReByte uses commands to generate answers specific to your assistant.
- **Planning:** Plan and choose the best strategy to solve user queries. When this feature is enabled, the Assistant will have the ability to call multiple tools to handle complex issues. For example, if a user asks to find the GDP data of all countries last year and make a table, the Assistant can call the search function to query the GDP, organize the data, and then call **Code Sandbox to organize the data into a table. If this feature is disabled, the assistant will only communicate with the first tool. Whether to enable this feature depends on the function positioning of your Assistant. Revia, as a special Assistant, has this feature enabled by default.
- **Code Sandbox:** When enabled, this GPT can analyze data, process your uploaded files, perform mathematical calculations, etc. Revia, as a special Assistant, has this feature enabled by default.
- **Tools:** The abilities of the assistant. We provide you with dozens of default tools. When you click the "Add Tool" button, you can see them. For details, please check Tool.
- **Home Page:** This page is the default page that users see when they open the Assistant. Here you can personalize the introduction. Tell users how to use the Assistant you configured. We provide a markdown editor where you can edit the content on the left side and see the effect in real-time on the right side. You can also use the "Generate home page for your assistant" feature, which automatically generates introduction content for you.

Note: Configuration items require corresponding permissions to configure. If you do not see the settings button in the top right corner of the Revia page, please contact the team administrator for settings.

## Tool

We provide you with some commonly used tools. The following is an introduction. If you have personalized needs, you can also customize them on the Rebyte Platform.

- **Internet Search:** Can perform internet searches, returning the top three relevant websites and their content summaries. It can obtain the latest data from the internet, including news, prices, etc., but it does not contain any private information about your company.
- chat_with_gpt4o: chat with you using the latest OpenAI model, no additional knowledge. Good at Answering Questions on common knowledge, Providing Explanations, Creative Writing, summarizing content, Programming Help
- chat_with_llm: chat with you using LL, with common knowledge. Good at Answering Questions on common knowledge, Providing Explanations, Creative Writing, summarizing content, Programming, data extraction, etc.
- analyze_image: describe a given image in natural language - explain the image - tell me what happened in the image
- ai_tldr: Summarizes and condenses lengthy text and documents into concise and easy-to-understand summaries, allowing users to quickly grasp the main points without having to read through the entire content. # How it works Generate a summary of any text Tailor the summary to your expectations in terms of length, focus, and data extraction # Great for Getting up to speed on any topic by summarizing it and getting only the most important information
- search_team_knowledge: Retrieval info from the team's knowledge base and generate a concise answer
- universal_file_parser: parse common file to plain text for further processing, supported file types: "doc", "docx", "img", "epub", "xls", "xlsx", "ppt", "pptx", "md", "txt", "rtf", "rst", "pdf", "json", "html", "eml”
- browser: Extract URLs from conversation, for each URL, launch a headless browser to read the content of the page, output markdown format of the page for further processing
- image_generator: create an image based on user-provided descriptions, detailed descriptions lead to better quality.

## Knowledge

You can maintain a knowledge base dedicated to yourself or your team. We have set up a complete knowledge base function for you in Rebyte.

You can choose to upload local files, capture from the internet (websites, X), or synchronize from other places (Google Drive, GitHub, Notion, etc.).

Select the appropriate **Embedding Model and set the Max Chunk Size In Tokens, and your knowledge base is created.**

Note: This feature needs to be maintained by the team administrator on the ReByte Platform.
