---
layout: post
title: Why was that so @#&*ing hard?
date: '2019-05-31 02:37:52'
tags:
- cloud
- software-engineering
---

I've been pretty quiet on this blog for a long time. Sorry about that. A large part of it was because my blog website was very, very unreliable.

I kicked this site off in late 2017 using Wordpress. About a year later I migrated to a Bitnami AMI (Amazon Machine Image - I'm hosting this on AWS) to reduce the overhead of running two servers and keep admin low by using a standard image. Traffic is low and I wanted to manage costs better.

At this point you might point out that I could easily run this platform in a fault-tolerant highly-available manner. Yes that's true. But it requires spinning up more infrastructure than I wanted to manage - and pay for truth be told. Meanwhile, my new instance was up and down more often than the gate at a level crossing. The server logs were unhelpful and I started to enlist the support of Wordpress plugins to help. These revealed little of help.

Six months later - with only part-time effort on my behalf - I gave up and decided I needed a static website instead. A quick Google search revealed Jekyll as the hot favourite, and looked a good choice with some easy looking migration options.

But installing Jekyll was also hard. Getting the correct version of Ruby installed was tricky to start with, and then there appeared to be conflicts with the Jekyll installer even then. After a few weeks more of part time effort, I changed course and looked at Ghost. Bitnami also had a ready built Ghost AMI, which I've customised and now have my own AMI version - immutable, ready to go infrastructure.

I could still move to high-availability, but for now I've got a wheel that works. Here I am with a simpler, more secure and more robust site. Content at last (for now…)

That's my excuse for not writing much here recently. That and the part-time Master's degree I'm doing. Maybe I'll write more here more frequently...

