# CPSC-1520 - Lesson Plans

| Week | Monday | Tuesday | Thursday |
|:----:|--------|---------|----------|
|  1   | [W01-D1](#w01d1) | [W01-D2](#w01d2) | [W01-D3](#w01d3) |
|  2   | [W02-D1](#w02d1) | [W02-D2](#w02d2) | [W02-D3](#w02d3) |
|  3   | [W03-D1](#w03d1) | [W03-D2](#w03d2) | [W03-D3](#w03d3) |
|  4   | [W04-D1](#w04d1) | [W04-D2](#w04d2) | [W04-D3](#w04d3) |
|  5   | [W05-D1](#w05d1) | [W05-D2](#w05d2) | [W05-D3](#w05d3) |
|  6   | [W06-D1](#w06d1) | [W06-D2](#w06d2) | [W06-D3](#w06d3) |
|  7   | [W07-D1](#w07d1) | [W07-D2](#w07d2) | [W07-D3](#w07d3) |
|  8   | [W08-D1](#w08d1) | [W08-D2](#w08d2) | [W08-D3](#w08d3) |
|  9   | [W09-D1](#w09d1) | [W09-D2](#w09d2) | [W09-D3](#w09d3) |
|  10  | [W10-D1](#w10d1) | [W10-D2](#w10d2) | [W10-D3](#w10d3) |
|  11  | [W11-D1](#w12d1) | [W11-D2](#w11d2) | [W11-D3](#w11d3) |
|  12  | [W12-D1](#w12d1) | [W12-D2](#w12d2) | [W12-D3](#w12d3) |
|  13  | [W13-D1](#w13d1) | [W13-D2](#w13d2) | [W13-D3](#w13d3) |
|  14  | [W14-D1](#w14d1) | [W14-D2](#w14d2) | [W14-D3](#w14d3) |
|  15  | [W15-D1](#w15d1) | [W15-D2](#w15d2) | [W15-D3](#w15d3) |

---

## W01D1

> No Classes

---


## W01D2 

> Follow my [First Class](../Common/ReadMe.md) outline

- **Intro to the Course**
  - [ ] Introduce the course outline, syllabus, and planning calendar
  - [ ] Outline classroom etiquette and what is expected from students regarding attendance, homework, and effort
  - [ ] Briefly review the required text resource online at http://eloquentjavascript.net/index.html
  - [ ] Install [Required Software](../../ReadMe.md)
    - [git](https://git-scm.com/downloads)
    - [Visual Studio **Code**](https://code.visualstudio.com)
- **Introduction to git and GitHub**
  - [ ] Discuss git and version control
  - [ ] Setup student GitHub accounts
  - [ ] Setup student workbooks
  - [ ] Basics of MarkDown
    - Direct students' attention to the docs and [My Notes](../../docs/mynotes/ReadMe.md) portion of the workbook
    - Edit the [**ReadMe.md**](../../ReadMe.md) file at the root of your workbook

---

## W01D3

- **Handle Late Students**
  - [ ] Setup GitHub accounts & software installation & workbook assignment
- **Introduction to git and GitHub**
  - [ ] Basics of MarkDown
    - Create a [ReadMe.md](./demos/ReadMe.md) file and add an image (screenshot of [QR Code for their name](https://www.the-qrcode-generator.com/))
  - [ ] Committing Changes and Synchronizing (pull/push) with GitHub

---
---

## W02D1

> ***4* Marks** - There is an in-class assessment today

<!-- Demo the effect of a pull and the need for synchronizing by adding a commit to each student's repository  -->
<!-- JavaScript editing in the Browser + First assignment -->

- **Review/Questions**
  - [x] Answer student questions and review from previous class
- **Markdown Followup**
  - [x] Take a screen shot of something and put it in the `~\docs\images\` folder.
    - [Jing](https://www.techsmith.com/jing-tool.html)
  - [x] Add an image (screenshot of [QR Code for their name](https://www.the-qrcode-generator.com/)) to a ReadMe file. 

    ![Url](./images/me-on-github.png)

    - DON'T DEMO this => <small>And now for something completely different: <a href="https://ourcodeworld.com/articles/read/271/how-to-decode-a-qr-code-from-an-image-with-javascript">Decode QR Code in JavaScript</a></small>
- **Basics of JavaScript Execution**
  - [ ] [JavaScript Spec (ES5 vs ES6 vs ES7)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources) and [Implementations (Chakra for *Opera* vs Spider Monkey for *FireFox* vs V8 for *Chrome*)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources#Implementations)
    - JavaScript is
      - Case Sensitive
      - *not* a Type-Safe language (like C#)
  - [ ] Browsers and JavaScript Engines
    - How the browser parses pages and scripts
    - Interpreted vs compiled programming languages
      - Compiled programs tend to run faster, but are specific to the OS/hardware it is run on
      - Interpreted languages are a bit slower, but don't have to worry about the OS/hardware, because it runs in a "context" (the browser) that interprets the code
- **Basic Console Access**
  - [x] View the page with **Live-Server**
  - [x] How to open the developer tools console
  - [x] How to execute simple JS statements in the console
    - `5 + 7` &ndash; Adds two numbers
    - `'5' + 7` &ndash; Concatenates two strings
    - `'5' * 7` &ndash; Did you see that coming?
    - [The "Why" behind "WatMan"](https://medium.com/dailyjs/the-why-behind-the-wat-an-explanation-of-javascripts-weird-type-system-83b92879a8db) and [JavaScript WAT](https://blog.kevinchisholm.com/javascript/javascript-wat/)
- [**Basic DOM access**](#basic-dom-access)
  - [x] Demonstrate basic DOM selector methods
  - [x] Demonstrate how to use the innerHTML property of HTMLElement objects
- **Basic Variable Declaration and Assignment**
  - [x] Simple variable declarations
  - [ ] Simple types (strings and numbers)
    - [ ] **Data Types**: Number, String, Boolean, Object, Array
    - [x] The `typeof()` function
    - [ ] For an **element** that you query, you can check the `.tagName` or the `.nodeName`
- **In-Class Assessment**
  - [ ] Have students work through the 
    - [x] console exercise (not for marks) and 
    - [ ] in-class assessment (for marks), which **must be completed by the end of class** <!--(only release the in-class assessment in class on this day via GitHub Classroom Assignment; DO NOT release through Moodle).-->

#### **Basic DOM Access**

In the browser, the **document** object reference provides several methods for selecting elements in the
DOM:

- `document.getElementById(selector)` – returns a single matched element
- `document.getElementsByTagName(selector)` – returns a list of matched elements
- `document.getElementsByClassName(selector)` – returns a list of matched elements
- `document.querySelector(selector)` – returns the first matched element
- `document.querySelectorAll(selector)` – returns a list of matched elements

In this exercise we will only be looking at **getElementById** and **querySelector** (the other methods will be
explored later). Each of these functions returns the matched element (if any) from the DOM.

```javascript
document.getElementById('copyright-owner');
document.querySelector('h1');
document.querySelector('nav.top-nav');
```

Try it yourself by looking for the element with an ID of `'byline'`. *(**Hint:** `document.getElementById('byline')`)*

Notice that each of the searching functions used so far give us a single element. Here's one that gives us a whole bunch of elements! Compare that with what you get when just using `document.querySelector('p')`.

```javascript
document.querySelectorAll('p')
```

Of course, if you want to go ***wild***, you could try this:

```javascript
document.querySelectorAll('p').forEach(function (e) { console.log(e); })
```

---

## W02D2


- **Linking Scripts**
  - [ ] Introduce directory structure
  - [ ] Discuss `<script>` tag placement and concerns/issues that developers should be aware of that dictate when to place in the head vs body element.
        1. End of `<body>` for efficiency
        1. In the `<head>` if required
- **String Concatenation**
  - [ ] Practice with prompt() to get user input and concatenate with a message for output to the document
    - Go through greet_user example
- **Intro to Functions**
  - [ ] Discuss built-in functions (e.g. console.log) already used and how they work
  - [ ] Basics of function declaration (declared functions vs expressions)
    - Parameters
    - Return values
  - [ ] Basics of calling functions
    - Arguments
  - [ ] Scope
    - Variable access
  - [ ] Create a function to take care of the concatenation message display done in the previous example
    - Go through the "Intro to FUNctions" example (w02/d2)
  - [ ] Have students work through the posted functions exercise for homework

---

## W02D3

---
---

## W03D1

- Improve the use of our functions by using the **`const`** keyword
- In-Class Assessment [Functions]
  - Have students work through in-class assessment, which must be completed by the end of class (only release the in-class assessment in class on this day on the projector; DO NOT release through Moodle).
- Quiz
- **Introduce basics of event listening**
  - [ ] Event propagation
  - [ ] Event default behavior
  - [ ] Three steps for event listening
    1. Select the target element
    1. Create the function (event handler)
    1. Add the function as an event listener to the element
  - [ ] Go through events-intro example
    - E.g. clicking on links (`<a>`)
    - Go through events-default-behaviour example

---
## W03D2

- *Any remaining items from previous week*
- Clicking links (override default behavior) displays full-size image
  - [ ] Have students work through posted events exercise for homework

---
## W03D3

In-Class Assessment [Events]
Have students work through in-class assessment, which must be completed by the end of class (only release the in-class assessment in class on this day on the projector; DO NOT release through Moodle).

---
---

## W04D1

- **If-else statement**
  - [ ] Discuss the process of identifying conditions and then forming expressions that yield Boolean results
  - [ ] Review relational and equality operators
  - [ ] Go through decisions_intro example
    - Clicking the image toggles the description display

---

## W04D2

- **Operators**
  - [ ] Discuss the difference between equality and identity operators
  - [ ] == vs. === and != vs. !==
  - [ ] Revisit decisions_intro example
  - [ ] Have students work through posted decisions exercise for homework

---

## W04D3

Work through the resize_thumbnails examples, which cover the following:

1. One event handler for multiple elements
2. Reducing unnecessary variables and event propagation and reducing unnecessary adding of event listeners
3. Removing the decision making from the solution and using what is known in the HTML
4. Converting to an anonymous function (and the why and when to do so)
<!-- -->

---
---

## W05D1

- **Form Introduction**
  - Build a simple login form (text[name=username], password[name=password], input[type=submit]) to cover the basics of form submission (e.g. submit event listener, prevent default behaviour, etc) and how to access and work with form elements (i.e. event.target.elements)
    - Perform some basic form validation on the fields:
      - [ ] username must be contain at least one '@' symbol
      - [ ] password must be between 6 and 10 characters in length
    - And utilize a class for updating the form fields display when a field is invalid (e.g. add error class that makes the border red)

---

## W05D2

- Have students work through posted forms exercise, and complete as homework if necessary

---

## W05D3

In-Class Assessment [Decisions]
Have students work through in-class assessment, which must be completed by the end of class (only release the in-class assessment in class on this day on the projector; DO NOT release through Moodle).

---
---

## W06D1

> This week's work is to complete Assignment 1.

---

## W06D2

> This week's work is to complete Assignment 1.

---

## W06D3

> This week's work is to complete Assignment 1.

---
---
