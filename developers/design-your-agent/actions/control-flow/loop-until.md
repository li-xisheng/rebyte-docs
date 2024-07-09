# Loop

This `Loop` action allows you to run actions repeatedly when the condition is true.

## Usage


* First, cretae a `Loop Until` action and you will see two "Loop" blocks being created.

<figure><img src="../../../../images/loop-2.png"></figure
  
* Fill in the condition in Javascript format. This function should return a boolean value.
  
* You can also set the maximum iteration count. If the iteration count reaches the maximum iteration count, the loop will stop even if the condition is still true.

<figure><img src="../../../../images/loop.png"></figure>

* Then, add the actions you want to run inside the loop.

* During the execution, the system will judge if the condition is true. If so, the actions between the two loop blocks will be executed until the condition is no longer true. Otherwise, the execution will jump to after the second loop block.

* **NOTE**: The "Loop" action's results are arrays. Make sure to use formats like `env.state.LOOP_1[0]` or `{{LOOP_1[0]}}`.


## Example Tool

* [Loop Until](https://rebyte.ai/p/21b2295005587a5375d8/callable/0029ec181e52a9fc2bc3/editor)
