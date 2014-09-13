---
layout: post
title: Test 1 Guide Solutions
---

# Test 1 Guide Solutions

## Color

{% highlight java %}
// code to change to HSB mode
colorMode(HSB); // matches color picker values
colorMode(HSB, 100); // use 100 as max for H,S,B values

// code to set the fill color to white or black or very-light-gray
colorMode(RGB);
fill(255); // white
fill(0); // black
fill(220); // light gray
colorMode(HSB);
fill(0, 0, 100); // white
fill(0, 0, 0); // black
fill(0, 0, 80); // light gray

colorMode(RGB);
// code to set the fill color to 50% transparent dark red
fill(150, 0, 0, 128);

// code to set the background color to bright yellow or purple or cyan
background(255, 255, 0); // yellow
background(255, 0, 255); // purple (magenta)
background(0, 255, 255); // cyan

// 10 pixel stroke
strokeWeight(10);
{% endhighlight %}

## Coordinate system and shapes

{% highlight java %}
// code to draw a 4x4 square in the middle of a 50x50 window
rect(22, 22, 4, 4);

// code to draw a 4x4 square in the middle of a window of any size
rect(width/2 - 2, height/2 - 2, 4, 4);

// code to draw an ellipse that touches the four edges of a window of any size
ellipse(width/2, height/2, width, height);

// code to draw a rectangle that covers the entire window (and no more)
rect(0, 0, width, height);

// code to draw an arc from 9 o'clock to 12 o'clock
arc(200, 200, 100, 100, PI, 3*PI/2);
{% endhighlight %}

## Variables and types

- what type should be used to hold the value 55 (not 55.0)? **int**
- what type should be used to hold the value 55.5? **float**
- what type should be used to hold the value "foo bar" **String** (capitalization matters)
- what type should be used to hold the value of a single symbol that can be typed on the keyboard? **char**
- what type should be used to hold the value true or false? **boolean**

What is the result of each of the following computations?

{% highlight java %}
57 % 10       // 7 (remainder)
57 / 10       // 5 (quotient)
2.4 / 2.0     // 1.2 (floats are involved; do real division)
pow(3.0, 2.0) // 9.0
{% endhighlight %}

If we have `int x = 5`, what is the value of `x` after each of these commands:

{% highlight java %}
x--;     // now x == 4
x--;     // now x == 3
x *= 2;  // now x == 6
x++;     // now x == 7
{% endhighlight %}

If we have `boolean q = true`, what is the value of `q` after each of these commands:

{% highlight java %}
q = false;      // now q == false
q = true || q;  // now q == true
q = !q;         // now q == false
{% endhighlight %}

## Animation

Write the chunk of code (two functions) we will always include when we
start writing a program.

{% highlight java %}
void setup()
{
}

void draw()
{
}
{% endhighlight %}

The right chunk of code properly moves the triangle left-to-right,
since it increases `x`. The left chunk decreases `x`, so it moves
right-to-left, which is wrong.

Complete this code so that the ellipse starts large but shrinks over
time (its size is allowed to become negative).

{% highlight java %}
int bigness = 200;  // I can choose a different name and initial value

void setup()
{
    size(400, 400);
}

void draw()
{
    background(255);
    ellipse(50, 100, bigness, bigness + 100); // I can make it a circle or whatever
    
    bigness = bigness - 50;  // just has to decrease somehow
}
{% endhighlight %}

## Conditionals

Suppose some shapes are moving according to changing `x` and `y`
variables. Write some `if` statements that wrap-around `x` and `y` on
all sides of the window, without using the `%` (modulo) operator.

{% highlight java %}
if(x < 0)
{
    x = 400;
}
if(x > 400)
{
    x = 0;
}
if(y < 0)
{
    y = 400;
}
if(y > 400)
{
    y = 0;
}
{% endhighlight %}

Write some `if/else` statements that do the following: if `x` is
greater than the middle of the window width, then show text on the
screen that says `"Too far!"`, otherwise increase the value of `x`.

{% highlight java %}
if(x > width/2)
{
    text("Too far!", 100, 100);
}
else
{
    x++;
}
{% endhighlight %}

## Keyboard input

Write a `void keyPressed()` function that decreases the value of `y`
if you press the up key.

{% highlight java %}
void keyPressed()
{
    if(key == CODED && keyCode == UP)
    {
        y--;
    }
}
{% endhighlight %}

Write a `void keyPressed()` function that sets `x` (a `float`
variable) to a random value when the space bar is pressed.

{% highlight java %}
void keyPressed()
{
    if(key == ' ')
    {
        x = random(0, 50);
    }
}
{% endhighlight %}

## Mouse input

Write a complete program that randomly changes the background color
when the right mouse button is pressed.

{% highlight java %}
float r = random(0, 255);
floag g = random(0, 255);
float b = random(0, 255);

void setup()
{
    size(400, 400);
}

void draw()
{
    background(r, g, b);
}

void mousePressed()
{
    if(mouseButton == RIGHT)
    {
        r = random(0, 255);
        g = random(0, 255);
        b = random(0, 255);
    }
}
{% endhighlight %}

Write a complete program that draws ellipses wherever the mouse is
clicked.

{% highlight java %}
void setup()
{
    size(400, 400);
    background(255);
}

void draw()
{
}

void mouseClicked()
{
    ellipse(mouseX, mouseY, 100, 100);
}
{% endhighlight %}

Rewrite and fix this broken code that is supposed to allow the user to
drag three differently-colored 100x100 rectangular puzzle pieces over
a blue background, and gives the message "Success!" when they are
lined up so that they are all near the middle of the screen and the
red is above the green, which is above the gray.


{% highlight java %}
int x1 = 50;
int y1 = 20;
int x2 = 125;
int y2 = 75;
int x3 = 200;
int y3 = 300;

void setup()
{
  size(400, 400);
  noStroke();
}

void draw()
{
  background(20, 20, 250);
  fill(250, 20, 20);  // reddish
  rect(x1, y1, 100, 100);
  fill(20, 250, 20);  // greenish
  rect(x2, y2, 100, 100);
  fill(75, 75, 75);  // grey
  rect(x3, y3, 100, 100);

  if(x1 >= 150 && x1 <= 250 && y1 >= 50 && y1 <= 150
   && x2 >= 150 && x2 <= 250 && y2 >= 150 && y2 <= 250
   && x3 >= 150 && x3 <= 250 && y3 >= 250 && y3 <= 350)
  { 
    textSize(32);
    fill(255);
    text("Success!", 150, 200);
  }
}

void mouseDragged()
{
  if(mouseX >= x1 && mouseX <= (x1+100)
     && mouseY >= y1 && mouseY <= (y1+100))
  {
    x1 = x1 + (mouseX-pmouseX);
    y1 = y1 + (mouseY-pmouseY);
  }
  if(mouseX >= x2 && mouseX <= (x2+100)
     && mouseY >= y2 && mouseY <= (y2+100))
  {
    x2 = x2 + (mouseX-pmouseX);
    y2 = y2 + (mouseY-pmouseY);
  }
  if(mouseX >= x3 && mouseX <= (x3+100)
     && mouseY >= y3 && mouseY <= (y3+100))
  {
    x3 = x3 + (mouseX-pmouseX);
    y3 = y3 + (mouseY-pmouseY);
  }
}
{% endhighlight %}
