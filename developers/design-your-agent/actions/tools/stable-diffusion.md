# Stable Diffusion

This action allows you to input text prompts and generate images using the Stable Diffusion model.

<figure><img src="../../../../images/sd-1.png"></figure>

## Usage

* First, add a "Stable Diffusion" action to your agent.

<figure><img src="../../../../images/sd-2.png"></figure>

* Fill in the prompt, image size and the response_format.
  * prompt: detailed description of the image you want to generate.
  * image size: the size of the image you want to generate. Should be one of the following: "1024x1024", "1792x1024", "1024x1792".
  * response_format: the format of the response. Should be one of the following: "url", "b64_json".
  
<figure><img src="../../../../images/sd-3.png"></figure>
  
## Output 

* The output of this action is a URL or a base64 encoded image.

<figure><img src="../../../../images/sd-4.png"></figure>

* Click the link and you will see the generated image!

<figure><img src="../../../../images/sd-5.png"></figure>

* You can use `env.state.REBYTE_OPENAI_IMAGE_GEN_1.images[0].url` or `{{REBYTE_OPENAI_IMAGE_GEN_1.images[0].url}}` to reference the URL in the next action. 
  
* The base64 encoded image can be referenced using `env.state.REBYTE_OPENAI_IMAGE_GEN_1.images[0].base64` or `{{REBYTE_OPENAI_IMAGE_GEN_1.images[0].base64}}`.

## Example Tool

* [This](https://rebyte.ai/p/21b2295005587a5375d8/callable/3396e0e83a81396c1ba7/editor) is the "HowToUse" agent for stable diffusion action.

* [This](https://rebyte.ai/copilot/c359f8a71fa2e7c6264a/session/d67c8195be) is the app for stable diffusion.