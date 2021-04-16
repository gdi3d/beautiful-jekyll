---
layout: post
published: true
title: Ya!Meeting On-Demand Jitsi Meet Private Servers for videoconferences
date: '2020-04-28'
subtitle: Ya!Meeting.com My new side project to provide Jitsi Meet Private Servers On Demand for every videconference meeting
category: Posts
tags: sideproject
bigimg: /img/yameeting-blog-cover.jpg
---
I love [Jitsi Meet](https://jitsi.org/jitsi-meet/) and roughly one year ago I decided to kick off a new side project that allowed me to launch my own private servers, on-demand, for every videoconference meeting with my clients, friends, and team.

The application it's called [Ya!Meeting](https://www.yameeting.com/) and it's an orchestration service that launches and installs Jitsi Meet on a new VM on the cloud, and when the meeting is over the server gets deleted.

It's quite easy to create a new meeting, you type in the name of the meeting, choose how many participants (to determine the size of the VM), the duration (to schedule the termination time), the location of the attendees (to deploy the VM in a specific region) and the email address of the attendees to notify them with the date, time and link to the meeting.

You can read more about it in the [FAQ section](https://www.yameeting.com/#faq)

The cost for a meeting is quite low, for ex.: Up to 6 people, for 3 hours is just **USD 0.06**

I also offer a free meeting just like [Jitsi Meet](https://meet.jit.si/) but the server running this free meeting gets deleted and replaced by a new one at least once a week.

I'm currently working on allowing the users to deploy on their own cloud accounts like Digital Ocean, AWS, GCP, Azure and provide their own SSL certificate.

*Photo Credits: [https://www.pexels.com/@julia-m-cameron](https://www.pexels.com/@julia-m-cameron)*
