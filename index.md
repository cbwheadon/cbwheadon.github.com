---
layout: page
title: Psychometrics in R, JAGS and WinBUGS, with some Python thrown in... oh.. and it's in the cloud ...
header: 
tags : [R]
---

Psychometrics...

Qu'est-ce que c'est?

Say psychometrics to people and they think IQ tests. Fair enough.

I think <A href="http://cran.r-project.org/web/packages/eRm/eRm.pdf">eRm</A>:

    # Rasch model with beta.1 restricted to 0
    data(raschdat1)
    res <- RM(raschdat1, sum0 = FALSE)
    print(res)
    summary(res)
    res$W

The joy of fitting your first Rasch model in R is unparallelled. Go on try, it. Hmmm... a list of numbers. No idea what they mean?

ok. so you take an IQ test. How do we know how clever you are? We've fitted a model to the test, and the model tells us. Ah, but what interests
a pyschometrician is the residuals. What the model doesn't tell us. You may not fit our model. Interesting. Perhaps we need different questions for you, or perhaps we need a different model (sorry Benjamin Wright). In the old days that would mean expensive software where you spend days figuring out that 0 is not allowed as a valid response. Really?

Ah, R has an answer. And I love R. I mean really love R. ltm. Eat your heart out with generalised models. Only now the misfit is getting quite obscure. I know longer know if you fit or the items fit because there is a distribution of a statistic that Sitjsma has told me has certain properties, but I have no way of following his proof.

And so to Bayes, to JAGS, to WinBUGS, RJags, R2WinBUGS and models that have an elegance that was undreamt of before Gibbs sampling. Models galore: <A href="http://www.jstatsoft.org/v36/c01/paper">S. Mackay Curtis</A> and the testlet model. Now my items can live within testlets!

    model {
     for (i in 1:n){
     for (j in 1:p){
     Y[i , j] ~ dbern ( prob [i , j])
     logit ( prob [i , j]) <- alpha [j] * ( theta [i] - delta [j ] + gamma [i,d[j]])
    }

     theta [i] ~ dnorm (0.0 , 1.0)

    for (k in 1:n.t){
     gamma [i , k] ~ dnorm (0.0 , pr. gamma [k])
    }
     gamma [i , n.t + 1] <- 0.0
    }

    for (j in 1:p){
     alpha [j] ~ dnorm (m.alpha , pr. alpha ) I (0.0 , )
     delta [j] ~ dnorm (m.delta , pr. delta )
    }
     pr. alpha <- pow(s.alpha , -2)
     pr. delta <- pow(s.delta , -2)

    for (k in 1:n.t){
     pr. gamma [k] ~ dgamma (a. sigsq .gamma , b. sigsq . gamma )
     sigsq . gamma [k] <- 1.0 /pr. gamma [k]
     }
    }
  	
So you fit your model. And you load up your data. And you iterate. And iterate. And iterate. Minutes turn to hours turn to days. And if you are on Windows you have rebooted six times to install security updates. There must be a better way. Enter stage left Django, Python rpy2 and the cloud...

Follow me into the cloud...
	
	
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


