---
layout: post
title: "Getting started with Ajax"
comments: true
permalink: Getting started with Ajax
---

*Hello people!* It's been long time since the last post, i was bit busy with the work and all, today i'm going to 
take you through how things go in Ajax. So, let's get started.

## What on earth is Ajax ?
Ajax - Asynchronous JavaScript and XML
It's a new way of using existing standard, Ajax got popular when Google started using it in 2005 for Google Search, Google Maps and Gmail.

It's a way of exchanging data with the server without reloading the entire page. Classic pages load the entire page when a request is sent 
for the browser

## So, How does Ajax Work ?

*  When an <strong>HTML DOM events</strong> is occured an XMLHttpRequest Object is created by the browser and it sends HttpRequest.
*  Server Process the HttpRequest, sends back the response text and the data in the form of XML or Plain Text.
*  Now Browser process the received data using JavaScript and the content is updated.


## Simple example on Ajax with JavaScript

<strong>HTML Snippet</strong>

```html
   <!DOCTYPE html>
   <html>
   <head>
   <script>
        function loadContent()
          {
                var xmlhttp;
                if (window.XMLHttpRequest)
                  {// This code if for IE7+, Firefox, Chrome, Opera, Safari
                        xmlhttp=new XMLHttpRequest();
                   }
                else
                  {// IE5,6 doesn't XMLHttpRequest object  they have                    ActiveXObject Instead
                        xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
                  }
                xmlhttp.onreadystatechange=function()
                  {
                      if (xmlhttp.readyState==4 && xmlhttp.status==200)
                            {
                                document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
                            }
                  }
                xmlhttp.open("GET","hello.php",true);
                xmlhttp.send();
          } // end of loadContent
</script>
</head>
<body>
<img src="bill.jpg">
<h2>AJAX</h2>
<button type="button" onclick="loadContent()">Get data</button>
<div id="myDiv"></div>
 
</body>
</html> 

```

<strong>onreadystatechange</strong> is fired when the server response is ready to be processed.
When *readyState* is 4 and *Status* Code is 200 the response is ready.

For sending request to server open(), send() methods are used.
*open(method,page_url,asyncz(true/false))*

*responseText* is the response that is the text format.

Have a look at this [example here](http://practise.comoj.com/practise.html).