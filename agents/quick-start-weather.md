# Quick Start

We will show you how to build a weather agent in 10 minutes.

## Step 1: Create a Tool

* Navigate to the "My Agents" tab in the sidebar and then click on "Create Tool".

* Describe what you want to do with this agent and choose the right template for your agent. 

<figure><img src="../images/weather-1.png" alt=""></figure>

* Click the "Generate Tool Template" button and we will generate a basic template for you to build from. 

<figure><img src="../images/weather-2.png" alt=""></figure>

* You can change the name, description and visibility of the agent and add tags for more information. Or you can simply regenerate the template if you don't like the current one.

* Click the "Create Tool" and you will have your own agent in just a few seconds.

## Step 2: Design Your Tool

* In the auto-generated template, we have already created some actions for you. 

<figure><img src="../images/weather-3.png" alt=""></figure>

* The process of building the agent:
  * To get the location from the user's input, so we need a `Language Model Chat` action. 
  * To search for the weather, this can be done using the `You.com` search engine action. 
  * To analyze the results, we should use another `Language Model Chat` to analyze the search results from the You.com search and generate a prompt to draw the picture.
  * To draw the picture, we use `Stable Diffusion` action and return a base64 picture.

<figure><img src="../images/weather-4.png" alt=""></figure>

* Write the instructions more the model in the editor, describing what you want the model to do.

<figure><img src="../images/10.png" alt=""></figure>

## Step 3: Test Your Tool

* Click the "Datasets" tab on the top, then click "Create Datasets". 

* Fill in the name and description of your dataset.

* Since this is a chatbot, the testing dataset will be in the form of a (list of) json object representing a conversation.

<figure><img src="../images/11.png" alt=""></figure>

* After you've created the dataset, go back to the "Design" panel and choose the new dataset as the input.

<figure><img src="../images/11-1.png" alt=""></figure>

* Click "Run Testcases" to test your agent with the dataset.

* The results will be shown below each action. See if the output is what you want. If not, change the settings of your agent and try again.

<figure><img src="../images/13.png" alt=""></figure>

## Step 4: Deploy the Tool

* Click "Deploy Tool" on the top right, then click "Deploy A New Version". 

* You can use your agent on your ReByte app or integrate it into your own app using the code we provide.

<figure><img src="../images/12.png" alt=""></figure>

🎉 **Congratulations, you have created your first agent!**

View all your tools in the "My Agents" tab. You can also clone, save, or delete your tools here.

<figure><img src="../images/14.png" alt=""></figure>

