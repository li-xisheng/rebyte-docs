# Http Request Maker

### Description

This module supports making requests to specific URLs and retrieving results.


### Parameters
- Type
	- POST
	- GET
- Protocol
	- HTTP
	- HTTPS
- Address
	- Request address
	- Supports tera syntax, use {{ActionName}} to reference the output of the previous Action.
- Headers
	- Some URLs require sending specific headers with the request, usually to provide more metadata about the operation being performed.
	- You can define what needs to be sent, or you can get the content output from the previous Action using `env.state.actionname`

	```javascript
	_fun = (env) => {
	  return {
	  "Content-Type": "application/json"
	    }
    }
	```
- Body
	- Whenever you need to add or update structured data, you need to send body data with the request. For example, if you want to send a request to add a new customer to the database, you can include the details in the Body.
	- You can define what needs to be sent here, or you can get the content output from the previous Action. 

### Output
Depends on the specific request URL.