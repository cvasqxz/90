---
layout: post
author: cvxz
title:  "Nic.cl Whois Scanner"
date:   2020-01-23 11:04:05 -0300
categories: python
---

{% highlight python %}
import os

for i in range(100):
    word = str(i)
    a = os.popen('whois %s.cl' % word).read()
    
    if 'no entries found' in a:
        print('%s.cl - disponible' % word)
    else:
    	# Expiration date
        date = a.split('\n')[13].split(': ')[-1]
        print('%s.cl - %s' % (word, date))
{% endhighlight %}