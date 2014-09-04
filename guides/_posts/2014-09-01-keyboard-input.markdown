---
layout: post
title: "Keyboard input"
---

# Keyboard input

These notes make extensive use of conditionals. Read the
[notes about conditionals](/guides/2014-09-01-conditionals.html) to
get up to speed.

## A new special function

To detect keypresses, we'll need to create the function
`void keyPressed()`, like so:

{% highlight java %}
void setup()
{

}

void draw()
{

}

void keyPressed()
{

}
{% endhighlight %}

Whatever code is inside the `keyPressed()` function will be executed
when the user presses (and releases) on the keyboard. At this point,
we can use the special variable `key` to figure out which key was
pressed:

{% highlight java %}
int x = 200;
int y = 200;

void setup()
{
  size(400, 400);
}

void draw()
{
  background(255);
  fill(0);
  ellipse(x, y, 50, 50);
}

void keyPressed()
{
  if(key == 'w')
  {
    y = y - 10;  // decrease y coordinate, i.e., "move up"
  }
}
{% endhighlight %}

Notice we need an `if` conditional here (see
[conditional notes](/guides/2014-09-01-keyboard-input.html)) to
respond differently to each key. The `key` variable holds a `char`
type of value (see
[variables and types notes](/guides/2014-08-29-variables-types.html)),
so we check if it equals a particular character like `'w'`.

## Coded key presses

Special keys, like up, down, control, shift, etc. cannot be detected
with characters like `'w'`. Instead, we have to check if the `key`
variable has the special value `CODED`, and if so, check what kind of
coded key it is by examining the `keyCode` variable:

{% highlight java %}
if(key == CODED)
{
  if(keyCode == UP)
  {
    y = y - 10;
  }
}
{% endhighlight %}

Here are some more key codes, for use in `if(keyCode == XYZ)` (change
`XYZ` to one of the following):

- `UP`, `DOWN`, `LEFT`, `RIGHT`
- `ENTER`
- `BACKSPACE`
- `DELETE`
- `SHIFT`
- `CONTROL`
- `ALT`
- `TAB`

## A simple movement example

{% highlight java %}
int x = 200;
int y = 200;

void setup()
{
  size(400, 400);
}

void draw()
{
  background(255);
  fill(0);
  ellipse(x, y, 50, 50);
}

void keyPressed()
{
  println(key);
  if(key == 'w') // up
  {
    y = y - 10;
  }
  if(key == 's') // down
  {
    y = y + 10;
  }
  if(key == 'a') // left
  {
    x = x - 10;
  }
  if(key == 'd') // right
  {
    x = x + 10;
  }
  
  if(key == CODED)
  {
    if(keyCode == UP)
    {
      y = y - 10;
    }
    if(keyCode == DOWN)
    {
      y = y + 10;
    }
    if(keyCode == LEFT)
    {
      x = x - 10;
    }
    if(keyCode == RIGHT)
    {
      x = x + 10;
    }
  }
}
{% endhighlight %}

## Snake example

{% highlight java %}
int y = 0;
int x = 200;
int dy = 1;
int dx = 0;
int speed = 1;
float h = random(0, 100);

void setup()
{
  size(400, 400);
  rectMode(CENTER);
  colorMode(HSB, 100);
  textSize(48);
  background(0, 0, 0);
  noStroke();
}

void draw()
{
  fill(h, 100, 100);
  rect(x, y, 10, 10);
  x = x + dx;
  y = y + dy;
  
  if(x < 0 || x > 400 || y < 0 || y > 400)
  {
    fill(0, 0, 100);
    text("Oh no!", 150, 200);
  }
}

void keyPressed()
{
  if(key == ENTER)
  {
    h = random(0, 100);
  }
  if(key == ' ')
  {
    speed = speed + 1;
  }
  if(key == 'w' || (key == CODED && keyCode == UP))
  {
    dy = -speed;
    dx = 0;
  }
  if(key == 's' || (key == CODED && keyCode == DOWN))
  {
    dy = speed;
    dx = 0;
  }
  if(key == 'a' || (key == CODED && keyCode == LEFT))
  {
    dy = 0;
    dx = -speed;
  }
  if(key == 'd' || (key == CODED && keyCode == RIGHT))
  {
    dy = 0;
    dx = speed;
  }
}
{% endhighlight %}

## Guessing game example

{% highlight java %}
int answer = (int)random(0, 5);
float h = 50;
boolean win = false;
boolean badguess = false;

void setup()
{
  size(400, 400);
  rectMode(CENTER);
  colorMode(HSB, 100);
  textSize(32);
}

void draw()
{
  background(0, 0, 100);
  fill(0, 0, 0);
  if(!win)
  {
    if(badguess)
    {
      text("Bad guess!", 50, 100);
    }
    text("Guess the number", 100, 200);
  }
  else
  {
    text("You win!", 100, 300);
  }
}

void keyPressed()
{
  if((key == '0' && answer == 0)
     || (key == '1' && answer == 1)
     || (key == '2' && answer == 2)
     || (key == '3' && answer == 3)
     || (key == '4' && answer == 4)
     || (key == '5' && answer == 5))
  {
    win = true;
    badguess = false;
  }
  else
  {
    badguess = true;
  }
}
{% endhighlight %}
