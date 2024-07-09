# Dalle Image Generator

This action allows you to input text prompts and generate images using the [DALL-E](https://openai.com/blog/dall-e/) model.

## Usage

* First, add a "Dalle Image Generator" action to your agent.

<figure><img src="../../../../images/dalle-1.png"></figure>

* Fill in the prompt, image size and the response_format.
  * prompt: detailed description of the image you want to generate.
  * image size: the size of the image you want to generate. Should be one of the following: "1024x1024", "1792x1024", "1024x1792".
  * response_format: the format of the response. Should be one of the following: "url", "base64".
  
<figure><img src="../../../../images/dalle-2.png"></figure>
  
## Output 

* The output of this action is a URL or a base64 encoded image.

<figure><img src="../../../../images/dalle-3.png"></figure>

* Click the link and you will see the generated image!

<figure><img src="../../../../images/dalle-4.png"></figure>

* You can use `env.state.REBYTE_OPENAI_IMAGE_GEN_1.images[0].url` or `{{REBYTE_OPENAI_IMAGE_GEN_1.images[0].url}}` to reference the URL in the next action. 
  
* The base64 encoded image can be referenced using `env.state.REBYTE_OPENAI_IMAGE_GEN_1.images[0].base64` or `{{REBYTE_OPENAI_IMAGE_GEN_1.images[0].base64}}`.