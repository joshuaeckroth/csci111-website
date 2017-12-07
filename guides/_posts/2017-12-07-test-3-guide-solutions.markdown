---
layout: post
title: Test 3 Guide Solutions
---

# Test 3 Guide Solutions

## Classes

> 1\. If you see this code, `Xyz abc;` you can safely assume (in this
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

> 2\. Which message, if any, is printed when we do this: `Foo myfoo;` And
> what about this: `myfoo = new Foo();` And finally, what about this:
> `myfoo.f2();`

`Foo myfoo;` does nothing really, it just says the variable `myfoo`
has type `Foo`.

`myfoo = new Foo();` actually calls the constructor of the class,
resulting in `"A"` being printed.

`myfoo.f2();` calls the `f2()` method in the class, resulting in `"C"`
being printed.

> 3\. Which function is the constructor? Which message does the constructor
> print?

The constructor is always the function with the same name as the
class. The constructor prints `"A"` when it is called.

> 4\. Write the code necessary to declare and initialize an array of 200
> `Foo` objects (instances).

{% highlight java %}
Foo[] myfoos = new Foo[200];  // note, no objects exist yet!
for(int i = 0; i < 200; i++)
{
  myfoos[i] = new Foo();  // create one object at a time
}
{% endhighlight %}

> 5\. Write a class that enables the code above (not shown here) to work
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

## Transformations

6\. ![Display 1](/images/test-3-guide-1.png)

{% highlight java %}
void setup()
{
    size(300, 300);
    rectMode(CENTER);
}

void draw()
{
    fill(0);
    background(255);
    translate(150, 150);
    rotate(PI/4);
    translate(150, 0);
    rect(0, 0, 20, 100);
}
{% endhighlight %}

7\. ![Display 1](/images/test-3-guide-2.png)

{% highlight java %}
void setup()
{
    size(300, 300);
    rectMode(CENTER);
}

void draw()
{
    fill(0);
    background(255);
    for(int i = 0; i < 10; i++)
    {
        pushMatrix();
        translate(i*30, 150);
        scale(0.15*i);
        rect(0, 0, 20, 100);
        popMatrix();
    }
}
{% endhighlight %}

