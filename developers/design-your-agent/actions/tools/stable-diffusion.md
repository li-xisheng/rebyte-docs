# 稳定扩散

此动作允许您输入文本提示，并使用稳定扩散模型生成图像。

<figure><img src="../../../../images/sd-1.png"></figure>

## 用法

* 首先，将“稳定扩散”动作添加到您的代理中。

<figure><img src="../../../../images/sd-2.png"></figure>

* 填写提示、图像大小和响应格式。
  * 提示：您想要生成的图像的详细描述。
  * 图像大小：您想要生成的图像大小。应为以下之一：“1024x1024”、“1792x1024”、“1024x1792”。
  * 响应格式：响应的格式。应为以下之一：“url”、“b64_json”。
  
<figure><img src="../../../../images/sd-3.png"></figure>
  
## 输出

* 此动作的输出是一个 URL 或 base64 编码的图像。

<figure><img src="../../../../images/sd-4.png"></figure>

* 点击链接，您将看到生成的图像！

<figure><img src="../../../../images/sd-5.png"></figure>

* 您可以使用 `env.state.REBYTE_OPENAI_IMAGE_GEN_1.images[0].url` 或 `{{REBYTE_OPENAI_IMAGE_GEN_1.images[0].url}}` 在下一个动作中引用 URL。
  
* base64 编码的图像可以使用 `env.state.REBYTE_OPENAI_IMAGE_GEN_1.images[0].base64` 或 `{{REBYTE_OPENAI_IMAGE_GEN_1.images[0].base64}}` 进行引用。

## 示例工具

* [这是](https://rebyte.ai/p/21b2295005587a5375d8/callable/3396e0e83a81396c1ba7/editor) 使用稳定扩散动作的“如何使用”代理。

* [这是](https://rebyte.ai/copilot/c359f8a71fa2e7c6264a/session/d67c8195be) 稳定扩散的应用程序。
