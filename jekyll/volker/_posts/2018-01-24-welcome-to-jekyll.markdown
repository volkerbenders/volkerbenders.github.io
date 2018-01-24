---
layout: post
title:  "Formatting xml files"
date:   2018-01-24 17:50:50 +0100
categories: jekyll update
---
Sooner or later my xml files look pretty much messed up:
either too many blank lines
or
wrong indentation or...

Does this sound familiar?
Theres help:
{% highlight bash %}
$> cat messedup_file.xml |xmllint --format - |cat >  tidy_file.xml -
{% endhighlight %}
