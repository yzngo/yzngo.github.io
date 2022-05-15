---
title: Python - json
date: 2019-10-07 14:10:00 +0800
categories: [Language, Python]
tags: [python, json]
---



## json

```python
from json import dump
from json import load

file_path = r"Code\Python\numbers.json"
numbers = [2, 3, 5, 7, 11, 13]

def dump_numbers():
    with open(file_path, 'w') as file_object:
        dump(numbers, file_object)

    
def load_numbers():
    with open(file_path ) as file_object:
        numbers = load(file_object)
        print(numbers)

dump_numbers()
load_numbers()

```



