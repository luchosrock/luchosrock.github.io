---
layout: post
title: "Too bored to fill a form"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Everytime I sign up to my classes I'm prompted with some silly surveys. OK, I know there are _usefull_ to evaluate last classes results but sometimes I'm just too bored to fill them. 

I often do this little trick in developer inspector console (Hit `F12` > `Console`):

Let's say there are a lot of radio buttons and I want to check all the inputs with value **5**. Just copy & paste the following line:

{% highlight javascript%}
$('input[value=5]').attr('checked','checked');
{% endhighlight%}


But what if this page has no jquery embedded? We load it:

{% highlight javascript%}
var jq = document.createElement('script');
jq.src = "//ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js";
document.getElementsByTagName('head')[0].appendChild(jq);
jQuery.noConflict();
{% endhighlight%}

This will do the trick for Firefox, but I guess it should work in Chrome too.

And that's all! At least for _radio_ _buttons_ kind of surveys. If anything else comes up I eventually update this post to keep up.

Bye.


