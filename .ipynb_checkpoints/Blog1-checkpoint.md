# Week 1 - The Basics
###  Introduction to functional programming with Haskell

* Introduction
* Helpful links for learning 
* What is Haskell?
* Getting started guide
* Examples

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

Let's talk about data, consider writing the program x=1 and then later changing your mind, in Haskell you can't set it to a new number later. Data in Haskell is immutable!

Haskell is a functional programming language, so how do functions work in Haskel? In Haskell functions only take an input and return a result, This is often summed up by saying that functions in Haskell no side-effects. Haskell is also said to have referential transparency because an expression can be replace it's value without changing the result. Simply put this means that if you call a function with the same parameter, x, it will always return the same result.

## Getting Started Guide

To test the examples in this blog and to examples and to become more comfortable in Haskell you can use this online [compiler](https://repl.it/languages/haskell) otherwise follow the instructions to download [Haskell](https://www.haskell.org/platform/). *

*A helpful note for running haskell locally. To enter the Prelude session and run Haskell commands enter `ghci` in your terminal. To run a saved Haskell program use the `:load filename.hs` command in the ghci session. To run functions contained in the file simply type the function name with the appropriate arguments `plus 2 3`. To exit the ghci session use `control-d`.

Before writing any code take some time exploring the interactive Haskell shell by typing ghci. Then, enter various commands as you would in a python shell. Ex: 2+2, n=1, n+2.

Just like in any other language Haskell has types, lists, strings, booleans, chars, floats, etc., and it's important to know what type of data you are going to be working with before you jump into writing a program to plan accordingly. 

## Examples

To make things easier in learning the syntax and functionality of this new language, here are a few example programs and functions in Haskell. 


**Addition:**

	add :: Integer -> Integer -> Integer  
	add x y = x + y
**Head:**

    head :: [a] -> a
    head [] = error "Empty List"
    head (x:xs) = x
**Length**

    length :: (Num b) => [a] -> b
    length [] = 0
    length (x:xs) = 1 + length xs
**Area Of Circle given Radius**

    area :: (Show a, Floating a) => a -> String
    area x = "The area of the circle is" ++ show(pi * x * x)
    
**How's the weather**

    weather :: (Num a) => a -> String
    weather x
	    | x <= 65 = "It's cold"
	    | x <= 75 = "It's the perfect day"
	    | otherwise = "You better take that jacket off"
	    

## Going Forward
If you have more questions than answers right now, it's okay! Don't get discouraged, there is still much more too learn and can be a big learning curve transitioning from learning imperative programming to functional programming. Great job on making it through blog 1. Now that you're familiar with Haskell go to the next [lab 2](Blog2.md) to compare and contrast some Haskell and Python code!