---
layout: post
title: "My favourite SQL commands"
description: ""
category: 
tags: [snippets,slqserver]
---

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

- Find functions by name (`funName` is the name) :

{% highlight sql %}
SELECT name AS function_name
,SCHEMA_NAME(schema_id) AS schema_name
,type_desc
FROM sys.objects
WHERE type_desc LIKE '%FUNCTION%'
and name like '%funName%'
{% endhighlight %}

- Find text in stored procedures (it's helpful if you want to know wich object calls a function or procedure).

{% highlight sql %}
SELECT OBJECT_NAME(object_id) 'object_name',
       OBJECT_DEFINITION(object_id) 'definition'
FROM sys.procedures
WHERE OBJECT_DEFINITION(object_id) LIKE '%wordyouwanttofind%'
{% endhighlight %}

- Rename a column 

{% highlight sql %}
EXEC sp_rename 'table_name.old_name', 'new_name', 'COLUMN'
{% endhighlight %}
