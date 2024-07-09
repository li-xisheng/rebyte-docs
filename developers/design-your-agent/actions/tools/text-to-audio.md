# Text to Audio

This action allows you to convert text to audio in base64 format.

## Usage

* First, create a "text to audio" action in your agent.

<figure><img src="../../../../images/tta-1.png"></figure>

* Then, write the text you want to convert to audio in the action's editor.

<figure><img src="../../../../images/tta-2.png"></figure>

* Finally, run the agent and see the base64 audio result.

<figure><img src="../../../../images/tta-3.png"></figure>

## Output

The output is a object with two fields:"args" and "base64String". The "args" field contains the input text and the "base64String" field contains the base64 audio string.

```json
{
  "args": {
    "text": "Hello! Thank you for using ReByte!"
  },
  "base64String": "//UklGRiQAAABXQVZFZm10IBAAAAABAAEAgD4AAAB9AAACABAAZGF0YQAAAAAA..."
}
```

## Example Tool

[Here](https://rebyte.ai/p/21b2295005587a5375d8/callable/30fb713f62a5a2b562a3/editor#1) is a simple example of an agent that uses the "text to audio" action.