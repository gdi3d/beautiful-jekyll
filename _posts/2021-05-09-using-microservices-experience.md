---
layout: post
published: true
title: Yes! Use microservices and ask 'why are you like this?' afterward 😑
date: 2021-05-09
subtitle: Sharing my experience on using microservices the wrong way
category: Posts
tags: microservices development
bigimg: /img/microservices-experience.jpg
share-img: /img/share-microservices-experience.jpg
---

> TL;DR It's a good idea to use microservices for a team of three or four people that only handles one or two microservices. Otherwise, stay away!

# Falling in love with Microservices 🥰

I started using the microservice architecture in 2015 when I had to refactory a medium-size Django app into pieces. Since then I have been using microservices for both work and personal projects non-stop.

At first glance microservices are great, it looks like you get a lot of benefits and it makes you think harder about every component of your application.

> Microservices - also known as the microservice architecture - is an architectural style that structures an application as a collection of services that are:

> Highly maintainable and testable  
> Loosely coupled  
> Independently deployable  
> Organized around business capabilities  
> Owned by a small team  
> 
> source: [https://microservices.io/](https://microservices.io/)

I was very happy with having my multiple repos, big docker-compose.yml files, multiples databases, stitching everything together, and watch my software work, or kind of. But that excitement went away when I had to keep everything working and updating things.

# When reality kicks in 😕

Now, after 6 years of experience, I've concluded that **microservices are not a good idea when you have a team of ten or fewer people and more than three or four microservices**. 

In that scenario, your development cycle will suffer and things will become tedious and more time expensive.

The main issue is not the microservices architecture itself, but rather the number of tools, knowledge, and preparation that the team needs have to be able to work properly.

In my experience, the team that I lead experienced the following issues when dealing with microservices:

- Upgrading frameworks versions was hard because we had to do it for every microservice, build, and deploy.
- We had a few libraries that were common for all microservices. Every time we discovered a bug or decided to change something, we had to apply that change to every microservice.
- Changes are part of the product life cycle, and sometimes those changes affected more than one microservice.
- Debugging was harder because the data flow through applications.
- Individual database schema for every microservice and restricted access to them forced us to use multiple microservices to be called to obtain a dataset
- Creating and maintaining a small dump of all databases for dev and QA purposes was HARD!

Today I prefer going with the traditional monolithic architecture, but making sure that my design will allow me to switch to microservices easily.

As a conclusion, I'll (try to) get back to monolithic as a starting point and move to microservices when the team size is large enough and the correlation between team size and microservices is adequate.

Another solution is to create microservices for a small part of the application that could benefit from it.

> Fun fact: Although I say this, I did use microservices on my recent side project. Maybe I'm hooked up and need counseling 😂