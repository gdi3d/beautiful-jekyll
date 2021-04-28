---
layout: post
published: true
title: Hacking tool for HMR on docker
date: '2020-03-27'
subtitle: Sometimes HMR tools don't work quite right when using docker on some OS (OSX) with a mounted volume. You change a file and nothing happens, it doesn't detect the change and no rebuild happens.
category: Posts
tags: javascript docker HMR
bigimg: /img/broken-heart-love-sad-14303.jpg
share-img: /img/share-hacking-tool-for-hmr-docker.jpg
---
I'm starting a new project and I need to build the frontend for it. I decided to use Vue.js and get back to the frontend for a few days.

I'm used working with docker, so I created my container, installed everything on it and started working on it.

After reading some [nice tutorial about vue](https://savvyapps.com/blog/definitive-guide-building-web-app-vuejs-firebase) I started coding until I realized I needed my build to automatically refresh.

After reading about HMR (Hot Module Replacement) with webpack I realized it was too much of a hassle for my project. I asked a colleague about what else I could use and he suggested using [Parcel](https://parceljs.org/) since it was very straight forward to use.

However, it didn't work 😒.

For some reason, whenever I changed a file on my editor **Parcel** didn't rebuild my app. I read all the docs and tried every workaround without any luck.

I did some testing and the only way it worked was if I did a **touch** on the files from inside the container.

Just to be clear, this is not a problem with **Parcel** but on how the volume it's working on docker and I guess it might have to be with some cache issue.

After all this, finally I ended up building the following tool:

[https://github.com/gdi3d/js-hmr-osx-docker-helper](https://github.com/gdi3d/js-hmr-osx-docker-helper)

> Sometimes HMR tools don't work quite right when using docker on some OS (OSX) with a mounted volume. You change a file and nothing happens, it doesn't detect the change and no rebuild happens.
>
> This hack-script will make sure your HMR tools (webpack, parcel, etc) sees that a file has been changed/created/deleted/etc.
>
> It uses the command touch to update the file from inside the container helping the HMR tools to be aware of the update.

*Photo Credits: (https://instagram.com/burakkostak)[https://instagram.com/burakkostak]*
