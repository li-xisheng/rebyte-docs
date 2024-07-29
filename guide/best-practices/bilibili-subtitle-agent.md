# Bilibili 字幕助手

帮助您获取 bilibili 字幕并总结内容。

### 在 `Datasets` 中设置测试数据

```json
[
  {
    "role": "user",
    "content": "BV1Lu411J7Z8"
  }
]
```

### 从 `Code Action` 中提取内容

```js
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
  return env.state.INPUT.messages.slice(-1)[0].content
}
```

### 使用 LLM 处理用户的输入

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
 return env.state.GET_BV.completion.text
}
```

### 从 `Code Action` 中提取内容

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
 return env.state.GET_BV.completion.text
}
```

### 使用 `Http Request Maker` 请求 CID

```javascript
api.bilibili.com/x/player/pagelist?bvid={{BV}}
```

### 从 `Code Action` 中提取内容

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
 return env.state.GET_CID.body.data[0].cid
}
```

### 使用 `Http Request Maker` 请求字幕的 URL

```javascript
api.bilibili.com/x/player/v2?bvid={{BV}}&cid={{CID}}
```

### 从 `Code Action` 中提取内容

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
  // const data = JSON.stringify(env.state.GET_URL.body)
  // const regex = /<subtitle>(.*?)<\/subtitle>/;
  // const match = data.match(regex);
  // const subtitleURL = match ? match[1] : "";
  // const obj = subtitleURL.replace(new RegExp("\\\\\"","gm"),"\"")
  // const result = JSON.parse(obj)['subtitles'][0]['subtitle_url'].replace("//", "")
  const url = env.state.GET_URL.body.data.subtitle.subtitles[0].subtitle_url
  const result = url.replace(/\/\//g, "");
  return result
}
```

### 使用 `Http Request Maker` 请求字幕

```javascript
{{GET_CC_URL}}
```

### 从 `Code Action` 中提取内容

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
  let arr = []
  for(let i in env.state.GET_CC.body.body) {
    arr.push(env.state.GET_CC.body.body[i].content)
  }
 return arr.join(',')
}
```

### 将字幕发送到 LLM 进行总结

```json
{% if GET_URL.body.data.subtitle.subtitles[0].subtitle_url == "" %}
please reply to me with the phrase: "I apologize for being unable to retrieve content from the URL you provided. Please verify the correctness of the web address"

{% else %}
You are an AI with advanced comprehension and summarization skills. Your task is to read the following passage and provide a concise, clear summary that captures the main points and key details. 

Passage: 
{{CC}}

Please provide a summary of the above passage and respond to me in Chinese.

{% endif %}
```

### 从 `Code Action` 中提取内容

```javascript
_fun = (env) => {
  // use `env.state.Action_NAME` to refer output from previous Actions.
 return {
   role: "assistant",
   content: env.state.OUTPUT_STREAM.completion.text,
   retrievals: env.state.RETRIEVALS
 }
}
```

### 输出最终结果
