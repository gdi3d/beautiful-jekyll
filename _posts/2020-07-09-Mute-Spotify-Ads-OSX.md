---
layout: post
published: true
title: Mute Spotify Ads On Mac (OSX)
date: '2020-07-09'
subtitle: I created this small script that will mute your computer audio when Spotify plays and Ads and unmute it after Ads ends.
category: Posts
tags: bash spotify hack
bigimg: /img/pexels-burst-373945.jpg
---
I use Spotify on my computer from time to time but I hate when the Ads start playing.

The first solution I was using was blocking Spotify Ads DNS's, but that stopped working after a while.

I don't mind having a **break** between a few songs, but I don't wanna hear the Ads, so I decided to create a small script to hack it.

The script does the following:

1. Using OSX log system I can listen to Spotify events.
2. Read the events and check if an Ad is about to be played.
3. If the event is an Ad about to be played **automatically mute system audio**.
4. If the next event is a song, **unmute system audio**.

# How to install it

1. Open a new terminal (use Spotlight search and type **terminal.app**)
2. Inside the new window paste this command and then hit enter 
  
    ```
    mkdir -p ~/MuteSpotifyAds && curl https://raw.githubusercontent.com/gdi3d/mute-spotify-ads-mac-osx/master/NoAdsSpotify.sh > ~/MuteSpotifyAds/NoAdsSpotify.sh
    ```

3. This will create a new folder inside your Home folder called `MuteSpotifyAds` and will place a new file called `NoAdsSpotify.sh`
4. To run the program just copy and paste the code below in the terminal and hit enter 
    
    ```
    sh ~/MuteSpotifyAds/NoAdsSpotify.sh
    ```

5. Open Spotify and enjoy! 

To exit the program just **close the terminal app or press Ctrl+c**

# Why not blocking Ads instead???
I used to have all the Spotify Ads DNS blocked but that stopped working.

Besides, I was bored that Saturday noon and I wanted to give it a try.

# Website and Github Repo

[https://gdi3d.github.io/mute-spotify-ads-mac-osx/](https://gdi3d.github.io/mute-spotify-ads-mac-osx/)

Here's the repo if you want to know more:

[https://github.com/gdi3d/mute-spotify-ads-mac-osx](https://github.com/gdi3d/mute-spotify-ads-mac-osx)


*Photo Credits: [https://www.pexels.com/@burst](https://www.pexels.com/@burst)*