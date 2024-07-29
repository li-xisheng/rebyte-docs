# 构建一个投资者类型测验应用

本综合指南将引导您使用 ReByte 的工具和 Typeform API 创建一个投资者类型测验应用。Typeform 的 API 允许创建用户友好的表单和调查，是与用户进行清晰有效互动的理想选择。

这是应用的最终结果：

![app](https://res.cloudinary.com/dfjwtidnh/image/upload/v1710077600/investor-0_uqamir.png)

## 先决条件

* 一个 [Typeform 账户](https://www.typeform.com/)，以及对 [Typeform API 文档](https://www.typeform.com/developers/)的透彻理解。
* 基本熟悉 ReByte 的代理和应用程序，以及一些编程知识。

## 如何构建

应用程序基于简单的逻辑操作。它首先收集用户的基本信息，然后使用 Typeform API 生成一个表单以询问更详细的问题。用户完成并提交表单后，将分析他们的回答以确定他们的投资者类型。

### 步骤

1. **从用户输入中收集信息：** 

   使用 ReByte 的 `model-chat` 动作根据用户的初始输入提取信息。

   ![gather info](https://res.cloudinary.com/dfjwtidnh/image/upload/v1710077600/intestor-1_vj3kej.png)

2. **使用 Typeform API 创建表单：**
   
   实现预编写的代码来选择表单的合适问题。通过 "" 动作调用 Typeform API，然后生成一个表单 URL。

![code](https://res.cloudinary.com/dfjwtidnh/image/upload/v1710077600/investor-2_sun44v.png)

3. **收集用户的回答：**

   一旦用户提交完成的表单，通过 "http" 动作检索结果。

![get results](https://res.cloudinary.com/dfjwtidnh/image/upload/v1710077600/investor-3_k9ejp9.png)

4. **分析用户的输入：**

   使用随后的 model chat 动作处理用户的回答并确定他们的投资者类型。

   ![analyze](https://res.cloudinary.com/dfjwtidnh/image/upload/v1710077600/investor-4_puom38.png)

### 结论

该项目展示了将 Typeform 等 API 与 ReByte 技术集成的强大功能，以创建互动的用户关注的应用程序。投资者类型测验应用不仅以动态的方式吸引用户，还提供了对其投资偏好的宝贵见解，帮助他们做出明智的决定。本指南中概述的步骤提供了一个框架，可以适应各种应用，展示了这些工具在应用开发领域的灵活性和潜力。

## 演示

要查看应用和工具的实际操作，请访问以下链接：

[投资者类型测验工具](https://rebyte.ai/p/21b2295005587a5375d8/callable/ffdc7bd0d262b62cbd03/editor)

[投资者类型测验应用](https://rebyte.ai/copilot/0167ad764f8be5e1bd41/session/6afc350466)
