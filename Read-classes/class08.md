# Class 08
## APIs
### API Design Best Practices
* **What does REST stand for?**
    REST is an architectural style for building distributed systems based on hypermedia. it is independent of any underlying protocol and is not necessarily tied to HTTP. 
* **REST APIs are designed around**
 *a resources*

* **What is an identifier of a resource? Give an example.**
 resource has an identifier, which is a URI that uniquely identifies that resource. For example, the URI for a particular customer order might be:
HTTP
https://adventure-works.com/orders/1

* **What are the most common HTTP verbs?**
 GET, POST, PUT, PATCH, and DELETE.

* **What should the URIs be based on?**
 based on nouns (the resource) and not verbs (the operations on the resource).

* **Give an example of a good URI.**
https://adventure-works.com/orders
* **What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?**
that requires consumer to make tremendous (subjective matter) amount of distinct API calls to get needed information about a resource,The more requests, the bigger the load


* **What status code does a successful GET request return?**
returns HTTP status code 200 (OK).
* **What status code does an unsuccessful GET request return?**
return 404 (Not Found).
* **What status code does a successful POST request return?**
Created
* **What status code does a successful DELETE request return?**
No Content

## Things I want to know more about
 resources