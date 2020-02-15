---
layout: post
published: true
title: 4 Steps to creating a basic development environment
date: '2020-02-15'
Category: Posts
Tags: tips
bigimg: /img/acrylic-acrylic-paint-art-artistic-1174952.jpg
---
Recently I was asked to help out and organize a small group of programmers to improve their (non-existent) workflow.

This is a small document with the recommendation that I wrote for them

# Overview

1. Use Git
2. Create an account in BitBucket.org
3. Give your developers a small/medium size server to deploy their work and test it
4. Implement some work methodology

## Use Git

What's git?

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
 
Translation: It allows you to keep a **history** of the changes in your code over time and allows multiple developers to work on the same project without worrying about screwing things up badly.

You can learn how to use it at [https://try.github.io/levels/1/challenges/1](https://try.github.io/levels/1/challenges/1)

You should also check: [https://www.atlassian.com/git/tutorials/setting-up-a-repository](https://www.atlassian.com/git/tutorials/setting-up-a-repository) to get started with **git**

[Download Git](https://git-scm.com/downloads)

## Create an account in BitBucket.org

What's [BitBucket.org](https://bitbucket.org/)?

> Bitbucket is more than just Git code management. Bitbucket gives teams one place to plan projects, collaborate on code, test, and deploy.

What will you do in BitBucket:

- Manage your Git repositories. All your repositories will be stored here (repositories can be public or private)
- Give access to your developers
- It has a bug tracker where you will create your tickets for bugs or features that your team needs to work on.
- Manage pull requests (more on this below)

If you don't want to use BitBucket you can use [GitLab](https://about.gitlab.com/) and [deploy it on your server](https://about.gitlab.com/install/) or use [github.com](https://github.com/)

## Basic workflow to work efficiently with Git

In git, you **save** (commit) your code in branches. Branches are created when you want to create a new feature or work on bug.

There's at least one branch called **Master**. This branch will be your primary branch, where the most updated version of your application will be.

All the new features or bugfix that you develop will have their own branch and then will be merged, using a pull request, to **Master** branch

### Merge and Pull Requests
Pull Requests (or Merge request) it just a fancy name for the step needed to merge your changes into **Master** branch. 
*You can merge o ask a pull request to other branches too, it's not limited to Master. But I'm talking about the final step before deploying your changes to production*

Usually, there's a **Merge Master** inside your team and he is the sole responsible of accepting or rejecting the **Pull Request**.

### How many Branches should I use?
There's no fixed number of branches or anything like that. A minimal common pattern is to have something like this:

- **Master** Latest working version
- **Pre** Where you first merge the new features or bugfixes to test if everything works ok

### Example

Let's assume that you need to work on a new feature. This are the steps that you should follow to complete the task:

1. Create a new branch from **Master** ([doc about this](https://www.atlassian.com/git/tutorials/using-branches "Git Branching"))
2. Name it **Feature-#** where # is the id of the ticket where the task description is on your bug tracker (BitBucket, GitHub, Gitlab, etc.)
3. Code 🐒
4. Create a Pull Request to **Master** ([doc about this](https://www.atlassian.com/git/tutorials/making-a-pull-request "Pull Request"))
5. The **Merge Master** accepts your work and gets merged into master

![Git Workflow New Feature]({{site.baseurl}}/img/git-workflow-new-feature.png)

### Some Rules

- DO NOT commit directly to master
- DO NOT commit to "keep a copy of this". Git is not a "temp" folder
- DO NOT commit credentials of any kind to any branch
- RTFM
  - https://git-scm.com/doc
  - https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud

### A more advanced pattern

[http://nvie.com/posts/a-successful-git-branching-model/](http://nvie.com/posts/a-successful-git-branching-model/)

## Give your developers a small/medium size server to deploy their work and test it.

Make sure you have a **pre production** environment that matches your **production** environment to test everything (but smaller).

You don't need to spend a lot on this, you can launch a VM on [DigitalOcean](https://m.do.co/c/3f5960ccae7c "DigitalOcean") (use this link and get USD 100 of credit on new accounts), [Amazon Web Services](https://aws.amazon.com/lightsail "AWS Lightsail")

You can turn it off and on to save some bucks.


## Implement some work methodology

I've found that these two works well most of the time, but all teams are different so you need to test which one works for you and don't be afraid to make changes to it

## Scrum 

It's based on the Agile methodology

> Agile software development is a group of software development methods in which solutions evolve through collaboration between self-organizing, cross-functional teams. It promotes adaptive planning, evolutionary development, early delivery, continuous improvement, and encourages rapid and flexible response to change.

[Wikipedia](https://en.wikipedia.org/wiki/Agile_software_development)


> Scrum is an iterative and incremental agile software development methodology for managing product development.

[More About it](https://www.atlassian.com/agile/scrum)


## Kanban

> Kanban is a popular framework used to implement agile software development. It requires real-time communication of capacity and full transparency of work. Work items are represented visually on a kanban board, allowing team members to see the state of every piece of work at any time.

[More About it](https://www.atlassian.com/agile/kanban)

You can use [Trello](https://trello.com/ "Trello") to create your Kanban boards and assign tasks.
