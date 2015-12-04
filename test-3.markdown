---
layout: post
title: Test 3
due:
---

# Test 3

Submit your answers on Blackboard in the usual way. You will create multiple separate programs (one per task). Upload all of these ZIP files at once when you submit.

## Task 1

Create a small program that has a function called `showMessage` that has two parameters: the message to display (e.g., "You win!"), and a boolean value indicating whether the message is an error or not. Error messages (e.g., "System fault.") should be large and red. Non-error messages should be black and smaller. The background of the window should be white. Draw the message in the center of the window (using the `width` and `height` global variables). In your `draw()` method, call this new method with any parameter values you wish.

## Task 2

Write a function that returns the product (multiplication) of all values in an array of `float` values. Create an array in `setup()` and call this function from `setup()`. Save the result and print it (with `println()`). The function itself should not print anything, only return the result.

## Task 3

Create a class that is capable of drawing a button (rectangle) with a text label inside the rectangle. You can decide the size of the rectangle and text (all buttons can be the same size, regardless of the text). The class should have fields (variables) that hold the text label and button position. The class should have a function that draws the button (label + rectangle). Create at least three buttons in your main file, with different labels and positions, and draw them using the class method.

## Task 4

Assume a class exists called `Snowflake`. Assume it has a constructor with one argument: a `float` size value. Assume it has two methods: `updatePosition()` and `drawSnowflake()`, each with no parameters. You may create this class, but you do not have to. Create a small program that creates an array of 1000 snowflakes with random sizes (in `setup()`). Then, in `draw()`, call the `updatePosition()` and `drawSnowflake()` methods on every one of the 1000 objects.

