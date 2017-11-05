---
layout: post
title: "Azure Tips and Tricks Part 48 - Pushing a Container Image to a Docker Repo"
excerpt: "Learn how to create a container image with Docker"
tags: [azure, windows, portal, cloud, developers, tipsandtricks]
share: true
comments: true
---

## Intro

Most folks aren't aware of how powerful the [Azure](http://www.azure.com) platform really is. As I've been presenting topics on Azure, I've had many people say, "How did you do that?" So I'll be documenting my tips and tricks for Azure in these posts.

## The Complete List of Azure Tips and Tricks

[Available Now!](https://michaelcrump.net/azure-tips-and-tricks-complete-list/){: .btn .btn--success} 

## Containers for the rest of us

For some reason, I find containers are confusing and my goal with my [Azure Tips and Tricks](https://michaelcrump.net/azure-tips-and-tricks-complete-list/) is to try to make things easier. In this mini-series, I'll walk you through [Docker](https://www.docker.com) and how I use it with Azure. Below is a list of post that you can expect for this week. 

* [Azure Tips and Tricks Part 45 - Getting Started with Docker and Azure](http://www.michaelcrump.net/azure-tips-and-tricks45/)
* [Azure Tips and Tricks Part 46 - Run an app inside a Container Image with Docker](http://www.michaelcrump.net/azure-tips-and-tricks46/)
* [Azure Tips and Tricks Part 47 - Creating a Container Image with Docker](http://www.michaelcrump.net/azure-tips-and-tricks47/)
* [Today - Azure Tips and Tricks Part 48 - Pushing a Container Image to a Docker Repo](http://www.michaelcrump.net/azure-tips-and-tricks48/)

## Pushing a Container Image to a Docker Repo

Let's continue where we [left off](http://www.michaelcrump.net/azure-tips-and-tricks47/) in our last post, in which we created a new image that we can distribute that contains our new app. In this post, we'll go ahead and push the image to a Docker repo to prep it for later. 

Make sure you have a [Docker account](http://www.docker.com) (It's free) and type `docker login` at the terminal or command prompt to ensure we are authenticated. 

```text
Michaels-MacBook-Pro:~ mbcrump$ docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username (mbcrump): mbcrump
Password: 
Login Succeeded
```

Now in order to push to a new repo, you'll need to tag the existing image. You can do so by typing `docker tag mbcrump:mynewapp mbcrump/firstimage`. Where `mbcrump:mynewapp` is the existing image that contains our new app and `mbcrump/firstimage` will be our repo name. Play close attention to the `mbcrump/firstimage` part as `mbcrump` is your Docker username.

Once that is complete, then use `docker push mbcrump/firstimage` to move it to a repository. 

```text
Michaels-MacBook-Pro:~ mbcrump$ docker push mbcrump/firstimage
The push refers to a repository [docker.io/mbcrump/firstimage]
1fd4467b1c0e: Pushed 
0a3794bad5d4: Pushed 
54f3762778cc: Pushed 
88f0e0eb260c: Pushed 
1361e5e30088: Pushed 
52121b397f2e: Pushed 
480d03264b1d: Pushed 
a4212622fd11: Pushed 
a4af43f268c6: Pushed 
c2dca236d8e6: Pushed 
d4417cb76edb: Pushed 
0dc1ec77adb3: Pushed 
a75caa09eb1f: Pushed 
latest: digest: sha256:5458bbf2b1e35568c1542bc15551383737d379ddcd6e720d9701583925289157 size: 3060
Michaels-MacBook-Pro:~ mbcrump$ 
```

Great! Now you can log into your account on [store.docker.com](http://store.docker.com) and if you click on repos, then you'll see it. 
<img style="border:3px solid #021a40" src="/files/dockerazure10.png">

You'll see that it provides instructions to push a new version of the image as well as the commands to do so from the CLI. 

## To Recap what we've done so far

If you've been following the last four post, then we've went through the following steps: 

1. Installed and Setup Docker 
2. Verified installation through the CLI
3. Took a look at the Docker Store
4. Used an image from the Docker Store to build upon
5. Ran a Container and created a .NET Core app to it
6. Created a Shell Script to call the app through the new image
7. Added our app to a new container image
8. Called the app through the command line and executed our program
9. Packaged up the image container to send to a Docker repo
10. Pushed our image container to Docker through the CLI

I think we have a great foundation to keep building on this in the coming weeks and months. I hope you've learned a lot this week and I'll see you next week. 

**Bonus:** You can also go to [store.docker.com](http://store.docker.com) and create a repository. You'll also notice that they provide the CLI commands as well. 
<img style="border:3px solid #021a40" src="/files/dockerazure9.png">


## Want more Azure Tips and Tricks?

If you'd like to learn more Azure Tips and Tricks, then follow me on [twitter](http://twitter.com/mbcrump){: .btn .btn--success} or stay tuned to this blog! I'd also love to hear your tips and tricks for working in Azure, just leave a comment below. 