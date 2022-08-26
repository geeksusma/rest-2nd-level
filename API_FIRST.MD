# API FIRST, MODELLING EXERCISE
## What is API FIRST

Is a concept that treats your API's as a first class citizen. It is standing to have consistent and reusable API's written in an API description language to Establish the contract.

There are some advantages about using this approach, but my favourite one is about reducing the feedback loop. Writing the API First, is useful to validate the design with any pair. Or even it is encouraging to you to make questions before jumping to the production codebase.
Is always cheaper, if you have to do changes, if they are detected at early stages.

## Readings

* [API First](https://swagger.io/resources/articles/adopting-an-api-first-approach/)
* [API First How To with Swagger + SpringBoot](https://easyitblog.info/posts/api-first-approach-with-swagger/)

## The Exercise

### Our Meetup Tracker

![Meetups!](https://cdn.iconscout.com/icon/free/png-256/meetup-5-739520.png)

Imagine you want to design an API in order to keep track of the events your community are organising since you're tired of paying to Google Meetup.

```
When an event is created, we have to define:

* Date and time (in the future, otherwise we could not create the event)
* Title and Description (only title is mandatory)
* Location (Locations are already saved in the system, currently they are Main Office, Cool Cowork and Remote
* Speaker
* Facilitator (is optional)
```

For an already created event, people can join if they were already registered in our platform. Speakers and Facilitators must be registered as well

```
For registering a new person in our platform, the system needs the next info in advance:

* Name
* Last Name
* Email (must be unique in the system and for sure a valid email)

All fields above are mandatories.
```

Bear in mind, an event is the past is closed for updates, so nobody could join as attendee.

Once the event is passed is important to know if a person definitively went to the meetup, to measure how much absent people we have in our community. 

After some days, people who really attended to the meetup, could set how they liked the event, adding a score from 0 (they didn't like) to 5 (Best event in the world!) To do that, they will receive a notification to their email.

Bear in mind, the people registered are so responsible, so if they know in advance they could not be able to attend, they can remove itself from the event. Even they can be removed from the platform as well.

Also is important to allow complex searching over the events. No matter if they passed or if they are set in the future, we'd like to be able to filter by:

```
* Date Range: From/To if To is empty then To=TODAY
* Location: Main Office, Cool Cowork or Remote
* Title: It must be a "contains" and no case sensitive
```

In addition, we'd like to receive from the search, some stats based on the people registered to the event:
```
* Title
* Date
* Location
* Speaker
* Facilitator
* Registered People
* Attendees
* Absent
```

Finally, we'd like to have an easy way to collect all the people who acted as speaker/facilitator, and how many times, the data should be as follows, no matter if it is a speaker/facilitator

```
* Name: Name + Lastname
* Events: Counting how many times the person acted as speaker/facilitator
```

### Design the API in advance

Please design an API in advance (you can use for example the [swagger editor](https://editor.swagger.io/) which later has tools to export the api to php, java...) in order to model the endpoints needed to cover the exercise.

* ℹ️ At this point, we only want to know:
  * How many endpoints do we need? How they are going to be named? are some of them idempotent, not? why?
  * What kind of HTTP Verbs we have to use
  * What are going to be the HTTP Status to represent, success or ko
  * Our Data Model to represent the resources

As you see, API First is encouraging to you to make questions at design time!

### Go ahead for some Outside in TDD!

Once you are happy with the API designed in the previous step, let's go a little bit further, and design the whole solution using Outside In TDD (From your API to the Datasource)

Swagger Editor has a tool to export an API First YML file to code
Also you can use a library like [RestAssured](https://rest-assured.io/) or [Cypress](https://circleci.com/blog/api-testing-with-cypress/)

ℹ️ Just one last thing, the datasource is up to you, if you want to have a real database running at backend side is ok. If you want to have just an in-memory implementation, it is also fine

:warning: Don't submit any PR to this repo! just fork it and do your implementation there ;)
