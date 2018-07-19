---
layout: post
title: "URI for HTTP"
excerpt: "Introduce the URI of http, and some predestination. Also talk a little of server."
date: 2018-02-02
tag: [http, web]
---

This post is a summary of one of my Udacity class where I have got some important basic information of http. There is the [course link](https://cn.udacity.com/course/http-web-servers--ud303}\).

# Basic
The http transaction always involves a _client_ and a _server_.
And the browser is the most common _client_ we used.
The basic workfow of http is that your browser sends http _requests_ to web server, and the web server send _responses_ to your web browser.

Browsers are the most common and complicated user interface for web technology, but they are not the only web client around. 
Http is powerful and widely supported in software, so it is a common choice for programs that **need to talk to each other across the network**, even they don't look like anything like a web browser.


You enter a URL in the browser, and if there is a file named _index.html_ in the directory represented by the URL, the browser will present the content of the index.html.
{: .notice}

### 1. What is a server?
A server is just a program that accepts connections from other programs on the network.

When you start a server program, it **waits for clients** to connect to it. Then when a connection comes in, server will run some programs to handle it. The connection is like a channel, for example a phone call, the clients send requests over the connection, and servers send response back.

### 2. URI
A web address is also called a URI for _Uniform Resource Identifier_.

You put it into the browser to tell the browser where to go.

You problably have known the term URL or Uniform Resource Locator.
They are pretty close to the same thing. A URL is a URI for a resource in the network. And URI is slightly more prices. 
{: .notice}

A URI is a name for a resource, the form of the resource is pretty abundant, like page, data and API, so on.

Here is an example of URI:
https://en.wikipedia.org/wiki/Fish
(this is a common example of web address URI, and there are many other style URI)

The URI has three visible parts:

* **https** is the scheme
* **en.wikipedia.org** is the hostname
* and <p sytle="color=red">/wiki/Fish</p>is the path

#### Scheme
The first part is **scheme**, which tells the client how to go about accessing the resource.
For example, http, https and ftp. Http and https URIs point to resources served by a web server.

#### Hostname
Hostname tells the client which server to connect to. And hostname can only appear after a URI scheme that supports it, such as http or https. In these URIs
there will always be a "**://**" between the scheme and hostname.
And in fact, the "**:**" goes after the scheme, and the "**//**" goes before the hostname. For example, _mailto_ URIs doesn't have the hostname part, and mailto:example@gmail.com, a well-formed URI, only has the "**:**".

#### Path
In an http URI, the next thing that appears is the path, which identifies a particular resource on a server. A server can have many resources on it. The path can tells the server which resource the client is looking for.

When you write a URI without a path, such as <span style="color:red">http://www.baidu.com</span>, the browser fills in the default path, which is written with a single slash. That's why the http://www.baidu.com is the same with http://www.baidu.com/( with the slash on the end).

The slash after hostname is also called **root**.
You're not looking at the root of your computer's whole file system. It's just the root of the resources served by web server.

#### Relative URI reference
    <a href="a.png">a.png</a>

The above html fragment shows a URI of a picture named a.png, but the 'href' attribute doesn't include the hostname or port of the server.
This is a relative URI reference, and it's relative to the context in which it appears - specially the page is on. The browser can figure that out from context.

#### Other URI parts
https://en.wikipedia.org/wiki/Oxygen#Discovery

The part of the URI after the <span style="color:red">#</span> sign is called a **fragment**. The browser doesn't even send it to the web server. It lets a link point to a specific named part of a resource; in HTML pages it links to an element by **id**.

https://www.google.com/search?q=fish

The <span style="color:red">?q=fish</span> is a **query** part of the URI. This does get sent to the server.

There are a few possible parts of URI, you could read this for more information: 

<a href="https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Generic_syntax">https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Generic_syntax</a>


### 3. Hostname and Port

#### Hostnames
The internet tells computer by **IP address**, and the traffic of sending and receiving over the internet is labeled by IP address.
In order to connect to a web server such as <span style="color:red">www.baidu.com</span>, a client needs to translate the hostname into an IP address.

Your operating system's network configuration uses the Domain Name Service(DNS)- a set of servers maintained by Internet Service Providers(ISPs) and other network users - to look up hostnames and get back IP address.
There are two programs to look up hostnames in DNS.

>$ host www.baidu.com

>$ nslookup www.baidu.com

nslookup also give the IP address of the DNS server.

Why is it called a **host**name? In network terminology, a host is a computer in the network; one that could host services.
{: .notice}

####  Localhost
The IPv4 address **127.0.0.1** and the IPv6 address **::1** are special addresses that mean "this computer itself".
The hostname **localhost** refers to these special addresses.

####  Port
When start a server in the computer, it's usual to enter the URI like "localhost:8000", offering a port number after the hostname, but most of the web addresses you see in the wild don't have a port number on them.
This is because **the client usually figures out the port number from the URI scheme**.

For instance, HTTP URIs imply a port number of <span style="color:red">80</span>, whereas HTTPS URIs imply a port number of <span style="color:red">443</span>.

**What is a port number, anyway?**
In the network, IP address distinguish computers, and port numbers distinguish _programs_ on those computers to decide which program should handle this internet data.

We say that a server "listens on" a port, such as 8000. "Listening" means that when server starts up, it tells its operating system that it wants to receive connections from clients on a particular port number.
When a client(such as a web browser) "connects to" that port and sends a request, the operating system knows to forward that request to the server that's listening that port.



