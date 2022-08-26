# API FIRST EXCERCISE
## What is API FIRST

Is a concept that treats your API's as a first class citizen. It is standing to have consistent and reusable API's written in an API description language to stablish the contract.

There are some advantages about using this approach, but my favourite one is about reducing the feedback loop. Writing the API First, is useful to validate the design with any pair. Or even it is encouraging to you to make questions before jumping to the production codebase. Always to do changes in the design is going to be cheaper if they are detected at early stages.

## Readings

* [API First](https://swagger.io/resources/articles/adopting-an-api-first-approach/)
* [API First How To with Swagger + SpringBoot](https://easyitblog.info/posts/api-first-approach-with-swagger/)

## The Excercise

### Our Meetup Tracker

![Meetups!](https://cdn.iconscout.com/icon/free/png-256/meetup-5-739520.png)

Imagine you want to design an API in order to keep track of the events your comunity are organising since you're tired of paying to Google Meetup.

```
When an event is created, we have to define:

* Date and time (in the future, otherwise we could not create the event)
* Title and Description (only title is mandatory)
* Location (Locations are already saved in the system, currently they are Main Office, Cool Cowork and Remote
* Speaker
* Facilitator
```

For an already created event, people can join if they were already registered in our platform. Speakers and Facilitators must be registered as well

```
For registering a new person in our platform, the system needs the next info in advance:

* Name
* Last Name
* Email (must be unique in the system and for sure a valid email)
```

Once the event is passed is important to know if a person definitively went to the meetup, to measure how much absent people we have in our community. 

After some days, people who really attended to the meetup, could set how they liked the event, adding a score from 0 (they didn't like) to 5 (best event in the world!)

### Design the API in advance

### Go ahead for some Outside in TDD!
