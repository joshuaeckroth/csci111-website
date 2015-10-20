---
layout: post
title: Test 2 Guide Solutions
---

# Test 2 Guide

## Loops

Write a `for` loop that draws 100 ellipses (I don't care about the dimensions or locations of the ellipses).

{% highlight java %}
for(int i = 0; i < 100; i++)
{
  ellipse(random(0, width), random(0, height), 20, 20);
}
{% endhighlight %}

<hr/>

What is the value of `sum` after this loop is finished?

{% highlight java %}
int sum = 0;
for(int q = -5; q < 10; q--)
{
  sum += q;
  q = q + 3;
}
{% endhighlight %}

Answer: 16

<hr/>

Fill in the following blanks so that the loop sets an integer `k` to the values -10, -8, -6, ..., 6, 8, 10.

{% highlight java %}
for(______________; ______________; ______________)
{% endhighlight %}

Answer:

{% highlight java %}
for(int k = -10; k <= 10; k = k + 2)
{% endhighlight %}

<hr/>

Write a `for()` loop that computes the sum of the numbers 500, 495, 490, ..., 10, 5. Save the sum into a variable called `sum`.

{% highlight java %}
int sum = 0;
for(int i = 500; i >= 5; i = i - 5)
{
  sum = sum + i;
}
{% endhighlight %}

## Arrays

Suppose we have an array with 97 values. What is the first array "position" or "index"? What is the last index?

Answer: first position is 0, last position is 96.

<hr/>

What is the first and last position of this array:

{% highlight java %}
int[] xyz = new int[100];
{% endhighlight %}

Answer: first position is 0, last position is 99.

<hr/>

What code will tell you the number of elements in some array called `arr`?

Answer: `arr.length`

<hr/>

Create an array that can hold 100 decimal values. Don’t put any values in it.

{% highlight java %}
float[] vals = new float[100];
{% endhighlight %}

<hr/>

Create an array that can hold the names of the 50 states. Don’t put any values in it.

{% highlight java %}
String[] states = new String[50];
{% endhighlight %}

<hr/>

Create an array that can hold symbols from the keyboard. Don’t put any values in it.

{% highlight java %}
char[] symbols = new char[100]; // I guessed the size here
{% endhighlight %}

<hr/>

Using a loop, add 1 to every integer in the array arr. Don’t create the array.

{% highlight java %}
for(int i = 0; i < arr.length; i++)
{
  arr[i]++;
}
{% endhighlight %}


<hr/>

Using a loop, print in reverse all elements of the array arr, which holds integers. Don’t create the array.

{% highlight java %}
for(int i = arr.length - 1; i >= 0; i--)
{
  println(arr[i]);
}
{% endhighlight %}

<hr/>

Create an array of 100 floats and, using a loop, fill it with the number 7.7.

{% highlight java %}
float[] vals = new float[100];
for(int i = 0; i < 100; i++)
{
  vals[i] = 7.7;
}
{% endhighlight %}

<hr/>

Create an array of 100 floats and, using two loops, fill the first 50 elements with the number 2.2, and the second 50 elements with the number 9.9.

{% highlight java %}
float[] vals = new float[100];
for(int i = 0; i < 50; i++)
{
  vals[i] = 2.2;
}
for(int i = 50; i < 100; i++)
{
  vals[i] = 9.9;
}
{% endhighlight %}

<hr/>

Suppose we have:

{% highlight java %}
char q;
int w;
float[] fs;
String[] words;
boolean y;
{% endhighlight %}

What type are each of the following? When the answer is some kind of array, write "array" (not "collection" and not `[]`) as well as the type, e.g., "boolean array."

- What type is `y`? -- Answer: `boolean`
- What type is `fs[1]`? -- Answer: `float`
- What type is `words[w+1]`? -- Answer: `String`
- What type is `fs`? -- Answer: `float array`
- What type is `words`? -- Answer: `String array`
- What type is `w`? -- Answer: `int`

<hr/>

Suppose we have:

{% highlight java %}
int j;
String s;
float[] ww;
String[] t;
float r;
int[] z;
{% endhighlight %}

- What type is `s`? -- Answer: `String`
- What type is `t`? -- Answer: `String array`
- What type is `r`? -- Answer: `float`
- What type is `t[0]`? -- Answer: `String`
- What type is `t[j]`? -- Answer: `String`
- What type is `ww[3]`? -- Answer: `float`
- What type is `ww`? -- Answer: `float array`
- What type is `ww[j]`? -- Answer: `float`
- What type is `z`? -- Answer: `int array`
- What type is `ww[z[0]]`? -- Answer: `float`
- What type is `ww[z[j]]`? -- Answer: `float`

<hr/>

Suppose I want to create an array of 1000 `float` values. Write the necessary code to define such an array with the name `myvals` and set all the values in the array to `12.55`.

{% highlight java %}
float[] myvals = new float[1000];
for(int i = 0; i < 1000; i++)
{
  myvals[i] = 12.55;
}
{% endhighlight %}

<hr/>

Write code that creates an array of 2000 integers, called `oddeven`, and sets the values in "even" array positions (0, 2, ...) to `1` and "odd" array positions (1, 3, ...) to `0`. For example, `oddeven[18]` is `1` and `oddeven[19]` is `0`. (Note that you can determine if a number is even by checking if its remainder, after dividing by 2, is equal to 0.)

{% highlight java %}
int[] oddeven = new int[2000];
for(int i = 0; i < 2000; i++)
{
  if(i % 2 == 0) // even position
  {
    oddeven[i] = 1;
  }
  else // odd position
  {
    oddeven[i] = 0;
  }
}
{% endhighlight %}
  
<hr/>

Print all the words in a String array `words` as a list, with numbers in front. For example, if `words` contains only the words "cat", "hat", and "bat", in that order, then the output should be:

```
1. cat
2. hat
3. bat
```

Answer:

{% highlight java %}
for(int i = 0; i < words.length; i++)
{
  print((i+1) + ". " + words[i]);
}
{% endhighlight %}

<hr/>

Finish this code so that it finds the smallest value in the array called `xs`, and saves that value into the variable `smallest`.

{% highlight java %}
int[] xs = new int[200]; // ... the array is filled with random values;
                         // that code is intentionally not shown

int smallest = ________;

for(int i = 0; _________________; i++) {

    if(_________________)
    {
        _________________;
    }
}
{% endhighlight %}

Answer:

{% highlight java %}
int smallest = xs[0];

for(int i = 0; i < 200; i++)
{
    if(xs[i] < smallest)
    {
        smallest = xs[i];
    }
}
{% endhighlight %}

<hr/>

Complete the following code so that the array `copy` is a copy of the array `original`, i.e., it is the same size and all elements have the same values in the same order.

{% highlight java %}
float[] original = new float[100];
// original is filled with values...

float[] copy = ______________________________;

for(int j = (______________.length – 1); _____________________; j--)
{
    __________________________________________;
}
{% endhighlight %}

Answer:

{% highlight java %}
float[] copy = new float[100];

for(int j = (copy.length - 1); j >= 0; j--)
{
    copy[j] = original[j];
}
{% endhighlight %}
