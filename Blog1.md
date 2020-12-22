# Introduction to functional programming with Haskell

* Introduction
* Helpful links for learning
* What is Haskell?
* Getting started guide
* Examples
* Going forward
* Resources

## Introduction

[Haskell](https://www.haskell.org/) is a purely functional programming language. If you're not sure what that means it's okay, that is what this week's blog is all about! Before we dive deeper into the syntax of the language there are two important differences between functional and imperative programming languages:
1. Functions in functional programming languages are pure functions, meaning that they are strictly mathematical - they have an input and return a result but nothing else.
2. All data in Haskell is immutable, once data is assigned to a name it cannot change value.

## Helpful Links
* [Haskell Platform](https://www.haskell.org/platform/) - for installation
* [Learning Haskell Tutorial](http://learnyouahaskell.com/) - Less traditional but very helpful
* [Haskell Cheat Sheet](http://cheatsheet.codeslower.com/CheatSheet.pdf)
* [Haskell Excercises](https://wiki.haskell.org/H-99:_Ninety-Nine_Haskell_Problems)
* [More Learning Haskell Resources](https://wiki.haskell.org/Learning_Haskell)

## What is Haskell?

As I said above, Haskell is a purely functional programming language (a lazy language) which I will elaborate on now.

Let's talk about data, consider writing the program x=1 and then later changing your mind, in Haskell you can't set it to a new number later. Data in Haskell is immutable! For example, this piece of code would not run in Haskell.  

    x=2
    x=10

Even though you may want to change the value of x, the compiler will respond with an error: "multiple declarations of x".  

Haskell is a functional programming language meaning that in Haskell functions only take an input and return a result. This is often summed up by saying that functions in Haskell have no side-effects. Haskell is also said to have referential transparency because an expression can be replace it's value without changing the result. Simply put this means that if you call a function with the same parameter, x, it will always return the same result. With this basic understanding of important aspects of Haskell the best way to understand a language is to start working in it.

## Getting Started Guide

To test the examples in this blog and to examples and to become more comfortable in Haskell you can use an online compiler links in the resources. Otherwise follow the instructions to download [Haskell](https://www.haskell.org/platform/).

*A helpful note for running haskell locally. To enter the Prelude session and run Haskell commands enter `ghci` in your terminal. To run a saved Haskell program use the `:load filename.hs` command in the ghci session. To run functions contained in the file simply type the function name with the appropriate arguments `plus 2 3`. To exit the ghci session use `control-d`.

Before writing any code take some time exploring the interactive Haskell shell by typing ghci. Then, enter various commands as you would in a python shell.   

In this way we could practice using Haskell as a basic calculator, entering 1+2 or 2x3 gives us the result we expect etc. Why don't you give it a try and become comfortable working in GHCi. This is not a long term solution though, because there are often times that we need values stored to use multiple places in code, to do that we use variables. Instead of having uncessary repetition in your code, we could set a variable say n=2 and use it many different places.

To save Haskell code in source files, we save files using the extension .hs. I suggest writing your longer code in a text editor for syntax highlighting to make reading and writing code easier (many people enjoy [visual studio](https://code.visualstudio.com/) or [atom](https://atom.io/)).

Just like in any other language Haskell has types, lists, strings, booleans, chars, floats, etc., and it's important to know what type of data you are going to be working with before you jump into writing a program to plan accordingly. In getting started try creating a file called haskell101.hs with the code:

    a =2.0 --this is how to comment in Haskell
    
In your terminal, start GHCi and load the file that you just created with :load haskell101.hs. When the file is loaded, you are now able to use the variable that you defined in the file in any calculation you make in the session. Try entering a and see what happens - it should print 2.0 (the value you set a to in the file). Now type a\*2, does it display 4.0? 

The last important this to discuss in this first blog is functions. As in most every programming language we are able to define functions to save time and repetition. A function is simply something that takes a value and gives a result, in the examples section below are a few functions. Try saving these functions in your haskell101.hs file, loading the file, and testing the functions. To run a function once the file is loaded simply type the function name and it's arguments. For example to add to numbers simply type add 1 2. 

## Examples

To make things easier in learning the syntax and functionality of this new language, here are a few example functions in Haskell.


**Addition:**
```haskell
    add :: Integer -> Integer -> Integer  
    add x y = x + y
```
**Head:**
```haskell
    head :: [a] -> a
    head [] = error "Empty List"
    head (x:xs) = x
```
**Length**
```haskell
    length :: (Num b) => [a] -> b
    length [] = 0
    length (x:xs) = 1 + length xs
```
**Area Of Circle given Radius**
```haskell
    area :: (Show a, Floating a) => a -> String
    area x = "The area of the circle is" ++ show(pi * x * x)
```
**How's the weather**
```haskell
    weather :: (Num a) => a -> String
    weather x
	    | x <= 65 = "It's cold"
	    | x <= 75 = "It's the perfect day"
	    | otherwise = "You better take that jacket off"
```

## Going Forward
If you have more questions than answers right now, it's okay! Don't get discouraged, there is still much more too learn and can be a big learning curve transitioning from learning imperative programming to functional programming. Great job on making it through blog 1. Now that you're familiar with Haskell go to the next [blog 2](Blog2.md) to compare and contrast some Haskell and Python code!

## Resources    
### Beginning Haskell Tutorials  
* [Meta Tutorial](https://wiki.haskell.org/Meta-tutorial)
* [Learning Haskell](http://learn.hfm.io/)  
* [Haskell](https://en.wikibooks.org/wiki/Haskell)
* [School of Haskell](https://www.schoolofhaskell.com/)

### Online Compilers  
* [Co calc](https://cocalc.com/app)
* [Try Haskell](http://tryhaskell.org/)
* [Haskell Online Compiler](https://repl.it/languages/haskell)  
* [Code World](https://www.code.world/haskell) 
