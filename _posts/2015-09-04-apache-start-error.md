---
layout: post
title: "Comman Apache Starting Problems"
comments: true
permalink: "apache-start-error"
---

## Apache Starting Problems in Xampp
Xampp is one of the best `Solution Stack` for all the LAMP/WAMP Developers out there. `Apache` is the most widely used 
Web Server in the world but developers do face some kind of problems in Starting `Apache Web Server`. These are the set
of simple things that can get rid of this Problem in `Windows OS`.


* Blocked Port
This is mainly caused by `Skype`, `Skype` uses port `80` which is needed by `Apache` Prevent it from doing so
Goto <b>Tools</b>-><b>Options</b>-><b>Advanced</b>-><b>Connection</b>
There `Uncheck Use port 80 and 443 for additional incoming connections`.
Or 
You can also try changing the port in `http.conf` that can be found at `C:\xampp\apache\conf`, Now find
`Listen 80` and `ServerName localhost:80`. Type `netstat` in `cmd` and find a free port(ex:8090), replace it
in `http.conf` at `Listen 8090` and `ServerName localhost:8090`.


* Stop http Service
Run `cmd` as `Adminstrator` and type the following command
`net stop http`


* Stop Workstation 
Simply Stop the Service in Services.msc 
Goto `run` Services.msc find <b>Workstation</b>-><b>Right Click</b>-><b>Stop</b>

Hope these help, Thanks for reading.
Cheers.


