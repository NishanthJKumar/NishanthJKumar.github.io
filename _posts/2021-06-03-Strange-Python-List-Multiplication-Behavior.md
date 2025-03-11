---
layout: default
title: Strange Python list multiplication behavior.
date: 2021-06-23 00:00:01
---

I recently spent on the order of 2 hours debugging some code that it only took me 1 hour to write. This post is partially intended to be informational for a reader and partially intended to serve as a future warning/reminder for me.

Let's suppose you want to create a new Python list and initialize it with all 0's. Python provides a nice, intuitive and convenient way to do this with the `*` operator:
```
>>> my_list = [0] * 5
``` 
Great, and now you can edit/insert a value into any list index like you'd expect:
```
>>> my_list[0] = 23
>>> print(my_list)
[23, 0, 0, 0, 0, 0]
```
Now, suppose you want to kick it up a dimension and initialize a 2D list (i.e, a list of lists) with all 0's. It's only natural to use the nice and convenient `*` operator right?
```
>>> my_2d_list = [[0] * 5] * 5
```
Unfortunately, this doesn't do what you intuitively think it does. To illustrate, let's go and edit the top-left element
```
>>> my_2d_list[0][0] = 1
>>> print(my_2d_list)
[[1, 0, 0, 0, 0], 
[1, 0, 0, 0, 0], 
[1, 0, 0, 0, 0], 
[1, 0, 0, 0, 0], 
[1, 0, 0, 0, 0]]
```
Notice how not just the top-left element, but *all* elements in the first column got edited to the same value! What gives?

As it turns out, using the `*` operator to duplicate a list multiple times doesn't create new lists, but just references the same underlying list object. This is almost *never* what someone wants when making a 2D (or multi-dimensional) list. But the behavior has to be this way for compatibility reasons (as explained in [these nice StackOverflow answers](https://stackoverflow.com/questions/240178/list-of-lists-changes-reflected-across-sublists-unexpectedly)). 

If you didn't know about any of this before, don't feel bad - I'd been using the `*` operator to make Python lists for ~5 years before this and somehow never realized this particular quirk...

So, in conclusion, *never* make a more-than-1D Python list with the `*` operator. If you want to be extra safe, stop using the `*` operator to make lists at all.

If you're here because you're trying to debug strange Python behavior (hi future me!), and the quirk mentioned here wasn't at the root of it, check out [this GitHub repo](https://github.com/satwikkansal/wtfpython) for an exhaustive illustration of Python's weirdnesses.