---
layout: post
author: Kim Pastro
title: Understanding Rack for good
date: 2023-07-10 10:24:35 -0300
categories: ruby
tags: ruby rack
---

### Topics we're gonna cover:
1. Writing our own HTTP server.
2. Brief explanation about Socket, TCP and HTTP.
3. Rack is genious.

Once I become more confortable on Ruby on Rails, I ways wondered: "How things just works here?" Pretty sure that you've asked yourself the same question.

The first step to understand how Rails works (or any other Rack based Ruby framework) is to first understand what role does Rack plays and why it is so popular.

---
<br/>
### 1. Simple ruby HTTP server

As a starting point let's first code our own HTTP server in ruby.
With that server code we're gonna cover the next topics.

{% highlight ruby %}
require 'socket'
server = TCPServer.new 3000

loop do
  # accept the connection
  socket = server.accept

  # Print the request, which ends in a blank line
  puts line = socket.readline until line == "\r\n"

  # Tell the browser we are a HTTP server
  socket.write "HTTP/1.1 200 OK\r\n"

  # Tell the browser the body is 52 bytes
  socket.write "Content-Length: 52\r\n"

  # Empty line to separate headers from the body
  socket.write "\r\n"

  # Write the HTML that makes up the body
  socket.write "<html><body>"
  socket.write "<h1>Hello from Ruby!</h1>"
  socket.write "</body></html>\n"

  # Close connection
  socket.close
end

{% endhighlight %}


### 2. Socket, TCP and HTTP
Socket is an abstraction to the connection between two processes 

### 3. Rack FTW
