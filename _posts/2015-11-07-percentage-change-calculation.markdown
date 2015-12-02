---
layout: post
title:  "How much got increased ? Is it so complex to calculate ???"
date:   2015-11-07 22:21:54 +0530
categories: maths change-percentage
---

Recently we calculated the increase in percentage for prices between current month and previous month. It was a simple math and as an engineer, the formula was on top of my head and coded it as below,

{% highlight ruby %}
percentage = (current_price - previous_price) * 100 / previous_price
{% endhighlight %}

This is straight forward and it says, how much is the change in price with respect to the previous price. It worked like a charm till we faced the issue where previous_price was < 0. We simply ignored it as data issue as the price can t be less than 0. But when we do the percentage in change for margin and other values where negative is allowed, our ship was destroyed. Because math got weird with 0,

eg: 
{% highlight ruby %}
current_margin = 0
previous_margin = -1.1

percentage = 0 - (-1.1) * 100 / -1.1
percentage = 100 %

{% endhighlight %}
lets take another case where

{% highlight ruby %}
current_margin=1.1
previous_margin = -2.2

then percentage = 300 %

{% endhighlight %}

I ll show the absurd nature of maths in a tabular format,

| sno 	| previous_margin| current_margin 	 	| percentage 	|
|:------|----------------|----------------------|---------------|
|1  	|-1.1            | 0              		| 100       	|
|2  	| 0              | 1.1            		| 100       	|
|3  	| -1.1           | 1.1            		| 200       	|
|4  	| -2.2           | 1.1            		| 300       	|
|5  	| 4              | 2              		| 200       	|
|6  	| -2             | -4             		| 50        	|


I had chosen these 6 rows because they represent 3 key points,

1. Whatever might be your current value is, if you started from nothing (0) then the max you can reach is 100%
2. Whatever might be your previous value is, if you have nothing (0) in your hand now then you have lost only 100%
3. If you increased the quantity from 2 to 4 then the change is 200% improvement whereas if you increased the quantity from -4 to -2 then its only 50% improvement!!! In other words, to improve from 2 to 4 you have to put lot of effort compared to the improvement from -4 to -2. 

Had a silly feeling that whatever might be the direction (2 to 4 or -2 to -4), proceeding towards zero always requires less effort whereas moving away from zero always requires more effort. 

There might be some complex mathematical explanation behind this, but as a layman engineer I felt i should note down these points, so that in future if i happen to see the same pattern again, then could generalize it and could find the behaviour of maths.