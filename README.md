# duochem
Template for a chemistry course duolingo mode.

We are using Scala (Functional Programming Language) for the Session Generator (the Session Generator manages the exercises the user sees and their order).

We decided then to port the codebase to Scala, a statically-typed functional programming language built on top of the Java Virtual Machine (which means you can use existing Java libraries). Scala has been widely used in "big data" applications, which have some of the same high complexity characteristics as Session Generator. It seemed like a good fit.

Reasons for using Scala
-Improved latency.
-Increased engine uptime.

One of the main concerns with Scala is its steep learning curve. However, in highly complex systems where the learning curve of the system is steeper than that of the programming language itself, improving readability and maintainability has a higher priority. In this regard, Scala does a good job, as we’ll present in the next section.

Course data (which needs more processing steps but is shared among users in the same course) is processed off-line and serialized into files in AWS S3, Amazon’s cloud storage service. So we only need to fetch these files from a stable and cheap data store, and cache them. //Change cloud to Azure!!

The user data we leverage for personalization (which requires fewer processing steps but can’t be shared) is fetched through the API servers, and then injected into the request sent to Session Generator.

The stack we chose uses Finatra as the HTTP server, with Guice for the dependency injection framework and Mockito for the testing framework.

This stack is deployed on AWS Elastic Beanstalk, Amazon’s orchestration service which automatically handles rolling deployment, load balancing, autoscaling, monitoring, and so on.

100% Kotlin


Duolingo has an important mission: to develop the best education in the world, and make it universally available.

