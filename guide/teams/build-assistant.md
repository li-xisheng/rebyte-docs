## Config **Revia**

Each team has exact one **Revia** assistant, which is the main interface for team members to interact with the AI assistant. You can config **Revia**'s behavior by clicking the **Config Revia** button in the top right corner of the UI, only builder and admin can config **Revia**.

## Build More Assistants
Besides **Revia**, you can build more assistants to help your team. To build a new assistant, click the **Create Assistant** button in the top right corner of the UI, then follow the steps to create a new assistant. You can also invite other team members to join the assistant, so they can collaborate on the assistant with you.

## Configurations

There are several configurations you can set for your assistant, we only emphasize the most important configurations here.

### Instructions
Describe what you want the assistant to do. We will use this information in various places, such as making responsees more specific to your needs, or do query planning based on your instructions.
We recommend you to write simple but clear instructions, so that the assistant can better understand your needs. For example, if you want the assistant to help you with data analysis, you can write:

- analysis sales data stored in database xxx
- generate a report based on the sales data

### Agents available to the assistant
This is the most important configuration for your assistant. You can select tools that you want to be available to the assistant. The assistant can use these tools to perform tasks for you. For example, if you want the assistant to help you with data analysis, you can select tools that can read data from your database, generate reports, and plot graphs.
There're two categories of tools:
** Agents made by you or your team members
- pros: you can customize the tools to fit your needs
- cons: you need to spend time building the tools

** Agents made by ReByte System
- pros: you can use the tools immediately without building them, we will keep updating the tools to make them more powerful
- cons: you may not modify the tools to fit your needs

All system tools are open source, you clone the agent to your team and modify it to fit your needs.
