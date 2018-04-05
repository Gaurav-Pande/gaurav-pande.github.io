---
layout: page
title:  "Ip Threshold prediction Using Spark Ml lib"
date:   2016-01-01 08:43:59
permalink: /classifier/
categories: ml
desc: "A application to predict Ip threshold based on historical data"
---

**Technologies**: Python,jupyter,Spark ml lib,scikit learn

---
Lately, I have been working on this use case called Ip pool automation which leverages the capabilities that Network Telemetry offers us today. Every solution comes out of challenge or problem that the network faces. Let's understand the problem scenario here first:

 

Broadband Network Gateway (BNG) is the access point for subscribers, through which they connect to the broadband network. When a connection is established between BNG and CustomerPremise Equipment (CPE), the subscriber can access the broadband services provided by the Network Service Provide (NSP) or Internet Service Provider (ISP). One of the responsibilities of the BNG is to manage the IP pools allocated to the subscriber.

 

### The Challenge here:

This management of the Ip pool is a manual process, i.e one has to monitor the BNG router for the threshold of the IP pools allocated, and if it exceeds a certain value, then the operator has to manually allocate a free range of the IP pool from the database to the BNG router.

 

### The opportunity here: 

We can see an opportunity here to overcome this challenge by making our device or box programmable.

 

### Solution:
We can stream the telemetry data from the box and monitors for the two fields ( used address, total address) and we then calculate real time percentage of used address, and then by comparing this percentage with threshold we can trigger some alarms to different web hooks or channels. In this case, we can trigger one alarm to spark room just for the notification purpose and other alarm to a python application which can apply some actionable intelligence to automatically allocate the free IP pool range to the device. 


### Machine Learning:

Using machine learning I predicted the threshold value of by trainig the spark ml algorithm with past 30 days of data. Now we can say that, if the ip usage increases every monday in the week and falls down by the end of the day(typicall when people have less internet activities), than we can mitigate the situation where we ran out of Ips :)




---
