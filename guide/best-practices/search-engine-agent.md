# 搜索引擎代理

帮助您总结网页内容。

### 在 `Datasets` 中设置测试数据

```json
[
  {
    "role": "user",
    "content": "Who won the last UEFA Champions League?"
  },
  {
    "role": "assistant",
    "content": "The last winner of the UEFA Champions League was Manchester City in the 2022-23 season. This was their first title in the competition. Real Madrid holds the record for the most victories in the Champions League, having won it 14 times [0][1]."
  },
  {
    "role": "user",
    "content": "Who scored the winning goal?"
  }
]
```

### 使用 `Code Action` 获取最后一条消息

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
  return env.state.INPUT.messages.slice(-1)[0].content
}
```

### 使用 `Code Action` 获取聊天记录

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
  return env.state.INPUT.messages.slice(0, env.state.INPUT.messages.length - 1).map((m) => m.content).join("\n")
}
```

### 使用 `Code Action` 提取内容

```txt
{# Your prompt here, for example: 'Answer those question based on the following content.' #}
{# Begin your prompt below: #}
This is the question: {{EXTRACT_QUESTION}}
This is the conversation history: {{HISTORY}}

Add necessary contexts to the question with the help of conversation history. If the contexts are irrelevant don't change the question. Give the question here:
```

### 使用 `Google_search` 搜索相关内容

```javascript
{{REFINED_QUESTION.completion.text}}
```

### 使用 `Code Action` 提取内容

```javascript
// Extracts title, snippet and link from the google search's organic results.
// capped at 3
_fun = (env) => {
  if (!env.state.GOOGLE_SEARCH.organic_results) {
    return [
      {
        title: "",
        link: ""
      }
    ]
  }

  return env.state.GOOGLE_SEARCH.organic_results.map((r) => {
    return { title: r.title, link: r.link, snippet: r.snippet };
  }).slice(0, 3);
}
```

### 映射结果以进行并行处理

```javascript
SEARCH_EXTRACT
```

### 使用 `WEB_CRAWL` 扫描页面

```javascript
{{SEARCH_RESULT_LOOP.link}}
```

### 使用 `Code Action` 提取内容

```javascript
// for each link, crawl its content and capped at 2000 bytes
_fun = (env) => {
  return {
    content: env.state.WEB_CRAWL_1.data ? env.state.WEB_CRAWL_1.data[0].results[0].text.slice(0, 2000) : "",
  };
} 
```

### 使用 LLM 分析内容

```json
{# Your prompt here, for example: 'Answer those question based on the following content.' #}
{# Begin your prompt below: #}

Given the following question:
"""
{{EXTRACT_QUESTION}}
"""

Extract the text from the following content relevant to the question and summarize it:
"""
{# {{GOOGLE_REFERENCES.content}} #}
{{SEARCH_RESULT_LOOP.snippet}}
"""

Extracted summarized content:
"""
```

### 使用 `Code Action` 提取内容

```javascript
_fun = (env) => {
  return {
    summary: env.state.MODEL_SUMMARIZE.completion.text.trim(),
    link: env.state.SEARCH_RESULT_LOOP.link
  };    
}
```

### 使用 `Code Action` 提取内容并生成提示

```javascript
const _example = (example) => {
  // prompt = `QUESTION: ${example.question}\n`;
  let prompt = "CONTENT:\n";
  prompt += '"""\n';
  example.forEach((d, i) => {
    if (i > 0) {
      prompt += '\n';
    }
    prompt += `link [${i}]: ${d.link}\n`;
    prompt += `content: ${d.summary.replaceAll('\n', ' ')}\n`;
  });
  prompt += '"""\n';
  console.log(prompt)
  return prompt;
}

_fun = (env) => {
  prompt = 'Given the following questions, reference links and associated content, create a final answer with references. If some of answer can be formatted in table format, format in table format. Answer should be accurate and concise. \n\n Never tell me "As a language model ..." or "As an artificial intelligence...", I already know you are a LLM. Just tell me the answer. \n\n';
  // env.state.EXAMPLES.forEach((e) => {
  // prompt += _example(e);
  // prompt += `FINAL:\n"""\n${e.final}\n"""\n`;
  // prompt += "\n";
  // });
  prompt += "QUESTION:" + env.state.EXTRACT_QUESTION + "\n";
  prompt += _example(env.state.FORMAT_SUMMARY);

  prompt += `FINAL:\n"""\n`;

  return { prompt }
}
```

### 将提示发送到 LLM

```json
{{FINAL_PROMPT.prompt}}
```

### 提取 `OUTPUT_STREAM` 作为输出

```json
{{FINAL_PROMPT.prompt}}
```
