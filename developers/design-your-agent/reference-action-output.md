# There are two ways to reference previous actions' output, depending on the action type.

## Plain javascript syntax

Use the `env.state` object to access the output of previous actions. For example, if you want to access the output of the `INPUT` action, you can use `env.state.INPUT`.

```javascript   
const llmOutput = env.state.LLM_CALL;
```

This syntax is used in all fields that support javascript.

## Prompt template language

This syntax is used in other fields that support the prompt template language. You can use the `{{}}` syntax to access the output of previous actions. For example, if you want to access the output of the `INPUT` action, you can use `{{INPUT}}`.

for example, if you want to access the first message of the `INPUT` action, you can use `{{INPUT.messages[0].content}}`.
```markup
{{INPUT.messages[0].content}}
```

The Prompt Template Language is a simple language that allows you to create a prompt template that can be used to generate prompts for your LLM models. The Prompt Template Language is a subset of the [Jinja](https://jinja.palletsprojects.com/en/3.1.x/) templating language. Here are some examples of how you can use the Prompt Template Language, for more information on the syntax, see the [Jinja documentation](https://jinja.palletsprojects.com/en/3.1.x/templates/).

\{\{ and \}\} for expressions

```
{{ 1 + 1 }}
```

For referencing variables

```
{{ variable_name }}
```

for statements

```markup

{% raw %}
{% for i in range(10) %}

    {{ i }}

{% endfor %}
{% endraw %}

```

{# and #} for comments To comment out part of the template, wrap it in {# #}. Anything in between those tags will not be rendered.

```
{# This is a comment #}
```

Construct and attributes can be accessed by using the dot (.) like \{\{ product.name \}\}. Specific members of an array or tuple are accessed by using the .i notation, where i is a zero-based index. In dot notation variable can not be used after the dot (.).

```
{{ product.name }}
{{ product[0] }}
```

Tests can be used against an expression to check some condition on it and are made in if blocks using the is keyword. For example, you would write the following to test if an expression is odd:

```markup

{% raw %}
{% if number is odd %}

    This is an odd number

{% endif %}
{% endraw %}

```

Tests can also be negated:

```

{% raw %}
{% if number is not odd %}

    This is not an odd number

{% endif %}
{% endraw %}
```
