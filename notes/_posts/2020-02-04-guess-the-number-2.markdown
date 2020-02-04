---
layout: post
title: guess-the-number-2.py
---

# guess-the-number-2.py

```
# Conditionals: if/elif/else

# Task: Guess-the-number game

import random
answer = random.randint(1, 10)
print(answer)

guess = int(input("Guess: "))

if guess == answer:
    print("Correct!")
elif guess > answer:
    print("Too high")
else:
    print("Too low")
    
```

