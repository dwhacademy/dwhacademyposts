---
title: "Proven DWH Design"
date: 2019-06-24
tags: [dwh, design]
---

There is an unlimited number of ways how to build a data warehouse. Few of them work and some of the few can even survive in the long term. In this post, we are going to describe the high-level design of the typical successful DWH in the long term.

### Landing Area
Imagine the Landing Area as an address, where the files from the source systems arrive. It is the first interface of the DWH, usually some file system organized into directories for each source file. The main goal of the Landing Area is to organize separate source files into batches which can be loaded into a database.

The challenge of the Landing Area is the control over the source files which are usually delivered by external parties. It needs to be recognized when some part of data is missing or when the structure of the data is not satisfying the delivery agreement with the source system. The biggest challenge is to completely automate all that. Frequently, a lot of manual inputs is involved here, and this, in theory, the simplest part of the DWH becomes the real bottleneck.

### Stage Layer
The Stage Layer is the first database layer, where the data from the source files are loaded

### Integrated Layer
test ste

### Access Layer
test ste

### Data marts
test ste
