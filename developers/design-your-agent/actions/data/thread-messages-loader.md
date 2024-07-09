# Thread Messages Loader

This action allows you to configure the number of historical messages to be memorized by the "thread" and sent to the large language model when using this agent.

Everytime a new message is received by the agent, the "thread" will be updated with the new message and add the corresponding number of historical messages as content and send it to the large language model.

## Usage

* Add a "Thread Messages Loader" action to your agent.

<figure><img src="../../../../images/thread-1.png"></figure>
  
* Specify the number of messages to be memorized by the "thread".

<figure><img src="../../../../images/thread-2.png"></figure>

* The number of messages to be memorized by the "thread" can affect the performance of the large language model. 
  
* The **more messages** to be memorized, the **more context** the large language model can get, but this will also increase the response time of the large language model.
  

