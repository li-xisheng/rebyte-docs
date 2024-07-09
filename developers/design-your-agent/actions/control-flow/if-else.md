# If Else

The `If Else` action allows you to run actions conditionally.

## Usage

* Add an `If Else` action to your agent, and you will see two blocks with the same name ("IF_ELSE_1" for example) being added to the action. 

<figure><img src="../../../../images/if.png"></figure>
  
* Fill in the condition in Javascript format. This function should return a boolean value.

<figure><img src="../../../../images/if-2.png"></figure
  
* During execution, the system will judge if the condition is true. If so, the actions between the first and the second `If_Else` block will be executed. Otherwise, the execution will jump to after the second `If_Else` block.

* * **NOTE**: The "If Else" action's results are arrays. Make sure to use formats like `env.state.LOOP_1[0]` or `{{LOOP_1[0]}}`.

## Example Tool

* [If Else Tool](https://rebyte.ai/p/21b2295005587a5375d8/callable/f6f55d6029c8a0aedd53/editor)
