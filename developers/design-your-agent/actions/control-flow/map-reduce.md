# Map Reduce

The `Map Reduce` action allows you to map over an array and executes a sequence of actions in parallel. 

This is useful for doing multiple actions in parallel, such as scraping multiple web pages.

## Usage

* Add a `Map Reduce` action to your agent, and you will see two blocks with the same name ("MAP_REDUCE_1" for example) being added to the action.

* The action added between the two blocks will be executed in parallel for each element in the array.

<figure><img src="../../../../images/map-2.png"></figure>

* Set the following specifications for the `Map Reduce` action:

### Specification

<figure><img src="../../../../images/map.png"></figure>

**MapOver**

  * Choose a previous action and we will map over this action's output.
  * The output of the previous action must be an array. Also make sure the array is not empty.

**Repeat** 

* The value will specify the maximum iteration count
* If "repeat" value is not specified, then the iteration will stop when the array is exhausted. There is a hard limit of 64 iterations.
* If "repeat" value is specified, then the iteration will stop when the array is exhausted or the iteration count reaches the repeat value, whichever comes first.

### Output

* Each action inside map-reduce action will output an array of values.