---
layout: post
title: "Getting started with Ajax"
comments: true
permalink: "getting-started-with-ajax"
---

*Hello people!* It's been long time since the last post, i was bit busy with the work and all, today i'm going to 
take you through how things go in Ajax. So, let's get started.

## What on earth is Ajax ?

Ajax - Asynchronous JavaScript and XML
It's a new way of using existing standard, Ajax got popular when Google started using it in 2005 for suggest in [Google Search](https://www.google.com), [Google Maps](https://www.google.com/maps) and [Gmail](https://www.gmail.com).

It's a way of exchanging data with the server without reloading the entire page. Classic pages load the entire page when a request is sent 
form the browser

## So, How does Ajax Work ?

* When an **HTML DOM events** is occured an `XMLHttpRequest` Object is created by the browser and it sends `HttpRequest`.

* Server Process the `HttpRequest`, sends back the response text and the data in the form of `XML` or `Plain Text`.

* Now Browser process the received data using `JavaScript` and the content is updated.


## Simple example on Ajax with JavaScript

**HTML Snippet**

{% highlight html %}

   <!DOCTYPE html>
   <html>
   <head>
   <script>
    function loadContent()
    {
    var xmlhttp;
    if (window.XMLHttpRequest)
      {
            // This code if for IE7+, Firefox, Chrome, Opera, Safari
            xmlhttp=new XMLHttpRequest();
       }
    else
      {
            // IE5,6 doesn't XMLHttpRequest object  they have ActiveXObject Instead
            xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
      }
      xmlhttp.onreadystatechange=function()
      {
          if (xmlhttp.readyState==4 && xmlhttp.status==200)
                {
                    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
                }
      }
    // here we use GET method, hello.php is a page sitting on the server,   
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

{% endhighlight %}

**onreadystatechange** is fired when the server response is ready to be processed.
When `readyState` is 4 and `status` Code is 200 the response is ready.

For sending request to server open(), send() methods are used.
*open(method,page_url,asyncz(true/false))*

`responseText` is the response that is the text format.

Have a look at this [example here](http://practise.comoj.com/practise.html).

## Ajax with jQuery

`jQuery` had made life so easy, `ajax` code can be written in a single line, jQuery team had taken care of everything
there is no need to write code for different browsers.

Using `jQuery` methods we can request many forms of data like `HTML`,Plain Text, `XML` or `JSON` using `GET` or `POST` methods.
Best part is we can load content directly into HTML elements in a page.

## jQuery load() method

This method is used load content directly into `html` elements.

**Syntax**


{% highlight js %}
   $(selector).load("file.txt"); 
{% endhighlight %}
**Example**

{% highlight html %}
   <!DOCTYPE html>
   <html>
   <head>
   <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
   <script>
   $(document).ready(function(){
        $("button").click(function(){
        
               // loads the content of HTML page into the div
               $("div").load("index.html");
               
        });
   });
   </script>
   </head>
   <body>

   <h2>jQuery AJAX adds content below me</h2>
   <div></div>
   <button>Get Content</button>

   </body>
   </html> 
{% endhighlight %}

Have a look at this [example here](http://practise.comoj.com/ajaxLoad.html).

## jQuery get()/post() method

This is similar to the one which we have done above with `javascript` but the entire thing is done in
a single line. 

**Syntax**

{% highlight js %}
   $.get(page_url,callback); 
{% endhighlight %}

`callback` is executed after getting the content from the page.

**Example**

{% highlight html %}
   <!DOCTYPE html>
   <html>
   <head>
   <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
   <script>
    $(document).ready(function(){
        $("button").click(function(){
        
            // Using Ajax in jQuery with GET, similarly post can be used.
            $.get("hello.php",function(data,status){
    
                    // loads the content of php page into h2
                    $("h2").html(data);
                    
            });
        });
    });
   </script>
   </head>
   <body>

   <h2></h2>
   <button>HTTP GET</button>

   </body>
   </html>   
{% endhighlight %}

Have a look at this [example here](http://practise.comoj.com/ajaxGet.html).

In addition to the above two methods we have various methods to perform ajax operations in our pages, as it was a basic 
article i would like to make it simple. In the next article i will show you how to make an `ajax call` to the `REST API` that is sitting on a third-party server.


Thanks for reading
cheers.

{% include twitter_plug.html %}
