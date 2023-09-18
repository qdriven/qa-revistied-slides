---
title:  Python Module 使用
summary: Python Module Loader
authors: [FluentQA]
tags: ['QAPython-Revisited']
categories: ['QAPython-Revisited']
date: '2022-12-10'
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: white
  # Choose a code highlighting style (see Hugo docs on Chroma)
  #   Light style: github-light. Dark style: dracula (default).
  highlight_style: dracula
---

# Python Module

- What's module
- How to Import Module?
- How to manipulate Module?
- How to import module programatically?

---

## Python inspect Module

```python
import inspect

inspect.ismodule(module_name)
```

---

## Python Import Module

```sh
python
     |--main.py
     |articles
        |--gfg.py 
```

```python
# class
class GFG:
   
  # method
  def method_in():
    print("Inside Class method")
     
# explicit function   
def method_out():
  print("Inside explicit method")
```

---

## Python Load Module: sys

```python
# importing module
import sys
 
# appending a path
sys.path.append('articles')
 
# importing required module
import gfg
from gfg import GFG
 
# accessing its content
GFG.method_in()
gfg.method_out()
```

---

## Python Load Module: importlib

```sh
import importlib.util
 
# specify the module that needs to be
# imported relative to the path of the
# module
spec=importlib.util.spec_from_file_location("gfg","articles/gfg.py")
 
# creates a new module based on spec
foo = importlib.util.module_from_spec(spec)
 
# executes the module in its own namespace
# when a module is imported or reloaded.
spec.loader.exec_module(foo)
 
foo.GFG.method_in()
```

---

## Python Load Module: SourceFileLoader

```python
from importlib.machinery import SourceFileLoader
 
# imports the module from the given path
foo = SourceFileLoader("gfg","articles/gfg.py").load_module()
 
foo.GFG.method_in()
foo.method_out()
```
