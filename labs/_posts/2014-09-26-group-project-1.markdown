---
layout: post
title: Group project 1
due: Oct 8, 11:59pm
---

# Group project 1

Watch the videos about
[game design 1](/videos/2014-09-26-game-design-1.html) and
[game design 2](/videos/2014-09-26-game-design-2.html). Read the notes
about [images](/guides/2014-09-26-images.html).

You are required to work in a group of two people (unless I've made an
exception for you). You will both receive the same grade. At the top
of your code, in comments (`// my comment...`), describe to me how
each person contributed (use each person's full name). If there is a
big disparity in contributions, your grades will not be equal.

You are required to make a simple game, with the following elements:

- a goal
- score (shown on the screen)
- difficulty levels (at least 3)
- a way to lose; losing stops the game
- visually appealing
- at least one keyboard function: `keyPressed`, `keyReleased`, and/or
  `keyTyped`
- at least one mouse function: `mousePressed`, `mouseReleased`,
  `mouseClicked`, and/or `mouseDragged`
- at least three images; check out
  [opengameart.org](http://opengameart.org) for possible images; be
  sure to write a comment in your code indicating where you found your
  images

You cannot copy the games developed in the videos or the class
examples below.

Only one person needs to submit the code in Blackboard. Include both
of your names in the code, in a comment, like so:

{% highlight java %}
// Created by: Albert Einstein & Joshua Eckroth

void setup()
{
  ...
{% endhighlight %}

## Example game ideas

These ideas have been implemented and can only be used for
inspiration. They are also very incomplete:

- Candy catch (from the [game design 1](/videos/2014-09-26-game-design-1.html) video)
- Touch blinky (from the [game design 2](/videos/2014-09-26-game-design-2.html) video)

You can use any of these ideas:

- dodge ball
  - player A throws circles and player B has to dodge them
  - both players stay on same x position, use up-down or w-s keys
- pong
- missile command
  - lines aiming randomly from top to bottom
  - shoot at some angle
  - detect if it "hits" a line
- space invaders
  - move along bottom
  - shoot alien ships
- frogger
- minesweeper
- sudoku

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
