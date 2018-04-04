---
layout: post
title: "Video: 2D Transformations"
---

# Video: 2D Transformations

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/78667474?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Planets example

{% highlight java %}
float planetDistance[] = { // in miles
  36.0e6, // mercury
  67.2e6, // venus
  93.0e6, // earth
  141.6e6, // mars
  483.6e6, // jupiter
  886.7e6, // saturn
  1784.0e6, // uranus
  2794.4e6, // neptune
  3674.5e6 // pluto
};

float planetDiameter[] = { // in miles
  3031, // mercury
  7521, // venus
  7926, // earth
  4222, // mars
  88729, // jupiter
  74600, // saturn
  32600, // uranus
  30200, // neptune
  1413 // pluto
};

float planetSunPeriod[] = { // in days
  87.96, // mercury
  224.68, // venus
  365.26, // earth
  689.98, // mars
  4329.6, // jupiter
  10751.4, // saturn
  30685.5, // uranus
  60155.7, // neptune
  90410.5 // pluto
};

float sunDiameter = 864576; // miles

float milesPerPixel = 20e5;

int day = 0;
float framesPerDay = 0.5;

int offsetX = 0;
int offsetY = 0;

void setup()
{
  size(1800, 1000);
  background(0);
  rectMode(CENTER);
}

void draw()
{

  fill(255);
  
  translate(offsetX, offsetY);
  
  translate(width/2, height/2);
  
  ellipse(0, 0, sunDiameter / milesPerPixel, sunDiameter / milesPerPixel);
  
  for(int i = 0; i < planetDistance.length; i++)
  {
    pushMatrix();
    rotate(day / (planetSunPeriod[i] * framesPerDay));
    translate(planetDistance[i] / milesPerPixel, 0);
    float pdiam = constrain(planetDiameter[i] / milesPerPixel, 5, 500);
    ellipse(0, 0, pdiam, pdiam);
    popMatrix();
  }
  
  fill(0, 0, 0, 10);
  noStroke();
  rect(0, 0, width, height);
  
  day++;
  
  if(keyPressed)
  {
    if(key == CODED)
    {
      if(keyCode == DOWN)
      {
          background(0);
        milesPerPixel = milesPerPixel * 1.1;
      }
      if(keyCode == UP)
      {
          background(0);
        milesPerPixel = milesPerPixel * 0.9;
      }
      if(keyCode == LEFT)
      {
        framesPerDay = framesPerDay * 0.9;
      }
      if(keyCode == RIGHT)
      {
        framesPerDay = framesPerDay * 1.1;
      }
    }
  }
}

void mouseDragged()
{
  offsetX = offsetX + (mouseX - pmouseX);
  offsetY = offsetY + (mouseY - pmouseY); 
}
{% endhighlight %}

## Psychedelic example

{% highlight java %}
float r = 0.0;
float r2 = 0.0;
int d = 1;
int d2 = 1;
float zoom = 1.0;

void setup()
{
  colorMode(HSB, 360, 100, 100);
  size(800, 600); // make this bigger for more fun
  rectMode(CENTER);
}

void draw()
{
  background(0);
  noStroke();

  translate(width/2, height/2);
  scale(zoom);
  rotate(r);
  for (int i = 0; i < 100; i++)
  {
    pushMatrix();
    rotate(r*i*0.5);
    translate(i*10, 0);
    scale(i*0.05);

    for (int j = 0; j < 20; j++)
    {
      pushMatrix();
      fill(i*3.6, 100, j/2.0+50);
      rotate(i*j*0.5*r2);
      translate(j*1.5+i*0.2, 0);
      ellipse(0, 0, j*0.5, j*0.5);
      popMatrix();
    }
    r2 += d2*0.000001;

    popMatrix();
  }

  r += d*0.001;
}

void keyPressed()
{
  if(key == ' ')  // change overall rotation direction
  {
    d *= -1;
  }
  if(key == 'x')  // change each spiral rotation direction
  {
    d2 *= -1;
  }
  
  if(key == '+')
  {
    zoom = zoom * 1.1;
  }
  if(key == '-')
  {
    zoom = zoom * 0.9;
  }
}
{% endhighlight %}

## Horizontal scrolling example

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
