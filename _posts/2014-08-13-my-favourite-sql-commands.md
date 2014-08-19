---
layout: post
title: "My favourite SQL commands"
description: ""
category: 
tags: [snippets,slqserver]
---
{% include JB/setup %}

Whenever I'm in SQL Server (usually Management Studio) I allways have some good snippets in handy. I'll try to update this post as much as I can.


- Find a stored procedure you just created but don't remember:

{% highlight sql %}
SELECT name, create_date, modify_date
FROM sys.objects
WHERE type = 'P'
order by create_date desc
{% endhighlight %}

- Select all objects created by date (it will show tables also):

{% highlight sql %}
SELECT name, create_date, modify_date
FROM sys.objects
order by create_date desc
{% endhighlight %}
