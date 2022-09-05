# Class 12

## CRUD
![CRUD](/1_pJRJgw1Vj-1MjhtQFZAZRA.png)

### Status Codes Based On REST Methods
 
* **In your own words, describe what each group of status code represents:**

    **100's =** *Information responses*;they tell the client that the header part of the request has been received and the server will try to comply with a transmission demand of the client
    **200's =** *Successful responses*;they tell the client that its request was accepted
    **300's =** *Redirection messages*;they tell the client that the resource they are requesting isn’t available at the expected location anymore
    **400's =** *Client error responses*;they are all about invalid requests a client sent to a server.
    **500's =** *Server error responses*; they indicate problems with overwhelmed servers or unreachable servers behind proxies, but sometimes they can be directly related to client requests that trigger error exceptions on the server

* **What is a status code 202?** *Accepted* it tells the client that the request was valid, but its processing will finish sometime in the future
* **What is a status code 308?** *Permanent Redirect*;it tells the client to use another URL to access the resource and not use the current URL anymore.

* **What code would you use if an update didn't return data to a client?**
204 *No Content*
* **What code would you use if a resource used to exist but no longer does?**
410 *Gone*

* **What is the 'Forbidden' status code?**
it indicates that the server understands the request but refuses to authorize it

### Build A REST API With Node.js, Express, & MongoDB

* **Why do we need to pull our MongoDB database string out of our server and put it into our .env?**
becuase  we have MongoDB database string inside localhost , and when we deploy app we are going to use something that is not our localhost so we need to put it into .env file
* **What is middleware?**
middleware are functions that execute during the lifecycle of a request to the Express server
* **What does app.use(express.json()) do?**
 parses incoming JSON requests and puts the parsed data in req.
* **What does the /:id mean in a route?**
this means that this is a parameter that we can access by typing in request.pramas.id
* **What is the difference between PUT and PATCH?**
*PUT* is a method of modifying resource where the client sends data that updates the entire resource . *PATCH* is a method of modifying resources where the client sends partial data that is to be updated without modifying the entire data[1]
* **How do you make a default value in a schema?**
by making the value of 
```
parameterName: Date.now
```
* **What does a 500 error status code mean?**
it means that there is an error on your server 
* **What is the difference between a status 200 and a status 201?**
The 200 status code is by far the most common returned. It means, simply, that the request was received and understood and is being processed. A 201 status code indicates that a request was successful and as a result, a resource has been created[2]

### Things I want to know more about
  How to handle with JSON req and res

### References:
* [[1]](https://www.geeksforgeeks.org/difference-between-put-and-patch-request/#:~:text=PUT%20is%20a%20method%20of%20modifying%20resource%20where%20the%20client,without%20modifying%20the%20entire%20data.) 
* [[2]](https://aloneonahill.com/blog/http-status-codes#:~:text=Successful&text=The%20200%20status%20code%20is,understood%20and%20is%20being%20processed.&text=A%20201%20status%20code%20indicates,for%20example%20a%20new%20page).) 