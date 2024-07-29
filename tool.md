## 什么是工具？

> 助手的后端子程序。

### 为什么我们需要它？

工具是一种捕获先验知识和经验并使其可由助手重复使用的方法。

让我们考虑一个示例，代理被要求阅读手册并按照说明处理数据。我们确切地知道如何执行以下操作：
1. 阅读手册
2. 解析手册
3. 按照说明进行操作
4. 处理数据

我们不需要任何 LLM 规划能力来执行此操作，我们只需要按顺序执行一系列动作即可。这就是工具的作用，工具是一系列可以按顺序或并行执行的动作，动作可以是从读取文件、发出 HTTP 请求到执行 SQL 查询、调用 LLM 等任何操作。

在 ReByte 中，我们将工具定义为可以在云端执行的无服务器 API，通常工具将利用 AI 模型来执行某些任务以实现其智能，但这不是必需的。没有任何 AI 模型的工具就像普通的无服务器 API，但我们将在本文档中重点介绍 AI 工具。
以下是一些典型的 AI 工具示例：
* 根据用户的查询，从用户的知识库中找到最相关的信息，总结结果并返回给用户。
* 用户用自然语言描述数据库查询，代理将查询翻译为 SQL 并在用户的数据库上执行查询以获取结果，然后使用 LLM 生成结果摘要并返回给用户。
* 帮助用户在两种语言之间进行专业翻译，用户可以用自然语言描述翻译任务，代理不仅会进行翻译，还会评估翻译质量，如果质量不够好，代理将迭代翻译过程直到质量足够好。

[//]: # (### 这是一个典型的工具工作流程)

[//]: # (<figure><img src="../.gitbook/assets/2.png" alt=""><figcaption></figcaption></figure>)


## 如何构建工具？

我们为常见用例预构建了模板，您可以从这些模板开始，也可以从头开始构建自己的工具。

### 动作
* 工具是一段可以在 LLM 无服务器运行时执行的连续动作。它是 ReByte 的核心构建块，也是终端用户创建自己工具的主要方式。ReByte 提供了一个 GUI 构建器，供终端用户创建/编辑自己的 LLM 工具。ReByte 提供了一系列针对常见用例的预构建动作，以及供 _软件工程师_ 构建自己的动作并与代理构建器无缝集成的私有 SDK。预构建动作包括：
  * LLM 动作
    * 语言模型接口
  * 数据动作
    * 数据集加载器，加载预定义的数据集以供后续处理
    * 文件加载器，提取/转换/加载用户提供的文件
    * 表查询，将用户的自然语言查询翻译为 SQL 并在用户的数据库上执行查询
    * 语义搜索，在用户的知识库中搜索相似内容
  * 工具动作
    * 搜索引擎，在 Google/Bing 上搜索信息
    * 网页爬虫，抓取网页并提取信息
    * HTTP 请求生成器，向任何公共/私有 API 发出任何 HTTP 请求
  * 控制流动作
    * 循环直到，运行动作直到满足条件
    * 并行，执行多个并行动作
    * 纯 JavaScript，执行任何纯 JavaScript 代码，用于进行纯数据转换

### 数据集
* 数据集是一组动作可以使用的 JSON 数据，最重要的数据集是工具输入测试数据集，这是每次从工具构建器 UI 运行工具时使用的数据，将输入数据集视为工具的测试用例，它应涵盖工具在生产中将面临的所有可能场景。

### 工具的生命周期
LLM 天生是不可预测的，很难预测 LLM 在特定场景中会做什么。工具的典型生命周期如下：
1. 定义测试数据集，这是您将用于测试工具的数据，它应涵盖工具在生产中将面临的所有可能场景。
2. 设计你的工具。这是创建 LLM 将执行的动作序列的过程。
3. 运行测试你的工具，这是用测试数据集运行工具的过程，看看结果是否符合预期。
4. 循环前面的步骤，直到您对结果满意为止。
5. 将您的工具部署到生产中。这是使工具可供终端用户使用的过程。


## 动作链
### 输入和输出

这里有两种情况：

* 构建一个与 ReByte 的助手无缝集成的工具，您的工具需要符合特定的输入/输出格式。助手将根据工具的输入/输出格式显示特定的 UI 元素，例如，如果您的工具有表输出，助手将以表格格式显示表。
* 构建一个工具并通过 API 访问，您可以定义自己的输入/输出格式。


以下是 ReByte 助手的输入/输出格式：

```javascript

export const AssistantIOSchema: JSONSchemaType<ChatProtocolType> = {
  type: "object",
  properties: {
    role: { type: "string" },
    content: { type: "string" },
    parts: {
      type: "array",
      items: AttachmentItemSchema,
      nullable: true,
    },
  },
  required: ["role", "content"],
}

const AttachmentItemSchema: JSONSchemaType<AttachmentItem> = {
  type: "object",
  properties: {
    type: {
      type: "string",
      enum: ["file", "text", "image_url", "link", "table"],
    },
    text: { type: "string", nullable: true },
    file: {
      type: "object",
      nullable: true,
      properties: {
        id: { type: "string" },
        name: { type: "string", nullable: true },
      },
      required: ["id"],
    },
    image_url: {
      type: "object",
      nullable: true,
      properties: {
        url: { type: "string" },
        detail: { type: "string", enum: ["low", "high"], nullable: true },
      },
      required: ["url"],
    },
    link: {
      type: "object",
      nullable: true,
      properties: {
        title: { type: "string", nullable: true },
        url: { type: "string" },
        id: { type: "string", nullable: true },
      },
      required: ["url"],
    },
    table: {
      type: "object",
      nullable: true,
      properties: {
        name: { type: "string" },
        columns: { type: "array", items: { type: "string" } },
        data: {
          type: "array",
          items: {
            type: "object",
            properties: {
              value: { type: "array", items: { type: "string" } },
            },
            required: ["value"],
          },
        },
      },
      required: ["name", "columns", "data"],
    },
  },
  required: ["type"],
}



```

### 参考先前动作输出

动作按顺序运行，先前动作的输出只是一个普通的 JSON 对象，可以用作下一个动作的输入。
有两种引用先前动作输出的方法：
* 在 JavaScript 代码中，使用
```javascript
env.state['action_name']
```
来引用名为 'action_name' 的先前动作的输出。

* 在 Jinja 模板中，使用
```jinja2
{{ action_name }}
```
来引用名为 'action_name' 的先前动作的输出。

动作可以输出：
* 字符串
* 数组
* 对象

[//]: # (### 运行时配置)

[//]: # (## 知识 - 捕获私有数据)

[//]: # ()
[//]: # (> 你的助手的成分。)

[//]: # ()
[//]: # (* 知识是存储在 ReByte 管理的向量数据库中的私有数据。ReByte 目前为终端用户提供以下连接器以导入他们的知识：)

[//]: # (  * 本地文件，支持的文件类型有：)

[//]: # (    * "doc", "docx", "img", "epub", "jpeg", "jpg", "png", "xls", "xlsx", "ppt", "pptx", "md", "txt", "rtf", "rst", "pdf", "json", "html")

[//]: # (  * Notion)

[//]: # (  * Discord)

[//]: # (  * GitHub)

[//]: # (  * 更多连接器即将推出)

[//]: # (* 知识可以在 LLM 代理中用于进行语义搜索，或进行数据增强。一个很好的例子是使用知识在用户的私有知识库中进行语义搜索，并使用搜索结果对语言模型进行数据增强，即 **检索增强生成**。)


## 工具版本
每次工具部署都会触发一个新版本，从 1 开始。
有两个特殊的版本字符串：
'latest' 始终指向最新版本的工具。
'Live'：您可以手动将一个版本提升为 live，这是终端用户将使用的版本。

最佳实践是在开发环境中始终使用 'latest'，
在生产环境中使用 'live'。


## 工具可观测性
ReByte 记录了工具执行过程中发生的一切，
包括输入数据、输出数据、推理步骤和执行日志。
我们称这些信息为 **工具运行**。
**工具运行** 对调试和改进工具至关重要。
您可以在工具构建器 UI 中访问这些信息。
