---
title: "DWH Design patterns in practice: Technical history as a fundamental element of every data warehouse"
image: "technical_history"
date: 2019-11-26
tags: [dwh, history]
categories: ["History handling"]
authors: [Grzegorz Swierniak]
---

Data is constantly changing for various reasons. Sometimes it is a result of errors made but human, sometimes the changes truly represent changes in the real-world, so none of the data warehouses can work without proper historization. This article will introduce you to a very fundamental type of history handling - technical history.

<img src="logging.png" width="800px" alt="logging"/>

### Technical and business history


<script src="https://gist.github.com/lubomirkamensky/8cac3fefb719a9774085461251238b94.js"></script>
	
tbd

### Common pattern to historize target tables


Fully functional code is available in our [Demo Project Repository on GitHub](https://github.com/dwhacademy/demoproject/tree/issue-6-implement_logging).

