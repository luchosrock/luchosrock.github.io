---
layout: post
title: "Too bored to fill a form"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Everytime I sign up to my classes, and I'm prompted with some silly surveys. I know there are usefull to evaluate results but sometimes I'm too bored to fill them. 

I do this little trick in dev inspector console (`F12` > `Console`):

Let's say there are a lot of radio buttons and I want to check all the inputs with value *5*:

{% highlight javascript%}
$('input[value=5]').attr('checked','checked');
{% endhighlight%}


What if this page has no jquery embedded? We load it:

{% highlight javascript%}
var jq = document.createElement('script');
jq.src = "//ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js";
document.getElementsByTagName('head')[0].appendChild(jq);
jQuery.noConflict();
{% endhighlight%}

And that's all! at least for radio buttons kind of surveys. If anything else comes up I eventually update this post to keep up.

Bye.


