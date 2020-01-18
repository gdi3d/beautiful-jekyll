---
layout: post
published: false
title: ''
---
Title: Creating a basic development environment
Date: 2015-09-18 20:00
Category: Posts
Tags: tips

Recently I was asked to help out and organize a small group of programmers to improve their (non-existent) workflow.

This is a small document that I wrote for them

# Overview

1. [Use Git](#use-git)
1. [Create a new instance and deploy GitLab on it](#deploy-gitlab)
1. [Give your developers a small/medium size server to deploy they work and test it](#devel-server)
1. [Implement Agile method using scrum](#agile-scrum)
1. [Full workflow example](#example)

<a id="use-git"></a>
## Use Git

Git definition:

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
 
Translation: It allow you to keep a **history** of the changes in your code over time and allows multiple developers to work on the same project without worring about screwing things up badly.

You can try it at [https://try.github.io/levels/1/challenges/1](https://try.github.io/levels/1/challenges/1)

You should also check: [https://www.atlassian.com/git/tutorials/setting-up-a-repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository) to get started with **git**

[Download Git](https://git-scm.com/)

#### Recommended workflow

Always have at least two main branches:

- **Master** will hold the lastest stable version of your project  
- **Devel** will hold all the new features for the next version of your project

Developers shouldn't make changes directly into **devel** nor **master**

Every time a developer need to work on a **feature** or **bug** he will create a new branch using **devel** or **master** as starting point.

**Should use devel when**: new feature or bugfix. 

**Should use master when**: hotfix.

This new branch will have the following pattern:

- For features: **feature/issue-\#**
- For bugs: **bug/issue-\#**

Where \# will be the issue number on gitlab.

A similar workflow can be found at: [http://nvie.com/posts/a-successful-git-branching-model/](http://nvie.com/posts/a-successful-git-branching-model/)

<a id="deploy-gitlab"></a>
## Create a new instance and deploy GitLab

GitLab is like github, but self hosted. This includes: git repository management, code reviews, issue tracking, wikis, user management, milestones, etc.

You will use this for managing your project.

Make sure to use labels on your tickets such as bug, discussion, feature, etc.

[Download GitLab](https://about.gitlab.com/downloads/)

#### Recommended workflow

- Every time a new feature, bug or question comes up it will be written as an issue on the project. And it should be labeled with **bug**, **feature**, **discussion** or any other. 
- When the developer start to work on the issue he should add the label **wip** to the issue. If any questions arise, he should add the question as new comment on the issue and add the label **discussion** on it.
- The project manager should be watching the issues progress to know if anyone needs some feedback (**discussion**) and to know what tickets are beign under development (**wip**).
- Once the task is finished, the developer can add some comment to the issue about how to deploy or use the feature/bugfix, and remove the **wip** label.
- After the feature/bug is tested and ready to be merge and deploy, the issue's creator can close the ticket.

<a id="devel-server"></a>
## Give your developers a small/medium size server to deploy they work and test it.

Developers need to test they work on the same environment as the production server. For that, you can use tools like [Docker](https://www.docker.com/) in conjunction with [Vagrant](https://www.vagrantup.com/) allowing to have on their own computer an enviroment that matches the production server on a smaller scale.

But you NEED a test server to deploy all the new features/bugfixes to be tested before deploying the changes on production.

<a id="agile-scrum"></a>
## Implement Agile method using scrum

Agile definition:
> Agile software development is a group of software development methods in which solutions evolve through collaboration between self-organizing, cross-functional teams. It promotes adaptive planning, evolutionary development, early delivery, continuous improvement, and encourages rapid and flexible response to change.

[Wikipedia](https://en.wikipedia.org/wiki/Agile_software_development)

Scrum definition:
> Scrum is an iterative and incremental agile software development methodology for managing product development.

[Wikipedia](https://en.wikipedia.org/wiki/Scrum_\(software_development\))

In nutshell: You group all your issues into milestones (sprints) and start iterating through them.

The project manager (scrum master) will be in charge of implementing this methodology

Read the articles on wikipedia for a more detailed explanation.

<a id="example"></a>
## Full workflow example

1. The product owner add the requests to the backlog.
2. The project manager (scrum master) creates the sprints and assigns the gitlab issues to the developers.
3. The developer adds the **wip** label to the issue. Creates a new branch and start working.
4. Once the issue is ready to be tested, the developer deploy his changes on the devel server and add the label **test** to the issue.
5. When the issue is finish and ready to deploy, the developer remove the label's **wip** and **test** from the issue and submit a merge request to the target branch (master or development).
6. The project manager will do a code review and accept or reject the merge request.
7. The new feature/bugfix is deployed into production.