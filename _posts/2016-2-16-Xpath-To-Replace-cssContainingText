---
layout: post
title: Use XPath to replace Protractor's by.cssContainingText()
---

I tried to match one element using Protractor's 
```
by.cssContainingText()
``` method. Problem is that I find more elements than I wanted.

I wanted to find 'Mouse Gene', but the search ended up giving me 'Mouse Gene' and 'Mouse Genetic Type'. What I want is a method that can match exactly the text in the element. I couldn't find such a method in Protractor. After several failed attempts to implement a function myself, it occurred to me that jQuery has a 'contains' method. Tried it in Chrome console, works. But it was not working in Protractor. Because that 'contains' method of jQuery is not part of CSS3 specs.

Finally, it dawned on me that XPath might provide the same functionality, tried it, and it worked. Not an expert on XPath, still has a lot to learn, but the line below is more than enough for the job.
```
element(by.xpath('//td[.="' + entityName + '"]'));
```
