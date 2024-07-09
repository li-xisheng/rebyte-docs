# You.com search

With this "You.com" search action, you can go and search anything and you will get your results in seconds!

<figure><img src="../../../../images/you-1.png" /></figure>

## Usage


* First add a "You.com" search action with the plus signs.

<figure><img src="../../../../images/you-2.1.png" /></figure>

* Choose the "You.com search" action.

<figure><img src="../../../../images/you-2.2.png" /></figure>

* There are some parameters you can set.
  * query: the search query.
  * num_web_results: the number of web results you want to get.
  * offset: the offset of the search results. If the offset is 0, the first result will be the first result of the search results. If the offset is 10, the first result will be the 11th result of the search results.
  * country: the country code. For example, "US" for United States.
    * country list include:'AR', 'AU', 'AT', 'BE', 'BR', 'CA', 'CL', 'DK', 'FI', 'FR', 'DE', 'HK', 'IN', 'ID', 'IT', 'JP', 'KR', 'MY', 'MX', 'NL', 'NZ', 'NO', 'CN', 'PL', 'PT', 'PH', 'RU', 'SA', 'ZA', 'ES', 'SE', 'CH', 'TW', 'TR', 'GB', 'US'.
  * safesearch: the safe search mode, it can be "strict", "moderate" or "off".

<figure><img src="../../../../images/you-3.png" /></figure>

* Run the agent and see the search results.

### Output

<figure><img src="../../../../images/you-4.png" /></figure>

* The output is a bit complex, it's a JSON object with two fields:"hits" and "latency". 

* The search results are in the "hits" field, it's an array with 10 most related search results.

## Example Tool

* To see and use this action, please check the example agent:[You.com Search](https://rebyte.ai/p/21b2295005587a5375d8/callable/b6e67fc59579d6304fef/editor).
