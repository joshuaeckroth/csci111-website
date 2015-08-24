---
layout: post
title: "Animation"
---

# Animation

## Required code

For now on, we'll always want to start our programs with this code:

{% highlight java %}
void setup()
{

}

void draw()
{

}
{% endhighlight %}

The `setup()` function is always executed just once. Whatever you put
between the braces (`{}`) will be executed when your program starts.

The `draw()` function is executed for each frame, and you typically
have 60 frames per second in your program. Thus, the `draw()` function
is executed very often, and putting code in that function is how you
will introduce animation.

## Variables

In order to "move" a circle, we'll draw it in one location, then erase
it with the `background()` function, then draw it in a different
location (nearby the previous location).

We'll need to know where the previous location was, and change it
slightly. Instead of drawing a circle at 200, 200 in every frame,
we'll draw it at `x, y` and change the values of `x` and `y` each
frame.

We say `x` and `y` are variables (they "vary"). A variable is just a
placeholder for a value. Processing requires that we indicate the
*type* of each variable we use. In this case, because `x` and `y` will
be pixel coordinates, we can make them integers a.k.a. `int`. Other
types are `float` for decimal values and `char` for symbols
(characters).

We'll want to "declare" our `x` and `y` variables at the top of the
program, then change their values in the `draw()` function:

{% highlight java %}
int x = 0;  // declare x as an integer and give it a starting value
int y = 0;

void setup()
{
    size(400, 400);
}

void draw()
{
    // clear the screen
    background(0);
    
    // draw a circle at x, y
    ellipse(x, y, 50, 50);
    
    // now increase x and y
    // (the circle will move down and to the right)
    x = x + 1;
    y = y + 1;
}
{% endhighlight %}

## Wrapping around the grid

Now that we have moving circles, we may want the circle to jump to the
left side of the grid when it moves past the right side, or jump to
the top of the grid when it moves past the bottom.

The problem is that `x` or `y` may grow too large. If the grid is 400
by 400, and we keep increasing `x`, eventually `x` will be larger than
400, and the circle will be off screen.

All we need to do is subtract 400 when `x` gets too large. This is the
same as dividing by 400 and just keeping the remainder. For example,
`405/400 = 1 + 5/400`, so the remainder is 5. The way we do this in
processing is with the `%` (read "mod") operator:

{% highlight java %}
int x = 0;  // declare x as an integer and give it a starting value
int y = 0;

void setup()
{
    size(400, 400);
}

void draw()
{
    // clear the screen
    background(0);
    
    // draw a circle at x, y
    ellipse(x, y, 50, 50);
    
    // now increase x and y
    // (the circle will move down and to the right)
    x = x + 1;
    y = y + 1;
    
    // make x and y wrap back around to small values if they are too large
    x = x % 400;
    y = y % 400;
}
{% endhighlight %}

When you want to wrap a complex design composed of multiple shapes, it
might be a good idea to treat the canvas as larger than it is, and
wrap around this larger canvas. That way, the complex design peeks out
from the side bit by bit rather than the whole thing appearing all at
once on other side, and disappearing all at once.

Here is an example of wrapping on a larger virtual canvas.

{% highlight java %}
int x = 0;

void setup()
{
  size(400, 400);
  rectMode(CENTER);
}
void draw()
{
  background(255);
  rect(x-150, 200, 100, 100);
  rect(x-50, 200, 100, 100);
  x = x + 5;
  x = x % (width+200);
}
{% endhighlight %}

## Random numbers

You can place a circle in random locations with the following code:

{% highlight java %}
void setup()
{
    size(400, 400);
}

void draw()
{
    // clear the screen
    background(0);
    
    // draw a circle at a random location
    ellipse(int(random(400)), int(random(400)), 50, 50);
}
{% endhighlight %}

The `random()` function has two forms:

- `random(n)` --- give a random number from `0` to `n-1`.
- `random(a, b)` --- give a random number from `a` to `b-1`.

The `random()` function gives back a `float` type. We wanted an `int`
type so we just use the `int()` function to convert it. If you give
the `int()` function a float value, it will chop off the decimal
portion in order to create an integer.

## What you'll need to know for test 1

- Know how to create a simple animation, by hand (write on paper, not
  on the computer). This requires using the `setup()/draw()`
  functions, and using variables.

- Know how to use random numbers.
