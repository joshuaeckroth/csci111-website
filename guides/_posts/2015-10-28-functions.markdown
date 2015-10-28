---
layout: post
title: Functions
---

# Functions

We have seen functions before:

{% highlight java %}
void setup()
{
  // ...
}

void draw()
{
  // ...
}

void keyPressed()
{
  // ...
}

// etc.
{% endhighlight %}

We can also make our own functions. This is useful when we want to collect some code under a single name (the function's name), and then execute that code just by referring to the name ("calling the function").

## Two kinds of functions

There are really two kinds of functions: those that are `void` functions, and those that "return" values. The kind that return values cannot be `void`, they must have a type like `float` or `boolean` or whatever.

Void functions look like this:

{% highlight java %}
void setup()
{
  size(600, 600);
}

void draw()
{
  myfunction(); // call the function below
}

void myfunction()
{
  // do something, like draw stuff
  ellipse(200, 200, 50, 50);
}
{% endhighlight %}

Non-void functions look like the following. Note, you probably want to save the value they "return".

{% highlight java %}
void setup()
{
  size(600, 600);
}

void draw()
{
  float r = calculateSomething(); // call the function below
  ellipse(200, 200, r, r);
}

float calculateSomething()
{
  // this is a "float" type function,
  // so it must "return" a value with type float

  // yes, this function is useless, but below we look
  // at better examples
  return 115.75;
}
{% endhighlight %}

## Functions can have inputs, or "arguments"

Often, you want your function to calculate or draw something depending on values given to the function. The function can indicate that it wants to receive certain values:

{% highlight java %}
int x = 100;
int y = 100;

void setup()
{
  size(600, 600);
}

void draw()
{
  background(255);
  drawEllipse(x, y, 50, 25, 3);
  x++;
  y++;
}

void drawEllipse(int x, int y, int width, int height, int sw)
{
  strokeWeight(sw);
  stroke(0);
  noFill();
  ellipse(x, y, width, height);
}
{% endhighlight %}

Here is a function, with arguments, that calculates something:

{% highlight java %}
float px = 200;
float py = 200;

void setup()
{
  size(600, 600);
}

void draw()
{
  background(0);
  fill(255);
  ellipse(x, y, 50, 50);
  py = moveUp(y, 4.3); // speed is 4.3, I suppose
}

float moveUp(float y, float speed)
{
  y += speed;
  if(y < 0)
  {
    y = height; // wrap around
  }
  else if(y > height)
  {
    y = 0; // wrap around
  }
  return y; // give back the new value
}
{% endhighlight %}

## A more useful example

This example is borrowed from the textbook:

{% highlight java %}
// This program draws a "Zoog" and animates it.
// Try moving the mouse left-to-right;
// the Zoog will speed up, and its eyes will darken.

// variables accessible by all functions
float x = 100;
float y = 100;
float w = 60;
float h = 60;
float eyeSize = 16;

void setup()
{
  size(200, 200);
}
void draw()
{
  background(255);

  // Draw a black background
  // mouseX position determines speed factor for moveZoog function
  float factor = constrain(mouseX/10,0,5);
  jiggleZoog(factor);// pass in a color to drawZoog
  
  // function for eye's color
  float d = dist(x, y, mouseX, mouseY);
  color c = color(d);
  drawZoog(c);
}

void jiggleZoog(float speed) {
  // This function changes the variables
  // defined at the top of the program
  
  // Change the x and y location of Zoog randomly
  x = x + random(-1, 1)*speed;
  y = y + random(-1, 1)*speed;
  
  // Constrain Zoog to window
  x = constrain(x, 0, width);
  y = constrain(y, 0, height);
}

void drawZoog(color eyeColor) {
  
  // Set ellipses and rects to CENTER mode
  ellipseMode(CENTER);
  rectMode(CENTER);
  
  // Draw Zoog's arms with a for loop
  for (float i = y-h/3; i < y + h/2; i += 10) {
    stroke(0);
    line(x-w/4, i, x+w/4, i);
  }
  
  // Draw Zoog's body
  stroke(0);
  fill(175);
  rect(x, y, w/6, h);
  
  // Draw Zoog's head
  stroke(0);
  fill(255);
  ellipse(x, y-h, w, h);
  
  // Draw Zoog's eyes
  fill(eyeColor);
  ellipse(x-w/3, y-h, eyeSize, eyeSize*2);
  ellipse(x+w/3, y-h, eyeSize, eyeSize*2);
  
  // Draw Zoog's legs
  stroke(0);
  line(x-w/12, y+h/2, x-w/4, y+h/2+10);
  line(x+w/12, y+h/2, x+w/4, y+h/2+10);
}
{% endhighlight %}

## Another example

{% highlight java %}
int offsetX;
int offsetY;

void setup()
{
  size(600, 600);
  reset();
}

void reset()
{
  offsetX = 0;
  offsetY = 0;
}

void draw()
{
  background(0);
  for(int row = 0; row < 10; row++)
  {
    for(int col = 0; col < 10; col++)
    {
      drawEllipse(calcEllipseX(col), calcEllipseY(row), row % 2 == 0);
    }
  }
  offsetX++;
  offsetY++;
}

int calcEllipseX(int col)
{
  int x = 50*col+offsetX;
  return x;
}

int calcEllipseY(int row)
{
  int y = 50*row+offsetY;
  return y;
}

void drawEllipse(int a, int b, boolean filled)
{
  if(filled)
  {
    fill(255);
  }
  else
  {
    fill(0);
  }
  stroke(128);
  strokeWeight(5);
  ellipse(a, b, 50, 50);
}

void keyPressed()
{
  if(key == ' ')
  {
    reset();
  }
}
{% endhighlight %}

## An example with arrays

{% highlight java %}
void setup()
{
  float[] vals = generate_random_vals(100);
  float sum_of_vals = sum_array(vals);
  println(sum_of_vals);
}

// return an array
float[] generate_random_vals(int count)
{
  float[] arr = new float[count];
  for(int i = 0; i < count; i++)
  {
    arr[i] = random(0, 100);
  }
  return arr;
}

// use an array for the argument
float sum_array(float[] xs)
{
  float s = 0.0;
  for(int i = 0; i < xs.length; i++)
  {
    s = s + xs[i];
  }
  return s;
}
{% endhighlight %}

## Some rules about functions

### Functions must be defined "outside" all other functions

BAD:

{% highlight java %}
void setup()
{
  void myfunc()
  {
    // ...
  }
}
{% endhighlight %}

GOOD:

{% highlight java %}
void setup()
{
  // ...
}

void myfunc()
{
  // ...
}
{% endhighlight %}

### Functions can only use "global" variables and argument variables

In this example, the variables `x` and `y` are accessible to the function, but `g` is not.

{% highlight java %}
int x = 5;

void setup()
{
  int g = 2;
  myfunc(77);
}

void myfunc(int y)
{
  // can access x and y, but not g
}
{% endhighlight %}

### Function arguments can have any name; only the function cares about this name

{% highlight java %}
void setup()
{
  // setup calls this 'x', but it's called 'w' in the function
  int x = 77;
  myfunc(x);
}

void myfunc(int w)
{
  // function calls its argument 'w';
  // this name does not have to match the code that calls the function

  ellipse(w, w, 50, 50);
}
{% endhighlight %}

### Functions return values, not variables; the caller can name the return value whatever it wants

{% highlight java %}
void setup()
{
  // save the return value of the function as 'foo'
  float foo = myfunc(1.25);
}

float myfunc(float val)
{
  float tmp = 52 * sin(cos(val)) + 10;

  // here, the value is returned, not the variable name
  return tmp;
}
{% endhighlight %}

## What you need to know for Test 3

- How to take existing code and rewrite it with one or more functions (like Lab 8).
- How to write a `void` function that has no arguments.
- How to write a `void` function that has some arguments (of any type, perhaps an array).
- How to write a non-void function that has some arguments.
- How to write these standard functions:
  - `min`, `max` of two numbers
  - `dist`, i.e., the distance function (I'll tell you the math involved)
  - `abs`, i.e., absolute value of a number
  - `constrain`, i.e., constrain a number between two bounds
  - `min` of an array
  - `max` of an array
  - `sum` of an array
  - `printArray` to print an array

