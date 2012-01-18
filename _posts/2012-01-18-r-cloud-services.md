---
layout: post
categories : R
tags : [R]
---
Ever since R was born (evoked?) geeks have been trying to get it to talk HTML. A list of web interfaces for R is updated on CRAN <A href="http://cran.r-project.org/doc/FAQ/R-FAQ.html#R-Web-Interfaces">here</A>. Aims are various. Some seek to replace R with a traditional GUI. Others are more ambitious and open up a glimpse of an architecture that provides live analysis of ever changing data...

Perhaps the most exciting of the architectures is <A href="http://jeffreyhorner.tumblr.com/post/4723187316/introducing-rook">Rook</A> a R web service that takes advantage of the built in web server in R.

    function(env){
      body = paste("<h1>Hello World! This is Rook",env$rook.version,".</h1>")
      list(
      status = 200L,
      headers = list(
      "Content-Type" = "text/html"
      ),
      body = body
      )
    }

    setRefClass(
      "HelloWorld",
      methods = list(
      call = function(env){
      list(
        status = 200L,
        headers = list(
        "Content-Type" = "text/html"
        ),
        body = paste("<h1>Hello World! This is Rook",env$rook.version,".</h1>")
        )
      }
      )
    )

Cool!

While I love R, however, there are some things that I'm really not sure it should be doing everything. Making toast and being a web server two of them. The joy of django and Ruby is that they do stuff for you like look after cross site validation forgery requests. I'm a whizz with R, but I wouldn't know where to start with those ones...

Anyhow, if the architecture exists where are the applications?

Over at Cambridge we have the brilliant <A href="http://www.psychometrics.cam.ac.uk/news.41.htm">Concerto</A> which makes writing an adaptive test using <A href="http://cran.r-project.org/web/packages/catR/index.html">catR</A> a breeze. It really is worth a go. They will even host a demo account for you.

Elsewhere Jeroen Ooms cuts a lonely figure in R web services. Linear models and ggplots in web interfaces. Check them out <A  href="http://www.stat.ucla.edu/~jeroen/">here</A> and how he did it <A href="http://www.stat.ucla.edu/~jeroen/files/barug2010.pdf">here</A>.

But where are the applications reaching critical mass? Where is the Ruby, django R integration work going on?





