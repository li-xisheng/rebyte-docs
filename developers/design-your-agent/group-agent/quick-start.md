# Quick Start

In this tutorial, we will show you how to create a group agent that will discuss a topic between two agent.

## Step 1: Create A Group Tool

* Navigate to the "Agents" tab in the sidebar and then click on "Create Tool" on the top right.

* Choose the "Group Tool" option.

* Fill in the name,description, and set the visibility of your group agent.

<figure><img src="../../../images/group-1.png"></figure>


## Step 2: Design Your Group Tool

* This agent only has four actions:`Input`, `Thread`, `Tool Group` and `Output`, and you can't add or delete any action.

* The `Input` and `Output` actions are the same as a stack agent.You can create your own datasets to test your agent.

**Thread**

<figure><img src="../../../images/group-2.png"></figure>

* Configure the "Max Number of Previous Runs on Thread" in the `Thread` action using the toggle button. This is the maximum number of history messages that the agent will record and send to the model everytime it runs.

* The longer the history, the more context the model will have to work with. However, the longer the history, the slower the agent will run. 
  
**Tool Group**

<figure><img src="../../../images/group-3.png"></figure>

* Choose the tools you want to use in the `Tool Group` action. Here we choose the two student chatbot tools we created.

* NOTE: You must be familiar with the agent's function and the agent's input and output format. Also make sure the agent's output format is compatible with the next agent's input format.
  
* Specify the execution order of the tools in the group agent. The agent will run the tools in the order you specified. For example, here we put "round robin" in Tool Selector Instruction, so the agent will run the tools one by one in a loop.
  
* Following the given order, the system will run the tools one by one. The first agent's output will be the input of the second agent, and so on.
  
* You can also set the maximum rounds of conversation between tools. If the conversation between tools exceeds the maximum rounds, the agent will stop running.

And that's it!

## Step 3: Test Your Group Tool

* This is basically the same a [testing a stack agent](../../test-your-agent/overview.md). 
  
* The only difference is that rather than focusing on the output of only one agent, you should take a good look at the output of all the tools in the group agent and try to find out if their behavior is what you want.



