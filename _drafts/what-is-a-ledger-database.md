---
layout: post
title: "What is a ledger database?"
---
A non ledger database is table-centric. A ledger database is log-centric. In other words, the log is truly the database. 
Let's dive into what this all means.

Here, the "log" is a data structure that is ["an append-only, totally-ordered sequence of records ordered by time"](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying).
We will have diagrams later that help to illustrate its structure and purpose.

# Some context

Let's start with some context. I work on AWS Quantum Ledger Database (QLDB), which is the first commercially available ledger database.
This document does not represent AWS's official definition of a ledger database. This is my own mental model.
This document will not be a QLDB tutorial. I will talk about the abstract concept of a ledger database, of which QLDB is one
implementation. 

I want to explain the simple ideas behind a ledger database.

# Ledger

# Database 


















# Why not use Blockchain?

I have a problem. I don't know what time it is. I need to find a device that will tell me the day and time... car vs watch. 









# More info:
- "The log is the database.": https://datatechnologytoday.wordpress.com/2014/02/10/the-log-is-the-database/
- The log: https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying
- Rich Hickey's "Deconstructing the Database": https://www.youtube.com/watch?v=Cym4TZwTCNU
- Short intro to QLDB: https://www.youtube.com/watch?v=jcZ_rsLJrqk
- Initial re:Invent talk on QLDB: https://www.youtube.com/watch?v=7G9epn3BfqE