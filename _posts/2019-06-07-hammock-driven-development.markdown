---
layout: post
title: Hammock Driven Development
date: '2019-06-07 06:04:27'
tags:
- architecture
- analytics
- software-engineering
---

I stumbled on a fascinating talk advocating the importance of really thinking through problems before committing to a solution. This applies not only to developing software but, maybe more importantly, designing the application. &nbsp;

<!--kg-card-begin: html--><iframe width="560" height="315" src="https://www.youtube.com/embed/f84n5oFoZBc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><!--kg-card-end: html-->

I was led here by a LinkedIn comment from a former colleague [Jamie Skipworth-Michel](https://www.linkedin.com/in/jamie-skipworth) pointing me to a [blog](https://blog.bradfieldcs.com/) from Oz Nova at Bradfield School of Computer Science saying '[You are not Google](https://blog.bradfieldcs.com/you-are-not-google-84912cf44afb)' (unless you are, of course) so you probably don't need the hyperscale solutions that they use.

I feel a little conflicted by the last post/point - at least from a headline perspective. It does not follow that because you are not operating at web-scale then &nbsp;you have nothing to learn from Google or Amazon, etc. - a conclusion you might otherwise reach from reading the article. But that is not really what Nova is saying - he's saying find out how much overlap _your_ situation has with the situation at Google/Amazon/LinkedIn or whoever when they came up with their cool tech (like Hadoop, Cassandra or others) - and _then_ _see how it could apply to your <u>specific</u> situation_. And _not_ the situation you wish you had...

A personal example of this approach is when I led the design of the architecture for the Whole of Victorian Government Analytics platform last year. We ended up using Azure SQL Database as the main data store for our relational data. Note a decision <u>not</u> to use Hadoop or other large scale analytics platforms, even if the user base was potentially very large.

Among all the choices this one doesn't scale to many terabytes or beyond - but that's OK right now as it will be a while before the core data gets to that point, but we had no reporting or data warehouse needs to manage high query concurrency - but we did want to minimise our management overheads which Azure SQL DB does really well. Each project can take a copy of the data, and manage their own performance contention without affecting others (a federated model where resources are spun up and down on demand - a bit like Snowflake in some ways).

You might say we could be storing up a lot of technical debt for the future, but we help guard against that by separating the application logic from the database - so we can easily swap the data layer in the future. And underwritten by automated testing to make that smoother also.

