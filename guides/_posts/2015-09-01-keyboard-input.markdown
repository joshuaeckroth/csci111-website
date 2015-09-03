---
layout: post
title: "Keyboard input"
---

# Keyboard input

These notes make extensive use of conditionals. Read the
[notes about conditionals](/guides/2015-09-01-conditionals.html) to
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
[conditional notes](/guides/2015-09-01-keyboard-input.html)) to
respond differently to each key. The `key` variable holds a `char`
type of value (see
[variables and types notes](/guides/2015-08-30-variables-types.html)),
so we check if it equals a particular character like `'w'`.

You can also check on these keys (they don't use the single-quote
syntax):

- `ENTER`
- `BACKSPACE`
- `TAB`
- `DELETE`

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
- `SHIFT`
- `CONTROL`
- `ALT`

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

## Multiple key presses (diagonal movement)

{% highlight java %}
int x = 200;
int y = 200;
boolean upPressed = false;
boolean downPressed = false;
boolean leftPressed = false;
boolean rightPressed = false;

void setup()
{
  size(800, 800);
}

void draw()
{
  background(0);
  fill(255);
  rect(x, y, 100, 100);
  if(upPressed)
  {
    y = y - 2;
  }
  if(downPressed)
  {
    y = y + 2;
  }
  if(leftPressed)
  {
    x = x - 2;
  }
  if(rightPressed)
  {
    x = x + 2;
  }
}

void keyPressed()
{
  if(key == CODED && keyCode == UP)
  {
    upPressed = true;
  }
  if(key == CODED && keyCode == DOWN)
  {
    downPressed = true;
  }
  if(key == CODED && keyCode == LEFT)
  {
    leftPressed = true;
  }
  if(key == CODED && keyCode == RIGHT)
  {
    rightPressed = true;
  }
}

void keyReleased()
{
  if(key == CODED && keyCode == UP)
  {
    upPressed = false;
  }
  if(key == CODED && keyCode == DOWN)
  {
    downPressed = false;
  }
  if(key == CODED && keyCode == LEFT)
  {
    leftPressed = false;
  }
  if(key == CODED && keyCode == RIGHT)
  {
    rightPressed = false;
  }
}
{% endhighlight %}

## Tron example

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

## Tron example with crash detection

{% highlight java %}
int x = 400;
int y = 300;
int dx = 1;
int dy = 0;
int speed = 1;

void setup()
{
  size(800, 600);
  background(0);
  noStroke();
  frameRate(60);
  rectMode(CENTER);
}

void draw()
{
  // if we're moving left/right (dx != 0), check left/right pixel
  // if we're moving up/down (dy != 0), check up/down pixel
  if ((dx != 0 && get(x+dx*4, y) == color(255))
    || (dy != 0 && get(x, y+dy*4) == color(255)))
  {
    textSize(32);
    fill(255);
    text("Oh no!", 200, 200);
    noLoop(); // stop the frames, stop everything
  }
  else  // we didn't lose, let's keep drawing
  {
    if (frameCount > 0 && frameCount % (60*5) == 0)
    {
      // 5 seconds have passed, let's increase the speed
      speed++;
    }

    rect(x, y, 4, 4);

    x = x + dx * speed;
    y = y + dy * speed;

    if (x < 0)
    {
      x = width;
    }
    if (y < 0)
    {
      y = height;
    }
    if (x > width)
    {
      x = 0;
    }
    if (y > height)
    {
      y = 0;
    }
  }
}

void keyPressed()
{
  if (key == CODED && keyCode == UP)
  {
    dy = -1;
    dx = 0;
  }
  if (key == CODED && keyCode == DOWN)
  {
    dy = 1;
    dx = 0;
  }
  if (key == CODED && keyCode == LEFT)
  {
    dy = 0;
    dx = -1;
  }
  if (key == CODED && keyCode == RIGHT)
  {
    dy = 0;
    dx = 1;
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

## Pong example

{% highlight java %}
int yLeft = 300;
int yRight = 300;
int ballX = 300;
int ballY = 200;
int ballDx = 3;
int ballDy = 3;
boolean wPressed = false;
boolean sPressed = false;
boolean upPressed = false;
boolean downPressed = false;
int leftScore = 0;
int rightScore = 0;

void setup()
{
  size(600, 400);
  rectMode(CENTER);
  noStroke();
}

void draw()
{
  background(0);
  fill(255);
  // draw ball
  ellipse(ballX, ballY, 30, 30);
  // draw left paddle
  rect(50, yLeft, 5, 70);
  // draw right paddle
  rect(width-50, yRight, 5, 70);
  
  // draw scores
  textSize(32);
  fill(250);
  text(leftScore, 200, 50);
  text(rightScore, 400, 50);
  
  // update ball position
  ballX += ballDx;
  ballY += ballDy;
  
  if(ballY > (height-15) || ballY < 15)
  {
    ballDy = -ballDy;
  }
  if(ballX < 0) // right player scores
  {
    rightScore++;
    ballX = 300;
    ballY = 200;
    ballDx = (int)random(-5, 5);
    ballDy = (int)random(-5, 5);
    if(ballDx == 0)
    {
      ballDx = 3;
    }
    if(ballDy == 0)
    {
      ballDy = 3;
    }
  }
  if(ballX > width) // left player scores
  {
    leftScore++;
    ballX = 300;
    ballY = 200;
    ballDx = (int)random(-5, 5);
    ballDy = (int)random(-5, 5);
    if(ballDx == 0)
    {
      ballDx = 3;
    }
    if(ballDy == 0)
    {
      ballDy = 3;
    }
  }
  
  // bounce ball off paddles
  if(get(ballX - 18, ballY) == color(255))
  {
    // hit on the left
    ballDx--;
    ballDx = -ballDx;
  }
  if(get(ballX + 18, ballY) == color(255))
  {
    // hit on the right
    ballDx++;
    ballDx = -ballDx;
  }
  
  // update left paddle position
  if(wPressed)
  {
    yLeft -= 5;
  }
  if(sPressed)
  {
    yLeft += 5;
  }
  if(upPressed)
  {
    yRight -= 5;
  }
  if(downPressed)
  {
    yRight += 5;
  }
}

void keyPressed()
{
  if(key == 'w')
  {
    wPressed = true;
  }
  if(key == 's')
  {
    sPressed = true;
  }
  if(key == CODED && keyCode == UP)
  {
    upPressed = true;
  }
  if(key == CODED && keyCode == DOWN)
  {
    downPressed = true;
  }
}

void keyReleased()
{
  if(key == 'w')
  {
    wPressed = false;
  }
  if(key == 's')
  {
    sPressed = false;
  }
  if(key == CODED && keyCode == UP)
  {
    upPressed = false;
  }
  if(key == CODED && keyCode == DOWN)
  {
    downPressed = false;
  }
}
{% endhighlight %}
