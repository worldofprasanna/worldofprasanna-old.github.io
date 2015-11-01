---
layout: post
title:  "Swapping variables using Ruby"
date:   2015-11-01
categories: ruby programming parallel-assignment
---

Swapping 2 numbers is the often asked interview question to see how many ways you know to swap and also to check your technical depth in the core area. There would be lot of technics like using temp variable, using XOR operator and if it was just numbers using addition and subtraction would do the need.

But in ruby I found this interesting piece called parallel assignment to swap 2 numbers, not only to swap but also to shift the values of variables. Let me show you an example,

{% highlight ruby %}
a = 10
b = 15

a,b = b,a # Nice way to swap right ??? and this means assign parallely
print "a=#{a}, b=#{b}" #=> a=15, b=10
{% endhighlight %}

No temp, no XOR just swapping. Let me show you another example,

{% highlight ruby %}
a=10
b=15
c=25

a,b,c=b,c,a

print "a=#{a}, b=#{b}, c=#{c}"" #=> a=15, b=25, c=10
{% endhighlight %}

In parallel assignment, values in the right hand side acts as arrays and each and every value is assigned to the variable in the LHS. So it means we can use arrays as RHS in PA and the values which don t have corresponding variables will be left out and variables which don t have corresponding values will be nil.

{% highlight ruby %}

a,b,c=[1, 2, 3, 4] # 4 will not be stored anywhere
a,b,c=[1, 2] # value of c is nil
a, *b = [1, 2, 3, 4]
print a, b #=> a=1, b=[2, 3, 4]

{% endhighlight %}

Using splat operator we can capture the rest of values to be an array.

And for the sake of preserving other techniques here,

Temp Variable :

{% highlight ruby %}
a=10
b=20

t = a
a = b
b = t
{% endhighlight %}

Xor :

{% highlight ruby %}
a = 10
b = 20

a ^= b ^= a # Java Code
{% endhighlight %}

Using basic math :

{% highlight ruby %}
a = 10
b = 20

a = a + b # means we are having both a, b in 'a'
b = a - b # remove b from {a, b}, so we ll get only a
a = a - b # remove a from {a, b}, so we ll get b. Remember because of last step, current b is the a. Hence remove a using b ;-)
{% endhighlight %}
