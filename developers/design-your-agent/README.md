# Design Your Tool

## Mental Model of Tool Execution

* Tool contains a list of actions, for a single agent invocation, the actions will be executed in strict order. You can have multiple invocations of the same agent at the same time.
* All actions except 'THREAD' are stateless across invocations.
* 'THREAD' action is stateful across invocations, typically used to store the conversation history.
* Downstream actions can access the output of actions that are executed before them.

## Spec and Config
* Each action has a spec and a config.
* The difference between spec is immutable at runtime, while config is mutable at runtime, which means you can change the config of an action when calling this action, but you can not change the spec of an action at runtime.
* Action also contains a default config, if you don't provide a config when calling the action, the default config will be used.


## Action

### Action Name

* Action name must be uppercase, e.g. `INPUT`, `OUTPUT`, `SEND_EMAIL`. `_` is allowed in the action name.
* Action name must be unique in the agent.

