---
layout: post
title: midterm-notes.py
---

# midterm-notes.py

```
# Variables
# They hold data.
# Every variable has a type.
x = 5 # x is an int type
print(x) # prints 5
print(type(x)) # prints int
y = 5. # y is a float type
print(type(y))
s = "hello" # s is a string type; 'hello' also works
print(type(s))
s = """long
string
with
newlines"""
print(s)
t = True
f = False
print(type(t)) # bool
print(type(f)) # bool

# Converting types
z = float(x)
w = int("55")
s = str(55.0)

# User input
x = input("Enter x: ") # x is str
x = int(input("Enter x: ")) # x is int

# Output (printing)
print("hello")
print(55.0)
print("Value: %d" % 55) # show integer ("digits")
print("Value: %.2f" % 55.5555) # show float, 2 decimals
y = 55.5555
print("Value: %.2f" % y)
a = 3
b = 4
print("Value 1: %d, value 2: %d" % (a, b))
name = "bob"
print("Name: %s" % name)

# Math operations
x = a + b
x = a - b
x = a * b
x = a / b
x = a ** b # a^b, a raised to power b, like a**2 (squared)
x += 1 # increase x
x -= 1 # decrease x
x += y # increase x by y amount
x = a % b # get remainder after dividing by b (5%2 is 1)
import math
x = math.log(a)
x = math.exp(a) # e^a
x = math.sin(math.pi)

# Functions (organize code)

# simple function
def func1():
    print("I am func1")
    
# now use the function
func1()

# function with arguments (parameters, inputs)
def func2(x):
    print("Here is x: %d" % x)

func2(55)

# set default value for parameter
def func3(x=0):
    print("Here is x: %d" % x)

# call without parameter
func3()
# call with parameter
func3(55)

# multiple parameters
def func4(x, y, z):
    print(x)
    print(y)
    print(z)

func4(1, 2, 3)

# return data from a function
def func5():
    return 100
    print("hi!") # this doesn't happen because the return

x = func5()
print(x)

def func6(x, y):
    return x**y

z = func6(2, 4)
print(z)

def ask(msg):
    x = int(input(msg))
    return x

val = ask("Enter value: ")

# Turtle graphics
import turtle
t = turtle.Turtle()
t.penup()
t.pendown()
t.forward(100)
t.right(45)
t.backward(50)
t.left(90)
t.goto(400, 800)
t.write("Hi!")
t.circle(100, 180) # half circle, 180-degrees

# Graphics with functions

def drawSquare(t, x, y, size):
    t.penup()
    t.goto(x,y)
    t.pendown()
    t.forward(size)
    t.right(90)
    t.forward(size)
    t.right(90)
    t.forward(size)
    t.right(90)
    t.forward(size)

drawSquare(t, 200, 200, 90)

# Loops

# do something a specific number of times
# this will print 0, 1, 2, 3, ..., 9
for i in range(10):
    print(i)

# print 4,6,8,10,...,18
for j in range(4, 20, 2):
    print(j)

# print a grid of numbers
for a in range(10):
    print("a: %d" % a, end = " -- ")
    for b in range(10):
        print(b, end=" ") # don't print newline
    print() # newline

# loop forever (until break)
while True:
    x = int(input("Enter number, or 0 to stop: "))
    if x == 0:
        break

# Conditionals (if/elif/else)

if True:
    print("This always prints")

# example with else
if True:
    print("This always prints")
else:
    print("This never prints")

if False:
    print("This never prints")

# example with else
if False:
    print("This never prints")
else:
    print("This always prints")

x = 5
if x == 5: # read: if x is equal to 5
    print("x is 5")
if x != 5: # read: if x is not equal to 5
    print("x is not 5")
if x < 5:
    print("x is less than 5")
if x > 5:
    print("x is greater than 5")
if x <= 5:
    print("x is less than or equal to 5")
if x >= 5:
    print("x is greater than or equal to 5")

# we can use a function that returns a bool
def greaterThan(a, b):
    if a > b:
        return True
    else:
        return False

x = 5
y = 6
if greaterThan(x,y):
    print("x is greater than y")
else:
    print("x is not greater than y")

# elif: which is same as else & if combined
# must appear after an if, might also have an else later

if x == 5:
    print("...")
elif y < 2:
    print("...")
elif y > 10:
    print("...")
else:
    print("...")

# What's the difference here?
x = 5
if x == 5:
    print("1")
if x > 0:
    print("2")

# and:

if x == 5:
    print("1")
elif x > 0:
    print("2")

# Nested if's

if x == 5:
    if y == 2:
        print("x is 5 and y is 2")
    else:
        print("x is 5 but y is not 2")

# Lists

empty = []
somestuff = [1, 5, 9]

# show length (size)
print(len(somestuff)) # prints 3

# add to end of list
somestuff.append(22)
print(len(somestuff)) # prints 4

somestuff = somestuff + [44, 55, 66]
print(len(somestuff)) # prints 7

# Slices

x = somestuff[4] # x is 44
y = somestuff[-2] # x is 55
partialstuff = somestuff[0:3] # values [1,5,9]

# Loop through list
for val in somestuff:
    print(val)

# Loop through list, version 2:
for i in range(len(somestuff)):
    print(somestuff[i])

# Build a list
mylist = []
for i in range(100):
    mylist.append(i)

# Strings are like lists

name = "Bob Smith"
print(name[0:3]) # prints Bob
print(name[0]) # prints B

# Example: adding up a list
result = 0
for val in somestuff:
    result += val
print(result)

# Another way:
result = sum(somestuff)
```

