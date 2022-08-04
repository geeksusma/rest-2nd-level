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

