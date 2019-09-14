---
title: "DWH Design patterns in practice: Logging as an essential part of the controlled development environment"
image: "logging"
date: 2019-09-14
tags: [dwh, logging]
categories: ["Logging"]
authors: [Lubomir Kamensky]
---

In my prior post [How to setup a controlled development environment](https://posts.dwhacademy.com/development-environment/), we talked about the automation of the deployment as the first step to the controlled development environment. Having controlled deployment, the next step is to get control over the data loads.  The goal of this post is to show a simple way of tracking all steps of the data load in a logging table. 

### Benefits of the logging
There are many benefits to having a good logging system.  The main is the transparency of the data load process.  It is clear what steps were executed during the load and what changes happened in data within each step.  It is easy to recognize that something went wrong and it is possible to compare different loads in the same or even in different database environments.

Deploying different versions of the code into two separate environments and loading the model using the same source data we can quickly see the impacts of the code change to the data load.

Typically we use the logging table to find out:

- the reason for the load failure

- whether data from all sources were loaded

- impacts of any code change

A logging table is a simple but powerful tool used in all environments, starting from the development database. It is part of project metadata. 
Let's look into the implementation of such logging.  First of all, we need to introduce an identification for the entire data load. 

It can be done using one simple table: 

<script src="https://gist.github.com/lubomirkamensky/8cac3fefb719a9774085461251238b94.js"></script>
	
And pair of procedures, one  starting each data load:

<script src="https://gist.github.com/lubomirkamensky/34d27d8c0a0343e456941cf07a6e73d4.js"></script>

And another ending the data load:

<script src="https://gist.github.com/lubomirkamensky/6bc9f2fd9701312230203abc803c8356.js"></script>

Having the Load identification ready, we can create the logging table itself:

<script src="https://gist.github.com/lubomirkamensky/bb896ee73d9822bfbfd5b4092b92b39e.js"></script>

And show how to use it in load procedures. The way how to get the number of affected records for each execution step varies between different databases.  Here is how it is done in the Postgres. There is logging after any interaction with the database, in our case we have two such steps, delete from the table and insert into the table.

<script src="https://gist.github.com/lubomirkamensky/6ef08de32dd0439e51f695f1fb23d92d.js"></script>


Having all parts in place we can  look into the logging table records:

<img src="/log01.png" width="800px" alt="logging table"/>

And now let's compare the logging records between two different versions of our code, current version in development environment and prior version in sandbox 03

<script src="https://gist.github.com/lubomirkamensky/3107264d43bb4d1cfbaf10d5c57c7942.js"></script>

All fully functional code is available in our (Demo Project Repository on GitHub)[https://github.com/dwhacademy/demoproject/tree/issue-6-implement_logging].

