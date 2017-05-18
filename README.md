# System Design

## Resources
> This lesson lifted heavily from https://www.hiredintech.com/classrooms/system-design/lesson/72 and its links. 
> A deep dive into these would yield rewards both in interviews and in practice.
* https://www.hiredintech.com/classrooms/system-design/lesson/72
* http://highscalability.com/start-here/ 


## Introduction 
The basic system design interview problem is an open ended conversational exercise where the interviewee is given a complex system to design based on a simple and/or vague prompt. Often this comes in the form of a cloning a known service, e.g.: Describe how you would build Instagram, or Twitter. While the nature of it is more open ended than an algorithm problem, your systematic approach to the problem is what is being judged.

Generally speaking it’s a backend-ish type problem and therefore as a candidate for an entry-level iOS position you might not be asked a system design question. However, you might. Or, if this type of question is posed of you it would focus on the structure of the app alone, or only as far as the app can “see” of the rest of the system, namely the APIs it would need to function.

### Why System Design?

Apart from the two flavors of interview question mentioned above you might actually want to design a system,
either as a member of a team or on a personal project.

## Client-Server Architecture

Since the majority of systems are partially or wholly client-server based, let's be sure we
define it.

<details>
  <summary>What is client/server architecture?</summary>
It's a pattern used to share data and processing between a centralized and usually more powerful system 
and a number of other devices.
</details>

<details>
<summary>Who is the client?</summary>
Computers, phones: in short the app.
</details>

<details>
<summary>Who is the server?</summary>
The server is the centralized resource on the Internet. In the literal sense it is a computer
but more broadly it's any arrangement of computers, routers, switches that the client 
communicates with.
</details>

<details>
<summary>How do they communicate?</summary>
Almost always the HTTP protocol. By API endpoint is how we've connected our apps to servers.
</details>


## Draw diagrams whenever possible

Start with a diagram and refine and optimize it. Flesh it out with text based calculations and data models.

Get familiar with common approaches. Don’t be afraid of being unoriginal. It’s how you apply known patterns and perhaps make small optimizations and customizations that will show you understand both the pattern and the specifics of the problem.

![Diagrams](https://www.hiredintech.com/lecture_materials/twitter_problem_system_design.png)

When we look at SQL we’ll look at how relational databases work and specifically for this problem how they communicate the modeling of a problem by the fields and relationships they have and how they anticipate queries and usage patterns by the indexes they define. It’s a powerful shorthand for expressing ideas even if a SQL database won’t be employed.

The very first thing you should do with any system design question is to clarify the  
constraints and identify what use cases the system needs to satisfy.

Don't fall prey to early optimization.

## Use Cases

There is no general answer for this. This is where we define and clarify the functionality of
the app in terms of the individual interactions with it (use cases). Similar to algorithm
design it's wise to start with the 90% case(s) and then consider the edge cases. At the same
time you don't want to dive too deep into a design until you do look at those edge cases. The 
Hired in Tech article mentions a Twitter clone where there is an expected average usage
but there are known spikes for popular content. So, first look at the common cases, propose a
design and test it against edge cases and refine.


## Everything is a tradeoff

This is one of the most fundamental concepts in system design.
> Don't skip steps, don't make assumptions, start broad and go deep when asked.

## Steps

1. Constraints and use cases
2. Abstract Design
3. Understanding bottlenecks
Bottlenecks and single points of failure are important topics in CS because they can undermine the quality of the whole system — a chain is only as strong as its weakest link
4. Scaling your abstract design
    1. Scope the problem: Don't make assumptions; Ask questions; Understand the constraints and use cases.
    2. Sketch up an abstract design that illustrates the basic components of the system and the relationships between them.
    3. Think about the bottlenecks these components face when the system scales.
    4. Address these bottlenecks by using the fundamentals principles of scalable system design.

You first build a high-level architecture by identifying the constraints and use cases, sketching up the major components and the relationships between them, and thinking about the system's bottlenecks. You then apply the right scalability patterns that will take care of these bottlenecks in the context of the system's constraints.

### Vertical Scaling

* Add More CPU (faster CPU or more cores)
* Add more disk
* there are “real world constraints”

### Horizontal Scaling

* Trade one big machine (vertical scale) price for many 
* requires rearchitecting

What’s expensive?
  * CPU
  * Writing to disk
  * The network (server-to server: external services, e.g. oauth, or database)
  * And what operations write to disk and goes to network?
  * Disks vs SSD

### Load balancing

The means by which horizontal scaling is accomplished, on the network level.

### Database replication

* Databases can be replicated for "hot failover"
* Or Master - Slave if read / write is exploitable

### Database partitioning

How do we distribute the "single source of truth"?

* partitioning/sharding

## Exercise: make IDs across multiple back ends
First discuss the issues.

* uniqueness
* speed 
* reliability
* sortability
* size

Instagram's ID generation approach
https://engineering.instagram.com/sharding-ids-at-instagram-1cf5a71e5a5c

## Calculations

Ask and make rough estimates of the scale of the system. How many users? How many operations per user? Which operations are read-only and which are writes? Does data need to be updated? A Facebook comment it can be edited but a Tweet cannot. No right or wrong, just decisions to be made.

social graph
nodes - users
edges - follows

## API

APIs are familiar to us so we might be asked to design one

GET /api/user - read
POST /api/action - write

## Front End/Client/iOS Architecture

* Dependency Management (Cocoapods)
* Storage
* Networking
* Interface
* MVC
* MVVM

The view controller doesn’t need to know about web service calls, Core Data, model objects, etc.
http://www.sprynthesis.com/2014/12/06/reactivecocoa-mvvm-introduction/

Inversion of Control
Dependency Injection

The “separation of concerns” is a popular phrase worth getting familiar with. It encompasses refactoring but keeps the implication of for the purpose of keeping things decoupled.

https://softwareengineering.stackexchange.com/questions/205681/why-is-inversion-of-control-named-that-way

## Exercises

1. Design an image upload system where the image store has disk and bandwidth limits imposed upon it 
2. Design a news reader app where the service is rate limited

## Case Study - Comic Chameleon

### Back end
* AWS
* EC2 (Linux server)
* Cloudfront (cache)
* RDS (dual zone)

### Front end: iOS App
* Core Data for episode info and read history
* NSUserDefaults for onboarding flag
* MVC
* UI: Storyboards and nibs
* Web page for News and the Timeline (hybrid)

# Problem

> Custom Favorites in combination
