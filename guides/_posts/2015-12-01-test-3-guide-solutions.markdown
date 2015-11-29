---
layout: post
title: Test 3 Guide Solutions
---

# Test 3 Guide Solutions

## Functions

> 1\. Create a small program that uses a function to draw a rectangle in the middle of the screen. This function should have no arguments and no return value.

{% highlight java %}
void setup()
{
  size(800, 600);
  rectMode(CENTER);
}

void draw()
{
  background(255);
  drawMyRectangle();
}

void drawMyRectangle()
{
  rect(width/2, height/2, 200, 100);
}
{% endhighlight %}

> 2\. Create a small program that uses a function to draw a rectangle at a given x, y and width, height. These four values should be given to the function as arguments. The function has no return value.

{% highlight java %}
void setup()
{
  size(800, 600);
  rectMode(CENTER);
}

void draw()
{
  background(255);
  drawMyRectangle2(200, 400, 100, 50);
}

void drawMyRectangle2(int x, int y, int w, int h)
{
  rect(x, y, w, h);
}
{% endhighlight %}

> 3\. Write a function that returns the largest (max) number of its three arguments (all `float` values). You do not need to write an entire program to test the function (but you can if you wish).

{% highlight java %}
float max3(float a, float b, float c)
{
  if(a >= b && a >= c)
  {
    return a;
  }
  else if(b >= a && b >= c)
  {
    return b;
  }
  else // i.e., (c >= a && c >= b)
  {
    return c;
  }
}
{% endhighlight %}

> 4\. Write a function that returns the sum of all even values in an array of integers. Create an array in `setup()` and call this function from `setup()`. Save the result and print it (all in `setup()`).

{% highlight java %}    
int sumEven(int[] vals)
{
  // start our sum at 0
  int sum = 0;
  // go through all array positions
  for(int i = 0; i < vals.length; i++)
  {
    // check if 'vals[i]' is even, NOT if 'i' is even
    // ('i' is the position in the array, not the value itself)
    if(vals[i] % 2 == 0)
    {
      sum = sum + vals[i];
    }
  }
  return sum; // can't return 'sum' until loop is done
}
{% endhighlight %}

## Classes

> 5\. If you see this code, `Xyz abc;` you can safely assume (in this
> class) that we are using object-oriented programming. Which of `Xyz`
> and `abc` is the class? Which is the object? What's a good synonym
> for "class" (in our usage)? What's a good synonym for "object"?

`Xyz` is the class, because it is used in the position of a type (such
as `int`).

`abc` is the object.

Synonyms for classes include: type, category, classification,
template.

Synonyms for objects include: variable, instance, realization.

Referring to the class shown in the guide:

> 6\. Which message, if any, is printed when we do this: `Foo myfoo;` And
> what about this: `myfoo = new Foo();` And finally, what about this:
> `myfoo.f2();`

`Foo myfoo;` does nothing really, it just says the variable `myfoo`
has type `Foo`.

`myfoo = new Foo();` actually calls the constructor of the class,
resulting in `"A"` being printed.

`myfoo.f2();` calls the `f2()` method in the class, resulting in `"C"`
being printed.

> 7\. Which function is the constructor? Which message does the constructor
> print?

The constructor is always the function with the same name as the
class. The constructor prints `"A"` when it is called.

> 8\. Write the code necessary to declare and initialize an array of 200
> `Foo` objects (instances).

{% highlight java %}
Foo[] myfoos = new Foo[200];  // note, no objects exist yet!
for(int i = 0; i < 200; i++)
{
  myfoos[i] = new Foo();  // create one object at a time
}
{% endhighlight %}

> 9\. Write a class that enables the code above (not shown here) to work
> as described. You must define this class with exactly seven lines of
> code, the minimum possible (as far as I know). We count lines of
> code by ignoring blank lines and lines with only `{` or `}`, and
> using the normal coding style we have seen in this class.

{% highlight java %}
class Baz
{
  String s;
  
  Baz(String s_)
  {
    s = s_;
  }
  
  void printMany(int times)
  {
    for(int i = 0; i < times; i++)
    {
      println(s);
    }
  }
}
{% endhighlight %}

> 10\. When we are using objects, what is the most common cause of a
> "NullPointerException"?

The most common cause for us is forgetting to make an object variable
equal to a "new" instance of the class. E.g., you have:

{% highlight java %}
Foo myfoo;
{% endhighlight %}

but you forgot:

{% highlight java %}
myfoo = new Foo();
{% endhighlight %}

The program crashes (with NullPointerException error) when you attempt
to do this:

{% highlight java %}
myfoo.doSomething();
{% endhighlight %}

