---
title: "Bootstrapping networks with R and igraph"
date: 2018-04-05
permalink: /posts/2018/04/bootstrapping-networks with-r-and-igraph/
tags:
  - R programming
  - networks
  - bootstrapping
  - igraph
---

Despite being quite new in this "brave new world" of R programming, I've been doing my best to dig through the depts of the internet to find good articles about some of the questions I have.

However, I often find complex lengthy articles and posts with enough code to fill a bible, which don't really shed much light into any questions, unless you're an expert in the field.
One of those questions is "how to bootstrap a network".

There are several useful R packages for that such as `bootnet` and `snowboot`. However, I have to admit that I've struggled to understand the output coming from both packages, in part due to the lack of a proper tutorial or examples. I don't doubt that they are good, but they are mostly designed to be used by experts.

The first thing we need is to create a sample network to work with.

```
library(igraph)
library(dplyr)

g <- sample_smallworld(1, 300, 5, 0.05)
```

In order to bootstrap a network, it is important to keep it's structure. The most common way of doing so is by keeping its degree distribution and swap its edges. (e.g. A - B and C - D edges, are replaced by A - C and B - D). [Hennemann (2012)](https://onlinelibrary.wiley.com/doi/full/10.1002/asi.22739)

Fortunately igraph has two good functions for that `rewire()` and `keeping_degseq()`. In this case we'll want to rewire the amount of edges in our network, 10 times. It is important to note that the igraph function runs n amount of trials, which some can be unsuccessful. However, almost 100% of the edges should be swapped.

```
g1 <- g %>%
  rewire(keeping_degseq(niter = ecount(g)*10))
```

Now that we have our resampled network, we need to repeat this n amount of times.
First we create an empty vector to store our results. Then we loop through our code 500 times, always saving our statistic of interest. I chose the graph centralisation betweenness.

{% highlight r %}
#' @export
#' @keywords internal
library(igraph)
library(dplyr)

btw <- c()
for(i in 1:500){
  gDeg <- gUnd %>%
    rewire(keeping_degseq(loops = FALSE, niter = ecount(gDeg)*10)) #Swaps edges
  btw[i] <- centralization.betweenness(gDeg)$centralization # Runs and saves statistic of interest
}

{% endhighlight %}

And that's it. It's always possible to create more vectors and more statistics depending on what you're studying. Surely after it is important to get the Confidence intervals for the bootstrapped results, but that's solely dependant on the method you're using for such.

Feel free to shoot comments or corrections to my mailbox.
