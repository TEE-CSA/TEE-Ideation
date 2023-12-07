---
title: DOM Manipulation and Event Handling
description: Advanced usage of jQuery.
type: plan
courses: {'csa': {'week': 15}}
---

# Introduction to DOM

One of the most useful abilities of JavaScript (and thus jQuery) is its ability to manipulate the DOM. But what is the DOM?

# Overview of DOM

The DOM, short for Document Object Model, is a standard that allows us to create, change, or remove elements from HTML or XML documents. 

Some operations that you can perform on DOM elements include...

- Extracting the content of an element
- Changing the content of an element
- Adding an element before or after an existing element
- Replacing an existing element with another element
- Deleting an element
- And many more!

## jQuery Get Methods

### text() method

The jQuery text method, as its name implies, simply returns the plain text value of the content.

Below is an example of an application of the text() method:


### html() method

The jQuery html method returns the plain text value of the content too, but it also returns it with HTML tags.

### Example 

```
<div id="info">
  <p class="name">John Doe</p>
  <p class="description">
    <span>Web Developer</span> at <a href="#">TechCorp</a>
  </p>
</div>
```

#### text() method use


```javascript
var descriptionText = $(".description").text();
console.log(descriptionText);

// with the text() method, this would output the plain text value of description 
// output: 'Developer at TechCorp'
```

- jQuery .text() method is used to retrieve the plain text content from the element with the class description ('Developer at TechCorp')
- The $(".description").text() part selects the element with class description and then gets its textual content without any HTML tags.

#### html() method use


```javascript
var descriptionHTML = $(".description").html();
console.log(descriptionHTML);

// with the html() method, this would output the HTML content of the element with all the HTML tags
// output:'<span>Web Developer</span> at <a href="#">TechCorp</a>'
```

- The .html() method is used to fetch the HTML content from the same description element
- $(".description").html() selects the description element and also its inner HTML content, including the HTML tags like <span> and <a> 

# Event Handling

## Events

Events refer to the various actions or occurrences that happen in the web browser, which can be detected and responded to with JavaScript

Some types of events include...
- keyboard events (keypress, keyup, etc.)
- form events (ex. submit)
- document/window events (resize, load, etc.)

### Examples

#### Event Handler for Clicking a Button

```
<button id="clickButton">Click Me!</button>

```



```javascript
$("#clickButton").click(function() {
    alert("Button was clicked!");
  });
```

Breakdown:

- In this first example, the jQuery code sets up an event handler for the click event on the button with the ID ```clickButton```
- When the button is clicked, an alert box displays the message, "Button was clicked!"

#### Event Handler for Form Submit

```
<form id="myForm">
  <input type="text" placeholder="Enter text">
  <input type="submit" value="Submit">
</form>
<div id="formOutput"></div>
```


```javascript
$("#myForm").submit(function(event) {
    event.preventDefault(); 
    var enteredText = $(this).find("input[type='text']").val();
    $("#formOutput").text("You entered: " + enteredText);
  });
  
```

Breakdown:

- In this code segment, the jQuery script handles the submit event of the form with the ID ```myForm```.
- The event.preventDefault() method stops the form from being submitted in the traditional way (clicking the submit button), which prevents the page from reloading.
- It gets the text entered in the text input field and displays it in a div with the ID ```formOutput```.

#### Event Handler for Mouse Enter/Leave

```<div id="hoverDiv">Hover over me!</div>```



```javascript
$("#hoverDiv").mouseenter(function() {
    $(this).css("background-color", "green");
  }).mouseleave(function() {
    $(this).css("background-color", "red");
  });
```

Breakdown:
- The code attaches two event handlers to the div with ID hoverDiv. (for when the mouse enters and leaves the div)
- When the mouse hovers over the div (mouseenter event), the background color changes to green.
- When the mouse leaves the div (mouseleave event), the background color changes to red.
