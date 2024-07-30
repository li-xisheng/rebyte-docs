# 构建 Agent 的步骤

# 第一步：定义任务

明确 Agent 需要完成的任务，如数据检索、文档生成或数据分析。

# 第二步：选择动作

动作是 Agent 的基本构建块，是代理可以执行的单个工作单元。以下是 ReByte 支持的内置动作：

- **模型 (Model)**

  - 语言模型对话界面 (Language Model Chat Interface)
  - 使用高级功能（如函数接口或基于消息的接口）查询大型语言模型 (???)。

- **数据 (Data)**

  - 数据集加载器 (Dataset Loader)：将数据加载到 JSON 对象中以便将来处理。
  - 历史消息加载器 (History Messages Loader)：从线程加载历史消息以供后续操作。
  - 文件加载器 (File Loader)：从文件中提取结构化数据，转换并加载以便将来处理。

- **控制 (Control)**

  - 如果-否则 (If Else)：如果满足条件，则执行一系列操作，否则跳过。
  - 循环直到 (Loop Until)：循环遍历一系列块直到满足条件。
  - Map Reduce：遍历数组并并行执行一系列块。
  - 提前返回 (Early Return)：提前退出代理。

- **实用工具 (Utilities)**

  - 知识搜索 (Knowledge Search)：基于您指定的知识进行搜索。
  - Google 搜索 (Google Search)：向谷歌发出查询，以便您可以将结果传递给其他块。
  - Http 请求生成器 (Http Request Maker)：执行 HTTP 请求以与外部服务接口。
  - 网页爬虫 (Web Page Crawler)：获取网页内容并将其转换为 Markdown 以便进一步处理。
  - 调用另一个工具 (Call Another Tool)：调用另一个代理并将结果传递给下游操作。

- **代码 (Code)**
  - 运行 JavaScript 代码 (Run JavaScript Code)：运行一段 JavaScript 代码以修改、增强或合并来自其他操作的结果。

# 第三步：配置动作

## 语言模型对话 (Language Model Chat)

配置语言模型对话动作，让代理能够与大型语言模型进行交互，生成所需的响应。

1. **指令 (Instruction)**

   - 编写您的提示，告诉大型语言模型该做什么。
   - 支持 [Tera](https://keats.github.io/tera/docs/) 格式。

2. **消息 (Messages)**

   - 将消息发送到 LLM，可以是字符串列表或对象列表。
   - 使用 Javascript 或 Tera 格式引用其他动作的输出。

3. **函数 (Functions)**

   - 允许模型智能生成 JSON 对象，连接外部工具。

4. **模型配置 (Model Configuration)**

   - 选择要使用的模型，默认模型是 "gpt-3.5-turbo-1106"。
   - 配置温度、最大输出令牌、JSON 响应、种子和停止词。

5. **其他设置 (Other Settings)**
   - 流模式 (Stream Mode)：允许接收部分聊天响应。
   - 缓存模式 (Cache Mode)：存储频繁访问的数据，提高响应时间。

<figure><img src="./images/chat-config-button.jpg" alt=""><figcaption>配置按钮 (Config Button)</figcaption></figure>

## 数据集加载器 (Dataset Loader)

`数据集加载器` 动作允许您从代理的数据集中加载数据。数据可以在后续动作中使用。

1. **用法 (Usage)**
   - 将 `数据集加载器` 动作添加到您的代理中，并选择要加载的数据集。
   - 在下游动作中使用数据集的名称引用这些数据，例如：`{{DATA_2}}`。

<figure><img src="./images/dataset-loader.png" alt=""><figcaption>数据集加载器 (Dataset Loader)</figcaption></figure>

2. **示例工具 (Example Tool)**
   - [数据集加载器 (Dataset Loader)](https://rebyte.ai/p/21b2295005587a5375d8/callable/fa56c8cf3f2080ef08d4/editor)

## 线程消息加载器 (Thread Messages Loader)

`线程消息加载器` 动作允许您配置由“线程”记忆的历史消息数量，并在使用此代理时发送给大型语言模型。

1. **用法 (Usage)**
   - 将“线程消息加载器”动作添加到您的代理中。

<figure><img src="./images/thread-1.png" alt=""><figcaption>线程消息加载器 (Thread Messages Loader)</figcaption></figure>
  
   - 指定由“线程”记忆的消息数量。

<figure><img src="./images/thread-2.png" alt=""><figcaption>指定消息数量 (Specify Number of Messages)</figcaption></figure>

- 由“线程”记忆的消息数量会影响大型语言模型的性能。记忆的消息**越多**，大型语言模型能获得的**上下文**越多，但这也会增加大型语言模型的响应时间。

## 文件加载器 (File Loader)

`文件加载器` 动作可以加载先前通过 ReByte UI 或 API 上传到 ReByte 的文件。一个典型的用例是希望代理处理用户上传的文件。

1. **用法 (Usage)**

   - 将 `文件加载器` 动作添加到您的代理中，并选择要上传到代理的文件。
   - 指定此文件的 `file_id`，并在需要引用此文件时使用此唯一的 `file_id`。
   - 如果您将代理连接到应用程序，应用程序用户可以在应用程序中上传文件，`file_id` 将传递给代理。
   - 此动作的输出为 JSON 格式，包含从文件中提取的数据。

2. **示例工具 (Example Tool)**
   - [文件加载器 (File Loader)](https://rebyte.ai/p/21b2295005587a5375d8/callable/bb48d1c1658b5a08917a/editor)

## 代码 (Code)

`Code` 动作是一个非常常用的动作。它允许您编写 Javascript 代码，以任何您想要的方式处理来自先前动作的数据。

1. **用法 (Usage)**

   **一般用法 (General Usage)**

   - 将 `Code` 动作添加到您的代理中。
   - 编写任何 Javascript 代码，以处理来自先前动作的数据并将数据发送到下一个动作。

   **缓存 (Cache)**

   - 在 `Code` 动作的右上角有一个 `cache` 按钮。如果打开它，结果将被缓存。如果 `Code` 动作的输入和代码相同，结果将直接从缓存中返回。这可以大大提高代理的性能。

2. **示例 (Example)**
   - 例如，如果 `MODEL_CALL` 动作返回的消息包含如下的 JSON 字符串：`"{"location":"New York","weather":"partly cloudy","temperature":"43"}"`。
   - 您可以添加一个 `Code` 动作（命名为 "CODE_1"）并编写以下代码：

```javascript
const \_fun = (env) => {
var jsonString = env.state.MODEL_CALL.message.content;
var jsonObject = JSON.parse(jsonString);
var weather = jsonObject.weather;
return weather;
}
```

<figure><img src="./images/code-2.png"></figure>

- 现在您可以使用 `{{CODE_1}}` 或 `env.state.CODE_1` 来获取 "weather" 字段的值。

<figure><img src="./images/code-3.png"></figure>

3. **示例工具 (Example Tool)**
   - 您可以在以下代理中找到上述示例中显示的代码。
   - [代码动作 (Code Action)](https://rebyte.ai/p/21b2295005587a5375d8/callable/4929456b3b6bfcee316d/editor)

# 第四步：测试和优化

在正式使用前，对 Agent 进行测试，确保其能够按预期完成任务。根据测试结果进行优化和调整。

# 示例

# 示例 1：财务数据检索

1. **定义任务**：从预定义的 xlsx 文件中回答财务数据问题。
2. **选择动作**：
   - 数据集加载器
   - 文件加载器
   - 运行 JS 代码进行数据检索
3. **配置动作**：
   - 设置数据集路径
   - 配置文件解析规则
   - 编写 JS 代码进行查询
4. **测试和优化**：根据测试结果调整查询条件和代码

# 示例 2：市场趋势分析

1. **定义任务**：分析 Twitter 上的市场趋势。
2. **选择动作**：
   - 互联网搜索
   - 解析网页
   - 知识搜索
3. **配置动作**：
   - 设置搜索关键词
   - 配置网页解析规则
   - 设置知识搜索条件
4. **测试和优化**：根据测试结果调整搜索关键词和解析规则

# 总结

通过以上步骤，您可以构建出功能强大的 Agent，提升团队的协作和生产力。ReByte 提供了灵活的工具和配置选项，帮助您实现各种复杂任务的自动化和智能化。

![img](<.gitbook/assets/image%20(5).png>)
