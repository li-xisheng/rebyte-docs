## Planning

Planning is the process of thinking about the activities required to achieve a desired goal. If you ask the assistant to perform a task, the assistant will create a plan to achieve the goal. The plan is a sequence of tools that will be executed to achieve the goal.

Planning is intrinsically hard. People always cite the inability to do a good planning as a big pain point for agent reliability. In our system, we're not solving a multiple steps planning problem, at lease not for now. We're targeting to do small steps planning at one time, and achieve the final goal iteratively under the guidance of the user. 

We've tried different planning strategies, in our v3 planner, we use function calls to represent the planning steps. Planner is always a **Tool** in our system, you can find the source code here:

https://rebyte.ai/p/a8056c9a7bac76e20087/callable/e89617c3477fa850b05e/editor/design


In Production, planner uses gpt-4o, but we're working on switching to other models.


### Next Steps

* Allowing you to provide domain-specific knowledge to the planner, so that the planner can make better decisions.
* Allow you complete control over the planner, so you can write your own planner.

