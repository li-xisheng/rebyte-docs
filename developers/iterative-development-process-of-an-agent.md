# Iterative Development Process of A Tool

Language models are naturally unpredictable, even though lots of techniques have been developed to make them more predictable, for example OpenAI has a seed parameter that can be used to control the randomness of the model. This dramatically changes how we ship software. In the past, we would write a piece of code, compile it, and then ship it. Now, we write a software agent, the only we can guarantee that the agent is working as expected is to have this agent run through a list of test datasets, and evaluate the result to see if it is passing some threshold.

## Iterative Development process of an agent

In ReByte, the first thing to design an agent is to create a test dataset. A test dataset is attached to **INPUT** action of agent, which is always the first action of an agent. In Design Mode, all test cases will be run in parallel to make the whole process faster, also action can be set to 'cache' mode to further speed up the process and save token usage.



<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
