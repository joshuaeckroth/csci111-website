---
layout: post
title: Conditionals
---

# Conditionals

In most programs, we want to execute different actions depending on
certain conditions. For example, if the user presses a particular key,
or clicks the mouse, we want something to happen. Or if the user
scores 1000 points, we want to show a win screen.

We do this with `if` conditionals, like so:

{% highlight java %}
if(true)
{
  rect(0, 0, 100, 100);
}
{% endhighlight %}

That piece of code is essentially useless. The test for the `if` is
just `true`, so it's always comes out true. Usually, we want to check
on variables:

{% highlight java %}
if(x > 5)
{
  rect(0, 0, 100, 100);
}
{% endhighlight %}

Now the rectangle will only be drawn if the variable `x` is greater
than 5.

You can write `else` after an `if` to handle cases when the `if` test
comes out false:

{% highlight java %}
if(x > 5)
{
  rect(0, 0, 100, 100);
}
else
{
  ellipse(0, 0, 100, 100);
}
{% endhighlight %}

You can put `if`'s inside `if`'s, as deep as you wish:

{% highlight java %}
if(x > 5)
{
  if(x <= 10)
  {
    rect(0, 0, 100, 100);
  }
}
else // i.e., x <= 5
{
  if(x < 0)
  {
    ellipse(0, 0, 100, 100);
  }
}
{% endhighlight %}

In that example, the rectangle is only drawn if `x` has one of these
values: 6, 7, 8, 9, 10. This is because the rectangle is only drawn if
both top `if`'s are true. And the ellipse is only drawn if `x` has one
of these values: 1, 2, 3, 4, 5. This is because the first `if` has to
be false, so that we're in the `else`, and the inside `if` needs to be
true.

Here is a more practical use. This program restarts the rectangle at
the top of the screen if it goes past the bottom (a kind of wrapping
around):

{% highlight java %}
int y = 0;

void setup()
{
  size(400, 400);
  rectMode(CENTER);
}

void draw()
{
  background(255);
  fill(0);
  rect(200, y, 100, 100);
  
  y = y + 1;
  
  if(y > 400)
  {
    y = 0; // reset y if it's too large
  }
}
{% endhighlight %}
