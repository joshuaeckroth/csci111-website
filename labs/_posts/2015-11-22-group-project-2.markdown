---
layout: post
title: Group project 2
due: Dec 7, 9:00am
---

# Group project 2

Create a bigger, better game. You may extend your first group project game, but only if it is a substantial extension. **You are not allowed to create any of the typical games (Pong, Snake, Asteroids, Spacewar, Super Mario Brothers, etc.)**. Ask me about your plans if you're unsure.

You may use Fisica. In fact, I recommend it. I also recommend you use sound and music.

Your code is required to include:

- At least three functions ***in addition*** to `setup`, `draw`, `mouseClicked`, etc. (i.e., not counting all mouse/keyboard functions).

- At least one use of `PImage` and `loadImage()`.

- At least two different arrays and at least one `for()` loop that iterates through an array.

- Mouse input or keyboard input (or both).

- An opening screen that gives instructions for how to play.

- At least three levels of difficulty. The player(s) may or may not be
  allowed to choose the difficulty level.

- A way to restart after losing, e.g., by typing the "r" key or clicking a button.

- A list of scores, listed in the order they were obtained (most
  recent first). This is not a "high score" list because it does not
  have player names and all scores are kept (not just the
  highest). For space reasons, display only the most recent 5 or 10
  scores (you choose how many). Show this screen when the player loses
  (or wins). You might find the `expand()` and `shorten()` functions
  from the
  [array utilities](/videos/2014-09-29-array-utilities.html)
  video to be helpful.
  
And make your game look nice!

## Hints

Scrolling background, keeping the player in the center:

{% highlight java %}

int px = 400;
int tx = 0;

void setup()
{
  size(800, 600);
  textSize(10);
}

void draw()
{
  background(255);
  fill(0);
  
  translate(-tx, 0);
  for(int i = 0; i < 2000; i += 50)
  {
    text(i, i, 50);
  }
  ellipse(px, 400, 50, 50);
  
  if(keyPressed && key == 'a')
  {
    px -= 5;
    if(px >= width/2 && px <= 2000 - width/2)
    {
      tx -= 5;
    }
  }
  if(keyPressed && key == 'd')
  {
    px += 5;
    if(px >= width/2 && px <= 2000 - width/2)
    {
      tx += 5;
    }
  }
  px = constrain(px, 0, 2000);
  tx = constrain(tx, 0, 2000-width);

}
{% endhighlight %}