# async
Homework 11 task. [OTUS C++]

[![Build Status](https://travis-ci.org/DGolgovsky/async_bulk.svg?branch=master)](https://travis-ci.org/DGolgovsky/async_bulk)
[![Code Health](https://landscape.io/github/DGolgovsky/async_bulk/master/landscape.svg?style=flat)](https://landscape.io/github/DGolgovsky/async_bulk/master)
[ ![Download](https://api.bintray.com/packages/dgolgovsky/otus-cpp/async_bulk/images/download.svg) ](https://bintray.com/dgolgovsky/otus-cpp/async_bulk/_latestVersion)

**Task description**

The main goal is to rework task 07 so that the data entry was controlled by an external code. The interface is described in the file `async.h`

The initiator of the exchange will be the external code, instead of the usual the `main()` input point will be three - `connect()`, `receive()`, and `disconnect()`

The call order is as follows:

• Called `connect()` with the size of the command block. Saved the return value. The meaning is not interpreted in any way and serves only for passing context;

• Called `receive()` with a pointer to the beginning of the buffer, buffer size and context. The call is repeatable;

• `Disconnect()` is called with context transfer. The call destroys context.

It is necessary to implement these functions in such a way as to preserve the old the functionality of the project and add a new feature. The implementation must allow multiple calls to `connect()`

Call `receive()` with different contexts should not interfere with each other. Depending on the internal implementation, a requirement may arise have the same block size for all commands.

There are no purpose profound changes. If the potential to name different queue size entails deep processing function `connect()` should return `nullptr`.

Calls can be made from different streams but calls with the same context is executed from the same thread.

Detailed description on the [gh-pages](https://dgolgovsky.github.io/async_bulk/)

**Dockerfile**
```
FROM ubuntu:trusty
#### Bintray (by JFrog) 
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 379CE192D401AB61
#### Dmitry Golgovsky (Packages sign) 
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D5CEB8D4D5185900
#### toolchain repo key
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1E9377A2BA9EF27F
RUN echo "deb http://dl.bintray.com/dgolgovsky/otus-cpp trusty main" | sudo tee -a /etc/apt/sources.list
RUN echo "deb http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu trusty main" | sudo tee -a /etc/apt/sources.list
RUN apt update
RUN apt install -y libstdc++6 async
```

**OTUS** C++ online [course](https://otus.ru/lessons/razrabotchik-c++/) studying repository.

**About the course**

Being one of the most popular programming languages, C++ is widely used for software development. The scope of usage includes the creation of operating systems, a variety of applications, device drivers, applications for embedded systems, high-performance servers, and entertainment applications (games).
In the course "C++ Developer" will be considered as introductory concepts, such as automation tools, STL, innovations of `11` and `14` standards; and more complex: asynchronous programming, design patterns, distributed high-availability services architectures.
