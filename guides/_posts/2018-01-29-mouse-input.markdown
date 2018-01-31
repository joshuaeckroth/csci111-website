---
layout: post
title: "Mouse input"
---

# Mouse input

These notes make extensive use of conditionals. Read the
[notes about conditionals](/guides/2018-01-29-conditionals.html) to
get up to speed.

## Detecting a mouse press

At any time when your program is running, the user might be holding
down a mouse button. You can detect this by referring to the special
variable `mousePressed`, which is a `boolean`, so it is `true` or
`false` and can be used in conditionals:

{% highlight java %}
void draw()
{
  if(mousePressed)
  {
    // ...
  }
}
{% endhighlight %}

## Detecting mouse buttons

When the mouse is being pressed, you can examine the special variable
`mouseButton` to determine which button is being pressed. The
possibilities are `LEFT`, `RIGHT`, or `CENTER`. Example:

{% highlight java %}
void draw()
{
  if(mousePressed && mouseButton == LEFT)
  {
    // ...
  }
}
{% endhighlight %}

## Mouse location

At any time, you can ask for the location of the mouse pointer. Use
these two variables (which are integers):

- `mouseX`, `mouseY`

You can also find out where the mouse was *at the prior frame*, using
these two variables:

- `pmouseX`, `pmouseY`

## Mouse events in separate functions

- `void mouseClicked()`

- `void mousePressed()`

- `void mouseReleased()`

- `void mouseDragged()`

- `void mouseMoved()`

- `void mouseWheel()`

## Code for demo 1: line drawing

{% highlight java %}
int linecolor = color(255, 255, 255);

void setup()
{
  size(500, 500);
  background(0);
}

void draw()
{
  stroke(linecolor);
  if(mousePressed && mouseButton == LEFT)
  {
    strokeWeight(10);
  }
  else if(mousePressed && mouseButton == RIGHT)
  {
    strokeWeight(2);
  }
  else
  {
    strokeWeight(5);
  }
  line(mouseX, mouseY, pmouseX, pmouseY);
}

void keyPressed()
{
  if(key == 'r')
  {
    linecolor = color(255, 0, 0);
  }
  if(key == 'g')
  {
    linecolor = color(0, 255, 0);
  }
  if(key == 'b')
  {
    linecolor = color(0, 0, 255);
  }
  if(key == 'w')
  {
    linecolor = color(255, 255, 255);
  }
}
{% endhighlight %}

## Code for demo 2: dragging/clicking inside a box

{% highlight java %}
int c = color(255, 0, 0);
int x = 100;
int y = 100;

void setup()
{
  size(500, 500);
}

void draw()
{
  background(0);
  fill(c);
  rect(x, y, 100, 100);  
}

void mouseClicked()
{
  if(mouseX >= x && mouseX <= (x+100) &&
     mouseY >= y && mouseY <= (y+100))
  {
    c = color(100, 0, 0);
  }
  else
  {
    c = color(255, 0, 0);
  }
}

void mouseDragged()
{
  if(mouseX >= x && mouseX <= (x+100) &&
     mouseY >= y && mouseY <= (y+100))
  {
    x = x + (mouseX - pmouseX);
    y = y + (mouseY - pmouseY);
  }
}
{% endhighlight %}


# Whack-a-mole game

{% highlight java %}
int activeMole = 1;
int score = 0;

void setup()
{
  size(700, 600);
  noCursor();
}

void draw()
{
  if(frameCount % 30 == 0)
  {
    activeMole = 1 + int(random(3));
  }
  
  background(#000000);
  
  if(activeMole == 1)
  {
    ellipse(150, 300, 150, 150);
  }
  if(activeMole == 2)
  {
    ellipse(350, 300, 150, 150);
  }
  if(activeMole == 3)
  {
    ellipse(550, 300, 150, 150);
  }
  
  textSize(32);
  text("Score: " + score, 50, 50);
  
  ellipse(mouseX, mouseY, 50, 50);
}

void mouseClicked()
{
  if(dist(mouseX, mouseY, 150, 300) <= 75) {
    if(activeMole == 1)
    {
      score++;
      activeMole = 1 + int(random(3));
    }
    else
    {
      exit();
    }
  }
  if(dist(mouseX, mouseY, 350, 300) <= 75) {
    if(activeMole == 2)
    {
      score++;
      activeMole = 1 + int(random(3));
    }
    else
    {
      exit();
    }
  }
  if(dist(mouseX, mouseY, 550, 300) <= 75) {
    if(activeMole == 3)
    {
      score++;
      activeMole = 1 + int(random(3));
    }
    else
    {
      exit();
    }
  }
}
{% endhighlight %}
