# 42
The answer to life, the universe, and everything.

## A short course on writing great software
Software is hard but is need not be that way there are but a few core things that can help us write great software and deliver excellent service to our internal clients.  These short sessions are designed to equip you with that knowledge, if you already know it then no harm in a refresher.  Each talk will be 40 minutes with 20 minutes allowed for Q&A.

## Schedule
[https://docs.google.com/spreadsheets/d/1-A4P29n5u_iYqExKBZoyZKW61sa0wr9i935lg80HR_I](https://docs.google.com/spreadsheets/d/1-A4P29n5u_iYqExKBZoyZKW61sa0wr9i935lg80HR_I)

## TODO
*   Schedule - Started google doc
*   Rooms - Meeting with Michael and Sara Tuesday
*   T-Shirts - Design complete
*   Stickers
*   Organise recording facilities - Hangouts live?

### Tracks
*   General
*   Soft skills
*   Software craftsmanship
*   Architecture

### Talks

#### 01 :: Managing upwards - Finding the balance between quality and delivery  
*Dan Knight*

#### 02 :: 23 Essential design patterns you will mostly never use
A look at the most common design patterns from the Gang of 4 design patterns book, summary of the most useful.  
*Jon Lim, Nic Jackson*

#### 03 :: Naming conventions and clean code
How code should read like a novel, a retrospective analysis of Bob Martins seminal work.  
*Jon Lim*

#### 04 :: Web 101, critical rendering path, speed and performance
How the web browser works and optimising the critical rendering path.
*Rob Jones*

#### 05 :: Full circle quality
Unit tests are not enough, in this session we will learn how to write good unit, integration, behavioural tests.  We will also look at how to implement service virtualisation to remove dependency.  
*Nic Jackson*

#### 06 :: All clients are idiots, or are they - Understanding others problems?
The primary objective of Agile "Everyone is doing the best they can", yet we often dismiss this becoming agitated and annoyed at the actions of others.  This session will teach how you can communicate to both your stake holders and within your team.  
*Dan Knight*
-- should this be merged into 01

#### 07 :: Container orchestration
To be announced.  
*Michael Hausenblas - Mesosphere*

#### 08 :: Package Oriented Design
You have learned the language and now you are ready to start building your product. Sounds easy but where do you begin? Go is not like other languages in the sense that you can’t organise your source code using folders. If you do, you are going to have problems. This is because each folder in your source tree represents a package. A self contained unit of compiled code. The better job you do in identifying the unique packages you need to solve the problem, the easier your projects will be to manage, support and grow over time. Developer productivity on the project will directly relate to how well you design your packages and their API. This has been my experience and this is what I will share with you in this talk. My best practices and guidelines to package oriented design.  
*William Kennedy - Arden Labs - Author of Go in Action*

#### 09 :: Practical Application Security
Covering topics such as secure application development, XSS, XRSF, Fuzzing and static code analysis.  
*Andrew Millar*

#### 10 :: Community Matters
In this talk you will learn why you should get involved with the community and teach others to code.  
*Eggya Chiquita*

#### 11 :: Easy setup - it is not ok to ask me to follow a 100 step process to compile your code
Why it is important to make your project easy to setup, in this talk you will learn some practical advice how you can use docker to create reproducible builds.  
*David Kelley*

#### 11 :: [Portable, painless project setup with Docker Compose](/11/README.md)
*David Kelley*

Setting up a project needs to be fast and most importantly, easy. Seriously, like, one `$> command`. This talk will cover the barriers and pitfalls of a difficult, complicated setup. As well as how setting up and using Docker Compose in a number of ways, will leave you feeling as fresh as a daisy when working with yours and other's projects.

#### 12 :: Making Code Fly: Load Testing Web Applications
"No battle plan survives contact with the enemy", they say. Likewise, popular web application often need optimisation when they encounter real World traffic. Being able to identify & fix performance bottlenecks in our running applications is a critical skill of any modern software engineer, and is a cornerstone of Site Reliability Engineering. In this talk I'll go through why performance is the job of a developer, how to test web application stacks, what tools exist to monitor production performance, how to identify the effect of bottlenecks (and their possible causes!). Finally, I'll talk about what options a developer can take to improve performance. This will be a whistle-stop tour but the extensive supporting notes will help you as you go about trying to conquer the World.
*Paul Robinson*

#### 13 :: Serverless
To be announced.  
*Danilo Poccia - Author of AWS Lambda in Action, Technical evangelist at Amazon*

#### 14 :: Architectural patterns for microservice development
This session explains the common patterns used in microservice development including asynchronous processing and event driven systems.  We will understand why Microservices has come into existence by examining some of the problems of the past.  
*Jonathan Coltman*

#### 15 :: Agile 101
What does it mean to be Agile? First we will take a look at the why the agile manifesto was set out and some of the common forms of Agile such as Scrum and Kanban.  Once we understand why we will look at how you can implement agile thinking into your everyday workflow.  
*Nic Jackson - Chris Caswell*

#### 16 :: Breaking down the monolith
Microservices patterns are awesome however we rarely find that we can develop on green-field applications and often face the trouble of integrating into an existing system.  This talk will teach you the principles of how to identify a seam to remove code from a monolith into a service as well as looking at how new functionality based in a microservice can be implemented.  
*Mazin Power*

#### 17 :: Event Driven development
A look at how we can use FaaS + Aggregate data stores, and event sourcing patterns.  
*Jon Coltman*

#### 18 :: All The 3D Maths You Will Ever Need
3D maths may look scary. But it's not. This talk will take you from the simplest possible building blocks to just about enough knowledge to build your own 3D pipeline. Give or take a bit.  
*Tony Green*

#### 19 :: Ethically Driven Development
To quote the President of Starfleet: "Just because you can do a thing, it does not mean that you should do that thing."  
*Rob Stearn*

#### 20 :: The Corporation of You, managing being managed as a developer
Management doesn't start above you, it starts with you. How you manage yourself is the only way you'll move forward.  
*Rob Stearn*

#### 21 :: Accessibility
*Sally Shepherd - Apple, MostGood Software*

#### 22 :: Classical Grounding
What things does Jon think you should have an understanding of  
*Jon Lim*

#### 23 :: Cross-Origin Resource Sharing (CORS). Why do we need it and how do we do it  
Making requests in your browser to other domains can be very useful, but also dangerous in terms of security. Cross-Origin Resource Sharing helps keeps our clients protected. We'll be looking at how it works in different use-cases and how to implement CORS safely. Having CORS enabled does not necessarily mean you are providing protection.  
*Chris Mckenzie*

#### 24 :: Writing Software Well: An introduction to DDD and CQRS
Software development is a relatively young industry, and many are still arguing about the best way to write complex applications well. Producing maintainable, adaptable and elegant software remains an elusive goal to many developers. In this talk I will provide an introduction to what many consider to be our best methodology yet: Domain-Driven Design. Building on the concepts of DDD, we'll discuss why MVC is a terrible pattern for non-trivial applications, and talk through an alternative pattern: Event sourcing and CQRS. By the end of this talk you will want to write better software, and have some idea of how to actually do it.
*Paul Robinson*

#### 25 :: How good dependency management can make your tests faster
We've all heard the buzzwords: SOLID, high cohesion, loose coupling, dependency inversion (and injection)... In this talk we'll get down to the real world and see how good use of some of these concepts can make our lives as developers easier. Because if there's something you can't escape, that's writing tests for your code. If you can write those tests in an easier way, and you can run them faster, you'll become a better developer.

#### 26 :: Give Go a go
Go programming language has been around for a little more than 7 years now, some have never tried it, some tried it and haven't actually start to appreciate it. In this talk, I want to help both group to understand what the language is and some of the common misunderstandings. You’d understand why the language is not “Go-ing” anywhere provided with how the industry has taken it to the heart. In addition of this, you’ll walk away knowing that the Go community is the best and you’ll be missing out if you don’t give Go a go.
*Eggya Chiquita*

#### 27 :: Data Science for Geeks
Data science is one of the biggest buzzwords of the past few years, but it has years of research and understanding behind it and has many practical applications. In this talk, I'll explain what data science is and how you can use it to do cool stuff. 
*Allan Whatmough*

#### 33 :: Afterparty
Drinks in the Shaftsbury
