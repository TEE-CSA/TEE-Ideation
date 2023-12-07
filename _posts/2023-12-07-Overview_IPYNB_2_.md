---
title: jQuery and CRUD Principles Lesson Overview
description: Our lesson on jQuery and CRUD!
type: plan
courses: {'csa': {'week': 15}}
---

# Overview of Today's Lesson

- jQuery
    - What is jQuery?
    - What is jQuery used for?
    - Demonstration of application in markdown and HTML tables
        - Be able to explain similarities and/or differences between markdown and HTML tables
- CRUD principles
    - What does CRUD stand for?
    - How can CRUD be applied to jQuery and beyond?
    - Show demonstration of applying CRUD to tables created
- Hacks (tentative)
    - A quiz that covers the concepts taught 
    - Creating their own table with jQuery and explaining how it works
    - Extra: create something completely unique using jQuery and CRUD, explaining how the project applies the two

# What is jQuery?

Any volunteers?

Essentially, jQuery is a library that allows us to use some of JavaScript's built in functions. Think of it as one of the lines you could see at the very top of a code file along with many other import statements. 

## Benefits of jQuery

Some benefits of jQuery include but are not limited to:

- Makes it easier for us to write JavaScript and HTML code
- Very flexible in terms of which browsers it can work on
- Simplifies some of the most common JavaScript functions into fewer lines of code

**Question:** What are some real life applications of jQuery? Name at least two you can think of. 

## Basic Syntax

Whenever you are working with jQuery, the most basic format you will you use is the following:

```$(selector).action()```

Some examples of these include:

```$(this).hide()``` - hides the current element.


```$("p").hide()``` - hides all <p> elements.


```$(".test").hide()``` - hides all elements with class="test".


```$("#test").hide()``` - hides the element with id="test".
