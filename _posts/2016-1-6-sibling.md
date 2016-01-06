---
layout: post
title: How to find the sibling element?
---

I have a table like this, which consists of a list of ng-repeat <tr> elements.
Each row has one general title, like "description" or "type", and one detail for the title.
I want to locate the detail <td> so that I can test it to be non-empty (some it really has some content in it). But I can't find it directly because I don't know about what's in the content.
But I can utilize the general title to locate this row, which will get me to the content <td>. What I have to use ```by.cssContainingText('class or id', 'description')```. 
Then I can use xpath to find the sibling of title <div>, that is the content <div> I am looking for.
The html is like this:
{% highlight html %}
<tr ng-repeat="ddd">
    <td>Description</td>
    <td>content and a blob of text...</td>
</tr>
{% endhighlight %}

To find the sibling of title <td>, I use 

{% highlight html %}
(by.xpath('following-sibling::div'));
{% endhighlight %}


A similar situation could be like this:
{% highlight html %}
<div class="div_i_want_to_get">
    <p></p>
    <p></p>
    <div class="div_i_can_get"></div>
    <p></p>
</div>
{% endhighlight %}

Find the <div> element inside the parent <div>, then use xpath '..' to find the parent <div> element.

