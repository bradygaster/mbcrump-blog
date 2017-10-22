---
layout: post
title: "Azure Tips and Tricks Part 38 - Create a JSON Schema to be used in a Azure Logic Apps"
excerpt: "Learn how to create a JSON Schema that we'll use with Azure Logic Apps"
tags: [azure, windows, portal, cloud, developers, tipsandtricks]
share: true
comments: true
---

## Intro

Most folks aren't aware of how powerful the [Azure](http://www.azure.com) platform really is. As I've been presenting topics on Azure, I've had many people say, "How did you do that?" So I'll be documenting my tips and tricks for Azure in these posts.

## The Complete List of Azure Tips and Tricks

[Available Now!](https://michaelcrump.net/azure-tips-and-tricks-complete-list/){: .btn .btn--primary} 

## My Scenario - Tracking Run Data

I thought I'd use this week's Tip and Tricks series to show a practical example of how I am using Azure. I've started running outdoors and would like to extract several links that my app generates via email and send them to my OneDrive account automatically vs doing it manually after each run. I'm also concerned that the app that generates my data may be abandoned one day. In order to secure my data, I used a combination of [Zappier.com](http://www.zapier.com) and [Azure](http://www.azure.com) to solve my problem and over the course of this week, we'll cover the following sections needed in order to implement this: 

* [Parse Emails to be used in a Azure Logic Apps](http://www.michaelcrump.net/azure-tips-and-tricks37/)
* [This post - Create JSON Schema to be used in a Azure Logic Apps](http://www.michaelcrump.net/azure-tips-and-tricks38/)
* [Setup an HTTP Request Trigger that is used in an Azure Logic Apps](http://www.michaelcrump.net/azure-tips-and-tricks39/)
* [Upload Files from a URL with Azure Logic Apps](http://www.michaelcrump.net/azure-tips-and-tricks40/)


## Create JSON Schema to be used in a Azure Logic Apps

In the [last post](http://www.michaelcrump.net/azure-tips-and-tricks37/), we decided that we'd extract the following 4 pieces of information from the email. 

* Filename - This is the general filename that the app uses and I think it's a piece of data we may want to store. 
* CSV URL - A URL to the CSV File that we'll be posting to OneDrive. 
* GPX URL - A URL to the GPX File that we'll be posting to OneDrive. 
* KML URL - A URL to the KML File that we'll be posting to OneDrive. 

We need to create the JSON body which we'll use to create the schema. I used [objgen.com/json](http://www.objgen.com/json) to quickly create this piece, but you can just manually type it if you want. 

<img style="border:3px solid #021a40" src="/files/schemablog1.gif">

Here is the JSON payload with some sample data. 

```text
{
  "filename": "myfilename",
  "gpx": "http://www.someurl.com",
  "csv": "http://www.someurl.com",
  "kml": "http://www.someurl.com"
}
```

OK, now I clicked the "Copy" Button and headed over to [jsonschema.net](https://jsonschema.net/#/editor) and pasted it in and my JSON schema was generated. 

<img style="border:3px solid #021a40" src="/files/jsonschema2.png">

```json
{
  "$schema": "http://json-schema.org/draft-06/schema#", 
  "definitions": {}, 
  "id": "http://example.com/example.json", 
  "properties": {
    "csv": {
      "id": "/properties/csv", 
      "type": "string"
    }, 
    "filename": {
      "id": "/properties/filename", 
      "type": "string"
    }, 
    "gpx": {
      "id": "/properties/gpx", 
      "type": "string"
    }, 
    "kml": {
      "id": "/properties/kml", 
      "type": "string"
    }
  }, 
  "type": "object"
}
```

Too easy! Now head over to the [Zappier Editor](https://zapier.com/app/editor) and create a new app.

You'll want to use the **New Email** Trigger and use the **Email Parser by Zappier** and allow it to connect to your mailbox that you [created earlier](http://www.michaelcrump.net/azure-tips-and-tricks37/).  

For the next step, you'll want to use an **Action** that is a **POST** request that uses **Webhooks by Zappier**. When you get to the point to where it asks you for a URL, then use [requestb.in](https://requestb.in/) to see what your HTTP client is sending or to inspect and debug webhook requests. Now you have a URL that you can use for testing. Ensure your payload is set to **JSON** and now you can select the data from your parsed email (filename, csv, kml, gpx). You can leave the rest of the fields as-is. When you finish your screen should look like the following: 

<img style="border:3px solid #021a40" src="/files/schemablog3.png">

Go ahead and save and run the test. After you switch over to your [requestb.in](https://requestb.in/). You should see the output that matches the parsed data from the email. 

<img style="border:3px solid #021a40" src="/files/schemablog4.png">

Come back [tomorrow and we'll replace the URL with a live Logic Apps URL](http://www.michaelcrump.net/azure-tips-and-tricks39/). 

## Want more Azure Tips and Tricks?

If you'd like to learn more Azure Tips and Tricks, then follow me on [twitter](http://twitter.com/mbcrump){: .btn .btn--success} or stay tuned to this blog! I'd also love to hear your tips and tricks for working in Azure, just leave a comment below. 