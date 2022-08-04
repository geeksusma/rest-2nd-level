# rest-2nd-level

## Introduction

### REST

- What is REST?

REST is an acronym for REpresentational State Transfer and an architectural style for distributed hypermedia systems. 

- What is a REST API?

A Web API (or Web Service) conforming to the REST architectural style is a REST API.

- What is the architectural style then?

It is based on six principles:

#### Uniform Interface:

Rest is resources oriented, so identifying the right level of abstraction for the resources involved, also their interactions and having a good representation of those resources is crucial.

#### Client Server:

Clients and Servers can evolved isolated since the concerns are separated (but keeping on mind the interface must be respected) The main idea is to separate the user interface concerns (client) from the data storage concerns (server)

#### Staless:

The server can't store any session at their side (since if we do that, we are killing the scalability) so every request made to the server has to contain all the information to allow to the server execute the requested action properly.

So the session state needs to be keep at client side

#### Cacheable:

Retrieving resources should be cacheable. (GET)

#### Layered System:

In Rest it is fine to hold the API in a server A and then save the resources in a server B (and even having the security in a server C)

All the above constraints help you build a truly RESTful API, and you should follow them. Still, at times, you may find yourself violating one or two constraints. Do not worry; you are still making a RESTful API – but not “truly RESTful.”

### Richardson Maturity Model

![alt text](https://martinfowler.com/articles/images/richardsonMaturityModel/overview.png)

Is a way to measure how mature is your REST Api based on 4 models, from 0 to 4. I'd like to encourage this is not a standard. In fact, there is no standard defined to say if a REST Api is good enough or not. But the truth is, the Richardson Maturity Model was quickly adopted by the IT Industry, at least ot have "something to follow" to let you know you're doing well


#### Level 0:

If you have an API defined over the Https protocol to transfer data, then you are already in that level. It's free!

### Level 1:

Good abstraction level based on resources. Following the plural over the singular, and not including verbosity at any endpoint

Examples of good naming:

- /employees
- /departments
- /employees/9e0343b9-a873-4db7-813e-fdeb68305d3b/departments
- /candidates/search?name=jhon&page=1&offset=20

First endpoint can be use to create/update a single employee, or even to retrive all of them

Second endpoint is similar to the first one but based on departments

The third can be use to update the departments of a given employee. Also to retrieve the departments where the employee is added (if the key is found)

The last one is a search endpoint following the google semantic, it is retrieving the first page with only 20 candidates who are named as John

Examples of bad naming:

- /employee (not plural)
- /departments/create (verbosity is not allowed)
- /getEmployeeById (Please don't)
- /search?type=candidate&name=jhon&page=1&offset=20 (Avoid using flags, wrong abstraction level)

### Level 2:

Http Verbs and right usage of Http Status Code.

Since the endpoint does not allow be verbose, we have to use the Http Verbs to specify the kind of action we want to execute. In addition, is a good practice to choose the right Http Status Code to return if the action requested were succeeded or not.

- POST (Use POST only for creating new resources, please return 201) **This operation is not idempotent**
- GET (Use GET to retrieve data without changing the status of the server, please return 200, remember then it can be cached)
- PUT (Use PUT to update a whole existing resource in an idempotent way, please return 200)
- PATCH (Use PATCH to update partially an existing resource OR changing the state in a non idempotent way OR implement a command that is out from the REST convention OR many other reasons.. I just listed the most tipicals) **This operation should not be idempotent**
- DELETE (Use DELETE to remove a resource from the server, please return 200) **This operation is not idempotent**

As you notice is important to keep in mind the idempotency principle. Some operations must be idempotent by default, not others. If you are not familiar with idempotency, this is **a mathematical principle that is saying you'll always have the same result, no matter how many times you execute it**

