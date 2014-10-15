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

There are really two kinds of functions: those that are `void` functions, and those that "return" values. The kind that return values cannot be `void`, they must have a type like `double` or `boolean` or whatever.

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
  double r = calculateSomething(); // call the function below
  ellipse(200, 200, r, r);
}

double calculateSomething()
{
  // this is a "double" type function,
  // so it must "return" a value with type double

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
double px = 200;
double py = 200;

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

double moveUp(double y, double speed)
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


