# Section 2: V8: The JavaScript Engine
## 1.6 Processors, Machine Code, and C++
### 🚀 Microprocessors
- A tiny machine  
- We give the microprocessor instructions  
- They speak a language  
- Not all microprocessors are the same  
- we have to give the instructions (code) in a language that it understands
- some of these languages:
 - IA-32
 - x86-64 (64 refers to 64-bit)
 - ARM
 - MIPS
- the code that we give to the microprocessor is called *machine code*


### 🚀 Machine Code (language)
- Programming languages spoken by computer processors
- **Every** program you run on your computer has been converted (compiled) into machine code!
- specifically, the language that my computer's processor speaks
- level of abstraction
 - Machine Language - very low level, what's happening is not abstracted away at all
 - Assembly language - a bit easier to understand and read
 - C / C++ - still used heavily today, its syntax looks similar to Java and JS (both these languages were inspired by C-syntax), still some level of control
 - JavaScript - very far removed, we don't deal with memory at all, we have an engine between you and the microprocessor
- because of this, we can have an improper mental model of how NodeJS is working

## 🚀 C++
- Node is written in C++
- we write in JS when we write Node programs
- the reason why Node is written in C++ is because V8 is written in C++ (the JS engine)
- V8 is the thing that converts JS to machine code!

## 1.7 JS Aside: JS Engines and the ECMAScript Specification
### 🚀 ECMAScript
- the standard JS is based on
- needed a standard since there are many engines
- JS came first, but then many browser vendors started making their own JS engines
- V8 is just one of those JS engines
- so, JS is the language, ECMAScript is the standard

### 🚀 JS Engine
- a program that converts JS code into something the computer processor can understand
- and it should follow the ECMAScript standard on how the language should work, and what features it should have

## 1.8 V8 Under the hood
- https://github.com/v8/v8
- V8 is Google's open source JS engine
- it was primarily written to be used inside Google's Chrome browser
- V8 implements ECMAScript as specified in ECMA-262.
- V8 is written in C++ and is used in Google Chrome, the open source browser from Google.
- V8 can run standalone, or can be embedded into any C++ application.

- in `v8/src` we can see `/x64`
- this is the code for the x64 machine language
- this means that there are entire sets of code FOR EACH machine language!
- this means that V8 can convert JS into any one of these machine languages
- there is a huge number of `.cc` and `.h` files - C++ files

## 1.9 Adding features to JS
- V8 can run standalone or it can be embedded into any C++ application
- JS > V8 (C++) > Machine Code
- JS > Another program with V8 embedded > Machine code
- when some JS is written in a particular way, we can cause V8 to write some extra Machine Code (more than what ECMAScript says JS can do)
- JS was designed to be in the browser
- JS wasn't designed to handle lower-level operations, like dealing with files, or connecting to a database
- C++ was designed to do those things
- we can create a C++ program that gives JS the `magic` keyword, to do what `Print` does in C++
- we embed V8 in our new C++ program
- `magic` is NOT in ECMAScript
- but, using V8, we have enabled JS to understand the keyword `magic`
- NodeJS is a C++ program that has V8 embedded inside of it, that adds a wealth of features to JS
- specifically, it enables JS to be a SERVER TECHNOLOGY; we can now use JS to write server-side code
