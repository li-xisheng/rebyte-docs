# 快速入门

我们将向您展示如何在 10 分钟内构建一个天气代理。

## 步骤 1：创建工具

* 导航到侧边栏中的“我的代理”标签，然后点击“创建工具”。

* 描述您希望使用该代理执行的操作，并为您的代理选择正确的模板。

<figure><img src="../images/weather-1.png" alt=""></figure>

* 点击“生成工具模板”按钮，我们将为您生成一个基本模板以供构建。

<figure><img src="../images/weather-2.png" alt=""></figure>

* 您可以更改代理的名称、描述和可见性，并添加标签以获取更多信息。如果您不喜欢当前模板，也可以重新生成模板。

* 点击“创建工具”，几秒钟内您将拥有自己的代理。

## 步骤 2：设计您的工具

* 在自动生成的模板中，我们已经为您创建了一些操作。

<figure><img src="../images/weather-3.png" alt=""></figure>

* 构建代理的过程：
  * 从用户输入中获取位置，因此我们需要一个 `Language Model Chat` 操作。
  * 搜索天气，这可以通过 `You.com` 搜索引擎操作完成。
  * 分析结果，我们应使用另一个 `Language Model Chat` 来分析来自 You.com 搜索的结果并生成绘制图片的提示。
  * 绘制图片，我们使用 `Stable Diffusion` 操作并返回一个 base64 图片。

<figure><img src="../images/weather-4.png" alt=""></figure>

* 在编辑器中为模型编写指令，描述您希望模型执行的操作。

<figure><img src="../images/10.png" alt=""></figure>

## 步骤 3：测试您的工具

* 点击顶部的“数据集”标签，然后点击“创建数据集”。

* 填写数据集的名称和描述。

* 由于这是一个聊天机器人，测试数据集将以表示对话的（列表）json 对象形式出现。

<figure><img src="../images/11.png" alt=""></figure>

* 创建数据集后，返回“设计”面板并选择新数据集作为输入。

<figure><img src="../images/11-1.png" alt=""></figure>

* 点击“运行测试用例”以使用数据集测试您的代理。

* 结果将显示在每个操作下方。查看输出是否符合您的预期。如果没有，请更改代理的设置并再次尝试。

<figure><img src="../images/13.png" alt=""></figure>

## 步骤 4：部署工具

* 点击右上角的“部署工具”，然后点击“部署新版本”。

* 您可以在您的 ReByte 应用中使用您的代理，也可以使用我们提供的代码将其集成到您自己的应用中。

<figure><img src="../images/12.png" alt=""></figure>

🎉 **恭喜您，您已创建了您的第一个代理！**

在“我的代理”标签中查看您的所有工具。您还可以在这里克隆、保存或删除您的工具。

<figure><img src="../images/14.png" alt=""></figure>
