---
layout: post
title: dict-ratings-pickle.py
---

# dict-ratings-pickle.py

```
# This example program asks users for book ratings,
# and prints average ratings

from statistics import mean
import pickle
import os.path

if os.path.exists("book-ratings.pkl"):
    ratings = pickle.load(open("book-ratings.pkl", "rb"))
else:
    ratings = {}

def print_ratings():
    for book in ratings:
        avg = mean(ratings[book])
        print("%s: %.1f" % (book, avg))

def add_rating():
    book = input("Title? ")
    rating = int(input("Rating? (1-5) "))
    if rating == 0:
        del ratings[book]
    elif book not in ratings:
        ratings[book] = [rating]
    else:
        ratings[book].append(rating)
    

while True:
    print_ratings()
    add_rating()
    c = input("Continue? ")
    if c == "no":
        break

pickle.dump(ratings, open("book-ratings.pkl", "wb"))
```

