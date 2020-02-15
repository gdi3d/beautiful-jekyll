---
layout: post
published: true
title: How to publish a website
date: '2015-08-10'
Category: Posts
Tags: 'web, beginner, how to'
subtitle: What do you need to know and do to create a website
category: Posts
tags: web beginner
---
### Overview

If you want to have your own website you need to:

1. The website
2. Hire a Hosting plan or a VPS
3. Buy a domain name
4. Setup yours DNS's (connects your domain to your hosting or VPS)

### Website

You can create it using:

If you're building a website for your company or a blog you can use [WordPress.com](https://wordpress.org/). If you need something more complex you could try [Joomla](https://www.joomla.org/) or [Drupal](https://www.drupal.org/). For e-commerce websites try [Magento](http://magento.com/) or [OpenCart](https://www.opencart.com/)

### Domain name

The domain is the **word** that you type in your browser to enter a website.

Ex.: **mywebsite.com**

#### Where do I buy it ?

You can buy your domains at:

* [GoDaddy.com](http://www.godaddy.com/)
* [Namecheap.com](http://www.namecheap.com/)
* [Name.com](http://www.name.com/)

These are the most popular, but you can always google for more ;)

### Hosting or VPS

Now we need a place to store our website on the internet. This means, a place where we can **upload** the files of our website. For this, we have two options: **Hosting** or **VPS**

#### Hosting

A hosting company has a lot of severs where they store and run multiple websites.

The most common features that a hosting company provides are:

- Disk space to store our website
- FTP access to upload our files
- Email addresses with our domain name: **support@mywebsite.com**
- Administration panel to setup emails addresses, FTP users, statics, etc.

Before buying a hosting plan we need to make sure that has all we need for our website. If our website it's built on PHP and uses MySQL we must buy a plan that support that.

#### VPS

A VPS it's a **Virtual Private Server***. This means that we have access to all the server configurations and we can make any change we want to the operating system.

In this case we'll be the solely responsible for mantaining the server running.

### DNS's

DNS ***(Domain Name Server)*** it's what connects our domain name with the hosting or VPS. When someone tries to access our website, the DNS's are the ones that sent the user to the server where our website is runing.

When you hire a hosting, the hosting company will provide you the DNS's that you need to enter on your domain configuration.

Usually these DNS's looks like:

ns1.hosting.com
ns2.hosting.com

You will have to setup this address on your domain. For this, all domain providers have an admin panel where you can enter this information.

If you choose to use VPS then the DNS's can be set directly on the server configuration or admin panel in most cases.
