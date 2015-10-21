---
layout: post
title: Test 2
due:
---

# Test 2

Submit your answers on Blackboard in the usual way. You can upload multiple files at once.

## Task 1

1. What code will tell you the size of an array named `xs`?
2. If an array has 130 elements, what is the last valid index?
3. Suppose we have:

```
char[] symbols;
int[] positions;
int counter;
```

What type is each of the following? For arrays, say `float array` or similar.

- `positions`
- `symbols[5]`
- `positions[counter]`
- `counter`
- `symbols[positions[counter]]`


## Task 2

Write a `for()` loop that computes `15*14*13*...*3*2*1` (which should equal 2004310016). Use a `println` after the loop to print the final number. You can write this all in `setup()`.

## Task 3

Write a program that draws a grid of small ellipses (at least 5 rows and 7 columns, but you can choose how many). The fill color of the ellipses should change every row. One possibility is to alternate among two colors on odd/even rows. You choose the colors; alternating white and black is fine. The ellipses should not overlap or touch each other. Use one or more loops.

## Task 4

Create 50 small squares with random fill colors. The colors should not change once the program starts. Their positions start random. Allow the user to drag each box around the screen. It is acceptable that multiple boxes are dragged together whenever they overlap (it would be difficult to prevent this). Feel free to look at the code for mouse dragging at the bottom of the [mouse input notes](/guides/2015-09-01-mouse-input.html) (the `mouseClicked()` code in that example is not needed). It should be obvious that you'll need some arrays to complete this task.

