---
layout: post
title: "Fix Default 4000 Port Busy on Phoenix"
date: 2016-11-24 23:15
comments: true
categories: 
- programming
---

If you have experienced and got error like this ``` [error] Failed to start Ranch listener ConferenceWall.Endpoint.HTTP in :ranch_tcp:listen([port: 4000]) for reason :eaddrinuse (address already in use) ```
when you run server on phoenix ``` mix phoenix.server ``` .It's mean that is another process have reserve default port (4000) on phoenix. if you want to known which process is listening on this port
You can use something like ``` lsof -i :4000 ``` to find out more. the example result below is default port(4000) has reserved

```
(erlang-1802)[yrsdi@mac conference_wall]$ lsof -i :4000
COMMAND    PID  USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
Google     274 yrsdi  103u  IPv4 0xa174d9f2406034c5      0t0  TCP localhost:54543->localhost:terabase (ESTABLISHED)
beam.smp  7640 yrsdi   20u  IPv4 0xa174d9f2438e60e5      0t0  TCP *:terabase (LISTEN)
beam.smp  7640 yrsdi   25u  IPv4 0xa174d9f2443e7bcd      0t0  TCP localhost:terabase->localhost:54543 (ESTABLISHED)

```
If you need that port still used with that process, so you need to run your exiting project with another port, you can try this

```
$ PORT=4004 mix phoenix.server

```


or delete it

```

$ kill -9 <PID>

```
