---
layout: post
title: Introduction To JavaScript
subtitle: A Quick Look At What JavaScript Is And How It Works
tags: [basics, introduction]
readtime: true
gh-repo: enigma6174/javascript-blogs
gh-badge: star
---

JavaScript is a **dynamic, weakly typed** programming language which is compiled at runtime. It can be executed directly as a part of a webpage in a browser or on any other machine i.e. **host environment**.

JavaScript was originally created to **make webpages more dynamic** (e.g. change the content of the website directly from inside the browser). Originally, it was called **LiveScript** but due to the popularity of **Java** it was later renamed to **JavaScript**

{: .box-warning}
**Note:** JavaScript is totally independent from Java and has nothing in common!

### How Do Webpages Work?

When the user visits a webpage on their browser (for e.g. Google) what they are doing is connecting to the _Google servers_ and asking them for the Google homepage. This is called as making a request. The _Google server_ then validates this request and returns the requested file (the Google homepage in our case). This is called a response.

Now, let us consider that the user makes another request - maybe clicking on some search settings which displays a popup window with advanced options. The user can select or unselect checkboxes, radio buttons, select items from a list etc. Now, all these features are made possible by JavaScript.

![javascript-intro](/javascript-blogs/assets/img/js-intro.jpg)

### How JavaScript Gets Executed

When a JavaScript code is run (and let us assume, for simplicity that the effects will be seen on the website) then, before being executed the JavaScript code actually passes through something called as a **JavaScript Engine**. This is in built into the browser and each browser comes with it's own implementation of the JavaScript Engine. For example, the JS engine built into Chrome is called **V8** and the one inside Firefox is called **SpiderMonkey**.

The **JavaScript Engine** executes the JS code in 3 steps - **Parsing, Compiling, Execution**

##### Parse

In this phase the JS Engine reads the code, understands the code (i.e. what are the variables, what are the functions etc.) and performs some pre execution steps (like removing unwanted whitespaces, moving function defintions etc.)

##### Compile

In this phase, the parsed code is converted to machine code (i.e. a format understandable by the browser or the _host machine_). Conversion to machine code happens on-the-fly which means that the code conversion happens at source line by line.

##### Execute

In this phase, the machine code is then executed line by line and the results can be seen on the website or the host machine.

![javascript-execute](/javascript-blogs/assets/img/js-execute.png)

### JavaScript Is Dynamic And Weakly Typed

**Dynamic** means that JavaScript is not pre-compiled and instead parsed and compiled _on-the-fly_. In programming languages like Java, C++ etc. the entire code first needs to be compiled into an intermediate file and then, this intermediate file is converted into an executable file when required.

{: .box-note}
**Note:** In dynamic programming languages, the written code is directly converted to executable without going through the intermediate phase. Therefore, there is no need to compile the code first. The entire compilation and execution process happens together at runtime.

**Weakly Typed** means that the type of the data can change at runtime and datatypes are assumed automatically. This means that we do not have to specify the type of data a variable will hold. Whatever type of value is assigned to a variable, becomes the type. For e.g. a variable can hold numbers at one point _(Number type)_ and later on that variable may hold string _(String type)_

![javascript-dynamic-weak](/javascript-blogs/assets/img/js-dynamic-weak.png)

### JavaScript Runs On A Host Environment

_Host environment_ refers to the system or the machine that is executing the JavaScript code. JavaScript code cannot run standalone, it always needs an environment to run.

The most common envrionment to run JavaScript code is inside the browser. When running in a browser, JavaScript is used to make the websites more dynamic. It can manipulate HTML and CSS and also send and recieve HTTP requests among other things.

{: .box-note}
**Note:** Inside the browser JavaScript **cannot** access the local filesystem, interact with the host OS etc.

JavaScript can also run on the server side or a remote machine. This is basically the extracted JavaScript Engine running inside a C++ module. It can be executed on any machine and is therefore used extensively to design the backend web servers, API services etc.

{: .box-note}
**Note:** Server side JavaScript **can** access the local filesystem, interact with host OS etc. It however **cannot** manipulate HTML or CSS

![javascript-summary](/javascript-blogs/assets/img/js-summary.png)
