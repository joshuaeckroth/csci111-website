---
layout: post
title: Group project 1
due: "Fri, Oct 13, 11:59pm"
---

# Group project 1

You are required to work in a group of two people (unless I've made an exception for you). You may receive different grades. At the top of your code, in comments (`// my comment...`), describe to me how each person contributed (use each person's full name).

You are required to make a simple game, with the following elements:

- a goal
- keyboard and/or mouse control
- a way to lose
- a way to restar the game
- images
- at least somewhat visually appealing

I will approve your game design to ensure it's at the right difficulty.

Only one person needs to submit the code in the Blackboard Dropbox.

{% comment %}
## Example game ideas

## Tron example

Note, score is missing in this example. Also, it seems obvious to
include a second player, who uses WASD keys to control his/her
movements.

{% highlight java %}
int p1x = 250; // player's x location
int p1y = 250; // player's y location
int diff = 1; // difficulty; how far the player moves each frame
int p1xc = 1; // the direction of the player's movement
int p1yc = 0; // the direction of the player's movement
int p1sw = 5; // stroke weight

void setup()
{
  size(500, 500);
  background(0);
  strokeWeight(p1sw);
  stroke(255);
  frameRate(60);
}

void draw()
{
  // check if the player hits something not black, or goes out of bounds
  
  if(get(p1x + p1sw*p1xc, p1y + p1sw*p1yc) != color(0) ||
     (p1x + p1sw*p1xc) >= 500 || (p1x + p1sw*p1xc) < 0 ||
     (p1y + p1sw*p1yc) >= 500 || (py1 + p1sw*p1yc) < 0)
  {
    // here noLoop() stops the game; you can use loop() to continue the game
    // (maybe based on a keypress)
    
    noLoop(); // there seems to be a delay with this command
    textSize(28);
    fill(255);
    text("Congratulations, you died!", 100, 200);
  }
  
  line(p1x, p1y, p1x + p1xc, p1y + p1yc);
  p1x = p1x + p1xc;
  p1y = p1y + p1yc;
  
  if(frameCount % 120 == 0)
  {
    diff++;
  }
}

void keyPressed()
{
  if(key == CODED)
  {
    if(keyCode == UP)
    {
      p1xc = 0;
      p1yc = -diff;
    }
    else if(keyCode == DOWN)
    {
      p1xc = 0;
      p1yc = diff;
    }
    else if(keyCode == LEFT)
    {
      p1xc = -diff;
      p1yc = 0;
    }
    else if(keyCode == RIGHT)
    {
      p1xc = diff;
      p1yc = 0;
    }
  }
}
{% endhighlight %}

## Falling letters example

{% highlight java %}
char letter;
int x, y;
int c;
int score;
boolean lost;
int lives;
boolean paused;

void setup()
{
  size(800, 600);

  letter = char(int(random('A', 'Z'+1)));
  x = int(random(20, width-20));
  y = int(random(50, 100));
  score = 0;
  c = 1;
  lost = false;
  lives = 3;
  paused = true;
}

void draw()
{
  background(255);

  textSize(30);
  fill(0, 0, 255);
  text("Score: " + score, 50, 50);
  text("Lives: " + lives, 50, 150);

  if(paused)
  {
    
    noLoop();
    fill(255, 0, 0);
    textSize(60);
    text("Paused", 300, 300);
  }

  if (lost)
  {
    noLoop();
    fill(255, 0, 0);
    textSize(60);
    text("You lost.", 300, 300);
  }
  else
  {

    fill(0);
    textSize(40);
    text(letter, x, y);

    y += c;
    
    if(y > height)
    {
      lost = true;
    }
  }
}

void keyPressed()
{
  if ((key >= 'a' && key <= 'z') || (key >= 'A' && key <= 'Z'))
  {
    if (key == letter || key == (letter + 32))
    {
      score++;
      letter = char(int(random('A', 'Z'+1)));
      x = int(random(20, width-20));
      y = int(random(50, 100));

      if (score % 5 == 0)
      {
        c += 2;
      }
    }
    else
    {
      if(lives == 0)
      {
        lost = true;
      }
      else
      {
        lives--;
      }
    }
  }
  if(key == ' ')
  {
    paused = !paused;
    if(!paused) { 
      loop();
    }
  }
  
}
{% endhighlight %}

## Checking correct sequence of inputs

{% highlight java %}
String answer = "";
String guess = "";

void setup()
{
  size(800, 600);
  textSize(32);
  frameRate(4);
}

void draw()
{
  if (answer.length() > 0)
  {
    char currentColor = answer.charAt(frameCount % answer.length());
    if (currentColor == '1')
    {
      background(255, 0, 0);
    }
    if (currentColor == '2')
    {
      background(0, 255, 0);
    }
    if (currentColor == '3')
    {
      background(0, 0, 255);
    }
    if (currentColor == '4')
    {
      background(255, 255, 0);
    }
  }
  else
  {
    background(0);
  }
  if (answer.equals(guess))
  {
    text("Correct!", 200, 200);
  }
  text("Answer: " + answer, 200, 100);
  text("Guess: " + guess, 200, 150);
}

void keyPressed()
{
  if (key == ' ')
  {
    answer = "" + char(int(random(49, 53))) +
      char(int(random(49, 53))) +
      char(int(random(49, 53))) +
      char(int(random(49, 53)));
    guess = "";
  } else if (key == '1' || key == '2' || key == '3' || key == '4')
  {
    guess = guess + key;
  }
}
{% endhighlight %}
{% endcomment %}
