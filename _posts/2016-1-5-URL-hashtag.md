---
layout: post
title: This hashtag is messing my URL
---

The url in the app is some thing like
```
xxxxx/record#1/xxxx
```
Manually clicking on this wrong URL, will get you to the correct one,
```
xxxxx/record/#1/xxxx
```
The browser(Chrome and Firefox) somehow fix the problem and the correct page is shown.

When going to this URL using automation, it went wrong.
I put the correct URL into the browser using code below:
```
browser.get('xxxx/record/#1/xxxx');
```
The video shows the browser rendered the correct page, then changes the URL to 
```
xxxx/record/#/1/xxxx
```
and then the test failed because 'NOT FOUND PAGE' is shown instead of the right one.

At first, I thought it might be the browser that is trying to change the URL according to its own rules.
After checking with Jessie and Serban(again I want to thank them very much for taking the time and being so patient to help a student worker), I think the problem is probably due to Angular's routing scheme.
I remember the routing taking advantage of '#' to prevent the browser from firing the request, and manipulate the view itself.

That looks like a good explanation, except that I still have no clue what to do to prevent the URL from changing again.

What on earth is the difference between testing using standalone Selenium and testing on Saucelabs' Selenium?
Hope I can learn more to fix this.

--------

Miraculously, this line of code works around this problem.
{% highlight javascript%}
browser.ignoreSynchronization = false;
{% endhighlight %}
This line of code tells Protractor not to sync with AngularJS(not to wait for $http to finish). 
I tried this code without really believing it would work, but it did.
So the problem was with Angular's internal mechanism which I am still unaware of.
But good thing is the problem is solved, and I can move on to test other stuff.
