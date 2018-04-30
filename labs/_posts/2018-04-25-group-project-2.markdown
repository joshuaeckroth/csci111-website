---
layout: post
title: Group project 2
due: "Sat May 5, 11:59pm"
---

# Group project 2

Create a bigger, better game. You may extend your first group project game, but only if it is a substantial extension. You may work by yourself or in a group of 2. You may use Fisica. In fact, I recommend it.

During May 2 class, each group demonstrates their game.

Your code is required to include:

- Images for all visual aspects of your game, or complex Processing shapes.

- Mouse input or keyboard input (or both).

- An opening screen that gives instructions for how to play.

- Increasing difficulty (either player chooses or it gets harder over time).

- A way to restart after losing, e.g., by typing the "r" key or clicking a button.

- A score that shows as you play.
  
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

