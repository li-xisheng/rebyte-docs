## 创建一个欺诈分析助手

背景：您是一家金融公司的数据科学家，负责构建一个欺诈分析助手，以帮助您的团队识别潜在的欺诈案例。助手应该能够分析交易数据并识别可疑模式。

您将拥有：
* 一个包含 10 万条交易记录的 csv 文件。为了您的方便，我们为您准备了一个示例文件。您可以在[这里](https://storage.googleapis.com/cui-runtime/fraud1.csv)下载，或使用[Google 电子表格链接](https://docs.google.com/spreadsheets/d/1mY57k8zYkhCZo51XEydnplWRSu75KiOAhvolTE4IUpw/edit?gid=1496520613#gid=1496520613)。或者，您可以将其导入到 Google 电子表格，Google 会自动将其转换为 csv 格式。
使用 Google 电子表格的一个好处是，您可以直接编辑数据，ReByte 将自动同步数据。

### 第一步：在 ReByte 中创建一个表

这一步涉及在 ReByte 中创建一个表，您应该选择“csv”格式，并上传 csv 文件，或粘贴您的 Google 电子表格链接。

您可以通过点击“Explore”来探索数据，并使用任何 SQL 查询来过滤数据。

假设您最终在 ReByte 中创建了一个名为“transaction”的表。

### 第二步：创建一个欺诈分析工具

在 ReByte 中创建一个新工具，并命名为“Fraud Analysis”。
ReByte 具有预构建的数据分析模板，
您可以选择“Data Analysis”模板，然后根据需要进行修改。
**请记住**在“load table”和“query table”操作中将表更改为您在第一步中创建的“transaction”表。

**重要提示**：
您应该更改工具以从“transaction”表加载架构，并在同一表上运行 SQL。
您可能需要更改输入数据集以反映您要分析的内容。

### 第三步：将“Fraud Analysis”工具添加到您的助手

现在您可以将“Fraud Analysis”工具添加到您的团队助手中。

另一种方法是创建一个新的助手，专门用于欺诈分析，并将“Fraud Analysis”工具添加到该助手中。

派对时间！您已经成功构建了一个欺诈分析助手。

现在您的团队成员可以使用它了。

尝试用以下问题查询助手：

* **显示金额最高的前 10 笔交易**

* **总共有多少笔交易？有多少是欺诈性的？**
