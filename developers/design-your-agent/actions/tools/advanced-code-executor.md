# Advanced Code Executor

This action allows you to execute Deno code in your agent.

## Usage 

* First, create a "code interpreter" action in your agent.

<figure><img src="../../../../images/acode-1.png"></figure>

* Then, you can write your code in the action's editor.
* NOTE: In this action, we only support Typescript and Javascript code.

<figure><img src="../../../../images/acode-2.png"></figure>

* Finally, run the agent and see the result.

<figure><img src="../../../../images/acode-3.png"></figure>

## Output

* The output of the code will be a json object, the output is the code's execution result, the status_code is 0 if the code executed successfully, and the error field is empty. 
* If the code execution fails, the status_code will be the corresponding error code and the error field will contain the error message.

```json
{
  "status_code":0,
  "output":"Hello, Deno!",
  "error:"
}

```json
{
  "status_code":0,
  "output":"Hello, Deno!",
  "error:"
}
```

## Example Tool

[Here](https://rebyte.ai/p/21b2295005587a5375d8/callable/2f9c66ce2d576e5dc181/editor) is a simple example of an agent that uses the "Deno code executor" action.

