---
layout: post
title: Newer may not be better
date: '2017-10-11 11:08:00'
tags:
- analytics
- data-warehouse
- cloud
---

Many of my clients are are experimenting with newer technologies to help them drive agility, innovate faster or lower costs of their data platforms. I fully support this ambition, and there are many great choices out there to help achieve this.

I often see the technology choices being made before the business requirements are fully understood – and more often than not jumping on a cool tech bandwagon. This honestly both puzzles and irritates me. Lack of business engagement is a well understood reason for IT project failure, and I can’t think of a decent reason why the trap is so often sprung. Any reason I do come top with should be mitigated or resolved with stakeholder management. If you can’t manage the stakeholders, you probably shouldn’t be trusted with delivering the project in the first place.

Deep breath. OK. A case in point.

One of my large clients wants to create an Enterprise Data Hub, servicing up to 10,000 users with access to hundreds of terabytes of reference and transactional data in three layers – raw, conformed and aggregated (star schema).

So far so good. There’s plenty of cool new ways to do this right? Well, kind of. Did you notice the 10,000 users? That’s going to drive an awful lot of users trying to get data simultaneously – either simply pulling data out or querying it. The trouble here is that my client picked a stack that has no track record of servicing this number of users with this sort of architecture anywhere in the world. But the tech is cool and new so that will be fine…

So we have the Appeal to Novelty Fallacy:

> Appeal to Novelty is a fallacy that occurs when it is assumed that something is better or correct simply because it is new. This sort of “reasoning” has the following form: 1. X is new. 2. Therefore X is correct or better. This sort of “reasoning” is fallacious because the novelty or newness of something does not automatically make it correct or better than something older. This is made quite obvious by the following example: Joe has proposed that 1+1 should now be equal to 3. When asked why people should accept this, he says that he just came up with the idea. Since it is newer than the idea that 1+1=2, it must be better.

> This sort of “reasoning” is appealing for many reasons. First, “western culture” includes a very powerful commitment to the notion that new things must be better than old things. Second, the notion of progress (which seems to have come, in part, from the notion of evolution) implies that newer things will be superior to older things. Third, media advertising often sends the message that newer must be better. Because of these three factors (and others) people often accept that a new thing (idea, product, concept, etc.) must be better because it is new. Hence, Novelty is a somewhat common fallacy, especially in advertising.

> It should not be assumed that old things must be better than new things (see the fallacy Appeal to Tradition) any more than it should be assumed that new things are better than old things.

> LaBossiere, Michael. 76 Fallacies (pp. 34-35). Kindle Edition.

By the way, I thoroughly recommend this book – it really helps understand any fallacies in your own reasoning as well as proving clarity into other peoples arguments.

Old is not better than new. New is not better than old. There is a fit based on _need_. So here is a small, &nbsp;inexhaustive list of things to consider when moving to that new shiny tech for your data platform:

1. Get the business involved straightaway and make sure they support the vision. &nbsp;The principal use cases (user stories, epics, themes) should be sketched out with the business so you can line up the solution with the business needs
2. Defining the workload is a crucially important step. Only then you can define the architecture needed to support the workload. Do not neglect concurrency when evaluating tools and architecture. Defining a solution or architecture for 10-100 users is a very different requirement for 1000+ users. Many new data servicing technologies are poor at concurrency which can end up with a poor user experience and/or exponential increases on costs.
3. How can you govern the system? How will the solution cope with change over time? What do you do if users, stakeholders or customers disagree with the stuff coming in or out of the platform?
4. Make sure the evaluation includes a POC which rigourously tests against _your own real world_ requirements
