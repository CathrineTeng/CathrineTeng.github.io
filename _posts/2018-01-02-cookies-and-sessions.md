---
layout: post
title:  "Cookies和Sessions的介绍"
date:   2018-01-02
excerpt: "Cookies和Sessions是Web开发中基本知识，比较两者的不同，并介绍如何相互协作"
tag: [web]
comments: true
---


### 简介
在现代Web开发中，sessions和cookies总是重要组成内容，两者相互配合，共同实现web开发功能，例如用户登录和注销功能。

#### cookies的使用
当客户端想发生请求时，会检查一下是否有匹配目的服务器地址的cookies，如果存在，则将cookies包含在请求中，一起发送给服务器。服务器接收后对cookies进行解析，将合适的内容相应给客户端。

在用户登录的例子中，用户通过用户名和密码进行登录操作，一旦完成认证，服务器会返回给客户端一个包含了用户名的cookie，表明用户已登录，之后每次客户端发送请求都会包含这个cookie，登录信息可以用于渲染页面，例如将登录名替换为已登录的用户名。cookie中包含着敏感信息，所以必须设定失效时间，一般间隔几分钟或者几天就自动过期。

由于包含在cookies中的信息需要在客户端及服务器端之间传送，使用cookies实际打开了一个潜在的安全漏洞。在使用cookies时，设计者可以好好考虑一下，**这些打算以cookies形式存储的信息是否真的有必要发送及存放在客户端机器上**

#### Sessions 和无状态协议
Http协议是无状态协议，及每一次客户端发送请求，都需要重新建立网络连接（TCP连接）。这样可以简化http协议及网络连接，但是也带来一些问题，例如，同一个主机客户端需要每次都告诉服务器是谁登录。
现在Web开发中，采用的普遍方法是将状态信息保留在服务器端session中，例如用户名，密码，状态信息都放在session中，每个session对应一个独特的session ID，这个session ID以cookies形式返回及保留在客户端。这种方式解决看无状态协议和cookies安全性低的问题。

    without cookies
    替代cookies但是维持状态信息的另一种方法是将session id的编码放入URL。

