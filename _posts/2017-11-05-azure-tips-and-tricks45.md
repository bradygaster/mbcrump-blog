---
layout: post
title: "Azure Tips and Tricks Part 45 - Getting Started with Docker and Azure"
excerpt: "Learn how to get started using Docker and Azure"
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

* [Today - Azure Tips and Tricks Part 45 - Getting Started with Docker and Azure](http://www.michaelcrump.net/azure-tips-and-tricks45/)
* [Azure Tips and Tricks Part 46 - Run an app inside a Container Image with Docker](http://www.michaelcrump.net/azure-tips-and-tricks46/)
* Azure Tips and Tricks Part 47 - Creating a Container Image with Docker
* Azure Tips and Tricks Part 48 - Pushing a Container Image to a Docker Repo

## Getting Started with Docker and Azure

**What is Docker?** Docker is an open-source project that automates the deployment of applications inside software containers. It automates the repetitive tasks of setting up and configuring development environments so that developers can develop. 
{: .notice--primary}

Head over to [Docker](https://www.docker.com/) and you'll want to download the Community Edition. Keep in mind that there are two channels. Which are the Stable and Edge version. As you can imagine, the stable build is... well... stable and the edge build is for those that want the latest bits (which may not be tested). Choose your poison. For this series, we'll use the Stable version. 

Once it has been downloaded and installed, you should see a green light that indicates that docker is running. 

<img style="border:3px solid #021a40" src="/files/dockerazure1.png">

You can easily verify it was installed properly by opening terminal or a command prompt and typing `docker info`.

<img style="border:3px solid #021a40" src="/files/dockerazure2.png">

If you would like to see version information then type `docker version`. 

<img style="border:3px solid #021a40" src="/files/dockerazure3.png">

Great, so now let's pull an image since it is up and running properly. Head over to [store.docker.com](http://store.docker.com) and search for aspnetcore-build. 

**Why this image?** We want to run an ASP.NET Core without installing the tools, platform and SDK on my local machine. 
{: .notice--primary}

If you search for `aspnetcore-build` then you'll land on this [page](https://store.docker.com/community/images/microsoft/aspnetcore-build). Pay close attention to the following command (highlighted below) that we'll use to copy into our terminal/command prompt to pull down the image. 

Note the structure of the command - `docker pull microsoft/aspnetcore-build`. If you're familiar with git, then this syntax feels right at home. You can also type `docker help` for a full list of commands. 

<img style="border:3px solid #021a40" src="/files/dockerazure4.png">

You'll see Docker pulled the image from Docker Store, and when it completes, you can type `docker images` to list all the images available to use. 

<img style="border:3px solid #021a40" src="/files/dockerazure5.gif">

```text
Michaels-MacBook-Pro:~ mbcrump$ docker images
REPOSITORY                   TAG                 IMAGE ID            CREATED             SIZE
microsoft/aspnetcore-build   latest              c0c285a7a306        37 hours ago        1.85GB
```

Now we'll proceed to work with that image in the next post. 

## Want more Azure Tips and Tricks?

If you'd like to learn more Azure Tips and Tricks, then follow me on [twitter](http://twitter.com/mbcrump){: .btn .btn--success} or stay tuned to this blog! I'd also love to hear your tips and tricks for working in Azure, just leave a comment below. 