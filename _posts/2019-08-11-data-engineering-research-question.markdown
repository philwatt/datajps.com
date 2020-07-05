---
layout: post
title: Data Engineering Research Question
date: '2019-08-11 12:46:04'
tags:
- data-integration
- analytics
- architecture
- data-warehouse
- devops
- software-engineering
- integrated-data
---

TL;DR: I'm looking for some help to define my master's thesis research question. I'd really like you to give me some feedback through a short survey at:

[https://forms.gle/8iNv4Toaecb3fFtw8](https://forms.gle/8iNv4Toaecb3fFtw8)

Some of you know I'm working on a master's degree at the University of Melbourne. I'm in the home stretch now, and working on my final thesis. This requires a research question with the following characteristics:

- Clear
- Concise
- Complex
- Arguable

I'm most familiar with and interested in data and analytics as a domain, so this help to constrain the thinking. I've been talking to a number of people with data and analytics experience in my network that are also based in Melbourne. With their help, I've come up with the shortlist below, although I'm open to the idea that there may be better questions available. The questions I have so far are:

1. Why is it so hard to get real-time data into an analytics platform or data warehouse?
2. When should an organisation approach data integration / data engineering with an ETL Tool, and when is custom coding a better choice? (Definitions of both below)
3. Why is creating test data in a data integration / data engineering context so much more difficult than in a typical software engineering context?

I've laid out my current thinking for each question below. If you have some thoughts on the questions and how to answer them, please get in touch or complete the short survey &nbsp;

[https://forms.gle/8iNv4Toaecb3fFtw8](https://forms.gle/8iNv4Toaecb3fFtw8)

## **Why is it so hard to get real-time data into an analytics platform or data warehouse?** 

Many people I've interviewed &nbsp;cite this as a real problem. An example is as follows:

> Imagine an organisation with most systems run in their own on-premises data centre. The data warehouse development is managed by the Enterprise Finance division. The Marketing department wants to get real-time data into the data warehouse from the CRM system, which is owned by the Retail division. IT is responsible for the run and operation of the CRM system and the data warehouse. Operational (OPEX) costs for the CRM are borne by IT and licensing is by CPU sockets. The data is currently sent to the data warehouse overnight through a batch extract. The CRM system is otherwise idle overnight. Bonuses and promotions for IT executives are linked to annual OPEX cost reductions of 5%.

<figure class="kg-card kg-image-card kg-card-hascaption"><img src="/content/images/2019/08/BI--Data-Warehouse-and-Integrated-Data-Value---Unimelb-analytical-ecosystem-1.png" class="kg-image"><figcaption>Typical Analytics Ecosystem: based on a diagram by Humza Naseer, University of Melbourne 2019</figcaption></figure>

> Moving the extract to real-time will mean a small increase in the CPU requirement during the day. Turning off the overnight batch has no impact on the CPU requirement as the system must be sized based on peak CPU needs during the online day. This will attract an increase in OPEX costs for IT. IT executives will block this change for real-time data - even if Marketing provide additional OPEX funding because their bonuses are linked to cost reductions. Escalation may not help, as the first point where the escalation will meet a common manager could easily be the CEO - whose time will be very precious.

I hypothesise this is a result of organisational entropy, driven by misaligned incentives. I think I can model the behaviour and explore ways of altering pricing for the variables to change behaviour. The advantage of this question is that I can simulate the data and validate it through interviews. The downside of this question is the assumptions I need to make in the model - and can I get a model that gives a real insight into the problem? Kudos to [Leo Lopes at FICO](https://www.linkedin.com/in/leo-lopes/) who acted as a sounding board for developing the concept.

## **When should an organisation approach data integration / data engineering with an ETL Tool, and when is custom coding a better choice?**

There are two common approaches to data integration or data engineering. Firstly using an ETL tool with a graphical interface - sometimes a commercial tool like Informatica or even an open-source tool like NiFi, Talend or Node-RED. Secondly, custom coding using an open-source language like Java, Scala, Python or similar - often coupled with another open-source framework like Apache Airflow.

Given that data engineering can become very complex very quickly, which is the most productive choice over the lifecycle of the data assets under management?

For this question, I am considering using Compound Annual Growth Rate (CAGR) in the codebase over multiple years. This measure requires capturing data from source code control systems and has some dependencies and variables to control for. Kudos to [Chris Ottinger](https://www.linkedin.com/in/christopherottinger) at the Victorian Centre for Data Insights for suggesting CAGR as a metric.

Firstly, CAGR is usually measured against Lines Of Code (LOC) - but GUI based tools have binary objects which can't be counted this way. We can count the growth in objects for GUI approaches, and LOC for custom coding. This still gives us a comparable measure as both will resolve to a percentage growth. &nbsp;

Secondly, getting hold of the data. Assuming we can find a company to help, we need to get extracts from the codebase at various points over the last few years. This may be tricky to organise but I have sounded out one large enterprise already who seems willing to help.

Thirdly, it seems like many organisations are already moving away from ETL tools to custom coding. How much of this is driven by leveraging the available skills that organisations had already developed for Hadoop style infrastructure and how much is a conscious move away from ETL tooling? Hadoop style infrastructure, that is based on HDFS and closely coupling data storage with compute, looks like yesterday's technology. But many organisations have plenty of technical people who are comfortable with Java, Python, Scala or Spark programming paradigm and might view ETL tools as legacy or less productive.

Finally, and probably most importantly, there may be many factors that drive productivity including automated testing and continuous integration methods.

## **Why is creating test data in a data integration / data engineering context so much more difficult than in a typical software engineering context?**

In modern software engineering, automated testing is the default and often mandated through Test Driven Development (TDD). Code is modular, well defined and loosely coupled, meaning that unit tests can have clear boundaries and well known inputs and outputs. This constrains the complexity of testing the overall system.

In data engineering the situation can be more complex.

Let's start with the simplest situation - a Greenfield project with no existing data structures, reports or analytics. A blank canvass with a free choice on the architecture. Here it is possible to define discrete and reusable functions to acquire and load data, plus other functions like address or email validation. These can be reasonably easily validated. TDD can be applied from the beginning to all new functions and everything's groovy, right?

<figure class="kg-card kg-image-card kg-card-hascaption"><img src="/content/images/2019/08/BI--Data-Warehouse-and-Integrated-Data-Value---Examples-of-DI.png" class="kg-image"><figcaption>Example of Integrating Data</figcaption></figure>

Well, maybe not. You may still want to apply some conformity to the overall data, or apply a data model. I'm sceptical of the value of the late binding data (schema on need/read) approaches. It absolutely lowers the cost of acquiring data, but it just transfers that cost and multiplies it by the number of consumers of the data (each individual consumer must transform the data versus doing it once, centrally). There are many use cases where this makes perfect sense, [but as the number of consumers of the data grows, the economics flips](https://www.datajps.com/integrated-data-value/).

So you're conforming the data. Next thing you know someone has changed the range of values that are allowable in a critical field - but didn't bother telling you. They just made a procedural change in the call centre, and now you have data your system doesn't expect, and throws an error - in production. Or the test data you started with didn't contain all the possible combinations. Another error in production. You get the picture. I've spent 10 minutes writing this paragraph, and just scratching the surface on the unpredictability of data and analytics systems in Greenfield sites.

It's much worse if you have a brownfield site. The spaghetti code doesn't have unit tests defined. Or the test conditions have changed but no-one has documented them since the last time the code was changed. Everyone knows the platform has bad quality data, but no-one knows if the data issues are a bug in the system or a problem in the source. Often it's both. This also hides a staggering amount of technical debt in the platform because refactoring was never agreed by the business sponsor (I've paid for this code once, I'm not paying again...). Etc, etc.

Hmm... how do I model this? What data do I need to capture? No idea yet, but it could be fun finding out.

Righto - I know I'm labouring the point, but please spend a minute or two completing the survey at:

[https://forms.gle/8iNv4Toaecb3fFtw8](https://forms.gle/8iNv4Toaecb3fFtw8)

Thanks so much!

