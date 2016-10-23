# Section 3: The Node Core
## 1.10 Conceptual Aside: Servers and Clients
### 🚀 Servers and Clients
- a SERVER is a computer that is performing services
- it performs jobs that are requested of it


- a CLIENT is a computer that asks for those services
- the client can also do work, but the server does a heavier, deeper amount of work


- Client > makes a request for a service = "request"
- Server > responds to that request = "response"
- the Request and Response are both in some standard format, that both the client and server are programmed to understand
- (so, they are both computers, they can be the same computer in some circumstances)
- this is called "The Client-Server Model of Computing"
- one of the most popular means of using this model is The Internet


- the usual server is a Web Server, a computer connected to the internet, that accepts requests and provides responses
- the usual client is a Browser, like Chrome
- they communicate with Requests and Responses
- the standard format on the internet is called HTTP


- on the CLIENT, we use HTML and CSS for laying out our information on a webpage, and we use JS because browsers are standardized to use JS (they all implement a JS engine of some kind)
- Chrome is a C++ program
- Chrome embeds V8
- Chrome makes extra features available to JS (like the `XMLHttpRequest` object, which is outside the ECMAScript spec; similarly, if you look for "DOM manipulation", you won't find it in the ECMAScript spec)
- the work that we're doing here is CLIENT WORK – manipulating webpages, requesting data


- on the SERVER, there are many languages available that can handle server tasks
- PHP, C# (for ASP.NET), Ruby (for Ruby on Rails)
- the goal of NodeJS is to enable JS to be understood by SERVERS – to be understood by computers that perform server tasks
- now, we only need ONE programming language!
- NB. this (being able to write server-side code in JS) isn't the only reason that NodeJS exists


## 1.11 What does JS need to manage a server?
- what does JS need to be able to do the kinds of things that a web server needs to do?
- JS needs...
 - better ways of organizing our code into reusable pieces
  - previously, only available in other languages
  - now available in ES6
  - but provided by Node before that
 - ways to deal with files
  - web servers need to work with files, like zip files, or images
 - ways to deal with databases
  - almost always dealing with databases when building web software
 - the ability to communicate over the internet
 - the ability to accept requests and send responses (in the standard format)
 - a way to deal with work that takes a long time
  - we want people to be able to access the web server, even when it's doing things that haven't completed
- these things are provided by Node

## 1.12 The C++ Core
- this is the base of Node, that adds features to JS
- the NodeJS Foundation is at https://github.com/nodejs
- the repo for Node is at https://github.com/nodejs/node
- Node was written by Ryan Dahl in 2009 whilst working at Joyent
- `/deps` includes stuff that Node depends on
- we can see V8 there
- `/dep/zlib` is C++ code that enables JS to manage `.zip` files
- we can see that in `/src` there is a lot of C++ code; this is the source code for Node
- in `/src/node.h`, we see `#include "v8.h"` – we are using the V8 engine in Node to process and execute JS
- so, the Node C++ core is a core of features / utilities, written in C++, made available to JS, via the hooks in the V8 engine
- the mental note is that Node isn't JS; it extends the functionality of JS

# 1.13 The JS Core
- there is actually pure JS that has been written for us, to help making those C++ features easier
- `/lib/` is full of JS code!
- Node comes with a lot of JS written for us, to perform tasks
- like `/src/lib/zlib`
- most of these are actually WRAPPERS for the C++ features
- a lot of the files will have `process.binding`, like `process.binding('zlib')`
- this grabs the C++ feature, and makes it available inside the JS
- it goes and gets the C++ OBJECT, and makes it available
- but other files, like `/src/lib/util.js`, are not wrappers – they are regular JS functions that are just useful!
- so, Node is both a framework as well as a library of code

# 1.14 Downloading Lecture Source Code

# 1.15 Let's install and run some JS in Node
- install node
- let's see if Node is installed
```
node -v
```
- when we type
```
node
```
we start a Command Line Interface that comes for free with Node
- we can type JS into the command line (!!) and get the output back – AFTER it has been PROCESSED through the V8 engine and Node!!
- our JS > Node (its extensions to V8) (and V8) > response back to us
- let's write some code!
```
1+1;
// 2
const a = 'hello';
// undefined (the return)
a;
// hello
```
- Node gives us `console.log` (to work in a server; and not just the client (browser))
- let's get Node to process a file!
```
node <file-name>
```
- that file is our ENTRY POINT (and we can use multiple other JS files via that entry point)
- the argument is: the name of our file that we want Node to process (execute)

----
> ### 🚀 Node versions
- Node was invented within a company called Joyent
- Joyent were unhappy with how OFTEN V8 was being upgraded (by Google), and having to upgrade Node whenever V8 was upgraded
- those who wanted Node to be upgraded faster moved Node into another version called `io.JS`
- so, NodeJS was at `0.12.7` and io.JS moved from `1.0` > `2.0` > `3.0`
- then everyone came to an agreement about how Node should be structured and updated from a clerical standpoint
- Node `4.0` merged these 2 branches

----

- one of the reasons we're going to use VS Code is that we get Debug Mode
- so we can execute Node programs and insert breakpoints to help us debug and understand Node

----
> ### 🚀 Breakpoint
- A spot in our code where we tell a debugging tool to pause the execution of our code
- so we can figure out what's going on

----
