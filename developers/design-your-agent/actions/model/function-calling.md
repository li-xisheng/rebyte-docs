# Function Call

## Example 1

This is a simple demonstration of how to use the "Functions" feature. 

* First, uncomment the code in the "Functions" section.

<figure><img src="../../../../images/openai-functions.png"></figure>

* This is a detailed description of a weather API. You can use this API to get the weather information of a city.

* For any given input, the model will see if there is a need to call your function. 
  
* If so, it will give you json with the arguments you need to call the function. 
  
<figure><img src="../../../../images/openai-functions-1.png"></figure>

* Otherwise, it will respond like a normal chatbot.

<figure><img src="../../../../images/openai-functions-2.png"></figure>

* **NOTE**: If you use the "Functions" feature, you should use another action to call the actual function API. The language model only gives you the arguments you need to call the function API.

## Example 2

This is a more complex example of how to use the "Functions" feature. 

I will show you how to use the "Functions" feature and how to connect the result of the "Functions" feature to "Http Request Maker" to call the actual function API.

