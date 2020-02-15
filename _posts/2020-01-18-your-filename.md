---
layout: post
published: false
title: Creating a basic development environment
date: '2015-09-18'
Category: Posts
Tags: tips
---
Recently I was asked to help out and organize a small group of programmers to improve their (non-existent) workflow.

This is a small document with the recommendation that I wrote for them

# Overview

1. [Use Git](#use-git)
1. [Create an account in BitBucket.org]
1. [Give your developers a small/medium size server to deploy they work and test it](#devel-server)
1. [Implement Agile method using scrum](#agile-scrum)
1. [Full workflow example](#example)

## Use Git

What's git?

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
 
Translation: It allows you to keep a **history** of the changes in your code over time and allows multiple developers to work on the same project without worring about screwing things up badly.

You can learn how to use it at [https://try.github.io/levels/1/challenges/1](https://try.github.io/levels/1/challenges/1)

You should also check: [https://www.atlassian.com/git/tutorials/setting-up-a-repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository) to get started with **git**

[Download Git](https://git-scm.com/downloads)

## Create an account in BitBucket.org

What's [BitBucket.org](https://bitbucket.org/)?

> Bitbucket is more than just Git code management. Bitbucket gives teams one place to plan projects, collaborate on code, test, and deploy.

What will you do in BitBucket:

- Manage your Git repositories. All your repositories will be stored here (repositories can be public or private)
- Give access to your developers
- It has a bugtracker where you will create your tickets for bugs or features that your team need to work on.
- Manage pull requests (more on this below)

If you don't want to use BitBucket you can use [GitLab](https://about.gitlab.com/) and [deploy it on your own server](https://about.gitlab.com/install/) or use [github.com](https://github.com/)

## Basic workflow to work efficently with Git

In git you **save** (commit) your code in branches. Branches are created when you want to create a new feature or work on bug.

There's at least one branch called **Master**. This branch will be your primary branch, where the most updated version of your application will be.

All the new features or bugfix that you develop will have their on branch and then will be merged, using a pull request, to **Master** branch

### Merge and Pull Requests
Pull Requests (or Merge request) it just a fancy name for the step needed to merge your changes into **Master** branch. 
*You can merge o ask a pull request to other branches too, it's not limited to Master. But I'm talking about the final step before deploying your changes to production*

Usually there's a **Merge Master** inside your team and he is the sole responsible of accepting or rejecting the **Pull Request**.

### How many Branches should I use?
There's no fixed number of branches or anything like that. A minimal common pattern is to have something like this:

- **Master** Latest working version
- **Pre** Where you first merge the new features or bugfixes to test if everything works ok

### Example

Let's assume that you need to work on a new feature. This are the steps that you should follow to complete the task:

1. Create a new branch from **Master** ([doc about this](https://www.atlassian.com/git/tutorials/using-branches "Git Branching"))
2. Name it **Feature-#** where # is the id of the ticket where the task description is on your bugtracker (BitBucket, GitHub, Gitlab, etc.)
3. Code 🐒
4. Create a Pull Request to **Master** ([doc about this](https://www.atlassian.com/git/tutorials/making-a-pull-request "Pull Request"))
5. The **Merge Master** accepts your work and gets merged into master

![Git Workflow New Feature]({{site.baseurl}}/img/git-workflow-new-feature.png)

Always have at least two main branches:

- **Master** will have the lastest stable version of your project  
- **Devel** will have all the new features for the next version of your project

Developers shouldn't make changes directly into **devel** nor **master**

Every time a developer need to work on a **feature** or **bug** she/he will create a new branch from **devel** or **master** as the starting point.

This new branch will have the following pattern:

- For features: **feature/issue-\#**
- For bugs: **bug/issue-\#**

Where \# will be the issue number on your bug tracker.

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
