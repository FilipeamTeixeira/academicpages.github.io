---
title: 'Skynet - an R love hate story - Paragraph II'
date: 2018-03-18
permalink: /posts/2018/03/Skynet-story-paragraph-II/
tags:
  - R programming
  - Skynet
  - Spatial modelling
---


## Lying to myself. The creative process behind learning R

I admit it. I've lost some sleep while trying to learn R. I felt stupid, I felt that a comma would put me into a coma, but not everything was hard work, highly intellectual tasks and a deep understanding of R. Instead, I would easily say that a big part of it, probably more than I would like to admit, was pure luck and writing bits of code I still don't understand what they really do.

That's the part of science most researchers aren't keen to admit. Science is not something we do while seating in leather chairs, while smoking a cigar and drinking scotch. There's no classical music playing on the background and most researchers have no idea what Marxism is. Part of being a researcher means wearing sweatpants, drinking unhealthy amounts of coffee, and hating your office colleague for typing too loud.

So that somehow creative process doesn't always exist as we imagine it. It's just something which simply happens while watching "The Flash" or while actually working.

### Learning

Learning R was done by parts. I first tried to create my own code. I started with small problems and short bits of code, and progressed to more complex things.
One of the most important things I can think of is to look at good and well written bits of code, and do the same with yours. Some of the best and better documented packages, have a proper syntax, which allows you to learn often better than with some available books.


{% highlight r %}
#' @export
#' @keywords internal
group_by_prepare <- function(.data, ..., .dots = list(), add = FALSE) {
  new_groups <- c(quos(...), compat_lazy_dots(.dots, caller_env()))

  # If any calls, use mutate to add new columns, then group by those
  .data <- add_computed_columns(.data, new_groups)

  # Once we've done the mutate, we need to name all objects
  new_groups <- exprs_auto_name(new_groups, printer = tidy_text)
{% endhighlight %}

_From Dplyr package code._

### Documenting
Always but always document your code. Being with frustration remarks (don't forget to remove them later), being with what a certain bit of code really does.
This is one of the most important parts of coding and learning R as it will allow you to understand why you did what you did. I often made the mistake of not doing that to late regret with sweat, tears and some emotional binge eating.


### Ask questions
I've mentioned stackoverflow before. Ask a lot of questions there. If you don't want to be exposed to the cruelty of the internet, ask a colleague or a specialist working for your university.


### Backup your stuff
We're not in 1931 so backup your stuff. I know it sounds absurd to have to mention this but, I can't even tell how many researchers I've met who ended up losing weeks or even months of work for not backing up their data.
Github is a good way of sharing code, but as well to actually leave it in the cloud.

### Write it down on paper
This is a personal preference. However, I still love to write down things either in pseudocode, or simply just R code on paper. It trains your memory, speeds up the process whenever you don't have a computer in front of you, and it makes you definitively a better person.

### Practice, practice, practice.
Never ever stop. Not even when you think that life is miserable now that you have to code in R. You might think that the black plague and all that stuff with the dark ages was awesome compared to what you've been experiencing, but you'll soon realise that you're wrong.
If I could do it, so can you.

I know that this isn't much, but I'll soon post some extra tips and tricks which helped me a lot in R, so feel free to reach me, test my code, and please be critical. I have enough Portuguese wine to cope with ~~all~~ most criticism in the world.
