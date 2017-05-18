# System Design

The basic system design interview problem is an open ended conversational exercise where the interviewee is given a complex system to design based on a simple and/or vague prompt. Often this comes in the form of a cloning a known service, e.g.: Describe how you would build Instagram, or Twitter. While the nature of it is more open ended than an algorithm problem, your systematic approach to the problem is what is being judged.

Generally speaking it’s a backend-ish type problem and therefore as a candidate for an entry-level iOS position you might not be asked a system design question. However, you might. Or, if this type of question is posed of you it would focus on the structure of the app alone, or only as far as the app can “see” of the rest of the system, namely the APIs it would need to function.

## Client/Server Architecture

<details>
  <summary>What is client/server architecture?</summary>
It's a pattern used to share work between a centralized and usually more powerful system 
and a number of 
</details>

<details>
<summary>Who is the client?</summary>
iPhone
</details>

<details>
<summary>Who is the server?</summary>
Server(s) on the Internet.
</details>

<details>
<summary>How do they communicate?</summary>
Almost always the HTTP protocol 
</details>

Draw the high level architecture

Justify your ideas

"system design questions will also most likely be weakly defined.” 

The very first thing you should do with any system design question is to clarify the system's constraints and to identify what use cases the system needs to satisfy.

## Draw diagrams whenever possible

Start with a diagram and refine and optimize it. Flesh it out with text based calculations and data models.

Get familiar with common approaches. Don’t be afraid of being unoriginal. It’s how you apply known patterns and perhaps make small optimizations and customizations that will show you understand both the pattern and the specifics of the problem.

[Basic Server Diagram]

[Basic Schema]

When we look at SQL we’ll look at how relational databases work and specifically for this problem how they communicate the modeling of a problem by the fields and relationships they have and how they anticipate queries and usage patterns by the indexes they define. It’s a powerful shorthand for expressing ideas even if a SQL database won’t be employed.

This will be more in the form of an app

Example
Favorites in comic chameleon

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

Web hosting solutions like AWS, Firebase, Fieldbook is a good example of how an iOS developer might still need to know how to choose or at least use that system.

### Vertical Scaling
More CPU, more disk, there are “real world constraints”
Multiple cores and parallelism 

### Horizontal Scaling
Trade price for number requires rearchitecting

What’s expensive?
Writing to disk
The Network
And what writes to disk and goes to network?
Disks vs SSD

## Everything is a tradeoff

This is one of the most fundamental concepts in system design.

Don't skip steps, don't make assumptions, start broad and go deep when asked.

You first build a high-level architecture by identifying the constraints and use cases, sketching up the major components and the relationships between them, and thinking about the system's bottlenecks. You then apply the right scalability patterns that will take care of these bottlenecks in the context of the system's constraints.

Don’t fall prey to early optimization

## Problems
1. Image store has upload limits imposed upon it 
2. A service is rate limited


Progress from 
* one machine 
* two machines
* n-frontends + load balancer
* proxies in between load balancer and front ends

## Exercise: make IDs across multiple back ends
First discuss the issues.
* uniqueness
* speed 
* reliability
* sortability
* size

https://engineering.instagram.com/sharding-ids-at-instagram-1cf5a71e5a5c

##b Calculations

Ask and make rough estimates of the scale of the system. How many users? How many operations per user? Which operations are read-only and which are writes? Does data need to be updated? A Facebook comment it can be edited but a Tweet cannot. No right or wrong, just decisions to be made.

social graph
nodes - users
edges - follows

consider numbers

Comic Chameleon
favorites (combinatorial) 

Handling user requests
numerically break down the avg. req. per second

load balancer
forward proxy
web server
database

APIs are familiar to us so we might be asked to design one

GET /api/user - read
POST /api/action - write

## Front End/Client/iOS Architecture

Dependency Management (Cocoapods)

Storage

Networking

Interface

MVVM
The view controller doesn’t need to know about web service calls, Core Data, model objects, etc.
http://www.sprynthesis.com/2014/12/06/reactivecocoa-mvvm-introduction/

Inversion of Control
Dependency Injection

The “separation of concerns” is a popular phrase worth getting familiar with. It encompasses refactoring but keeps the implication of for the purpose of keeping things decoupled.

https://softwareengineering.stackexchange.com/questions/205681/why-is-inversion-of-control-named-that-way

This lesson lifted heavily from https://www.hiredintech.com/classrooms/system-design/lesson/72 and its links. A deep dive into these would yield rewards both in interviews and in practice.
