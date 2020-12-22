# Lambda Calculus

* Introduction
* What is Lambda Calculus?
    * Syntax
    * Evaluation
    * Alpha reduction
    * Beta reduction
* Going forward
* Resources

## Introduction
Lambda calculus was developed in the 30's by mathemetician Alonzo Church who also wrote a lot of work regarding Turing machines. Lambda calculus was designed as a way to study computations with functions. 

## What is Lambda Calculus?
  
### Syntax
   * Lambda term - a valid lambda calculus expression
   * Variable - consider a variable x, which is itself a lambda term
   * Abstraction - consider a lambda term e and variable x, we then say that λx.e is a lambda term called an abstraction. Abstraction is a definition of an anonymous function that takes x and returns e. \lambda x.x^{2}+2 is an abstraction for the function f(x)=x^{2}+2. 
   * Application - consider a lambda term e and lambda term f, we then say (ef) is a lambda term called an application. ef represents the application of a function e to an input f, that is, it represents the act of calling function e on input f to produce e(f).

### Evaluation
Pure lambda calculus has no built-in functions. We can start by looking at the two equivalent statements written below.

    ((1 * 5) + (9 * 2)) 
    (+ (* 1 5) (* 9 2)) 
    
We start by reducing (* 1 5) (* 9 2), the order of which reduce these two terms does not matter.

    (+ (* 1 5) (* 9 2)) 
    (+ 5 (* 9 2)) 
    (+ 5 18) 
    = 23
    
### Alpha Reduction
Alpha reduction is the simple form of reducing an expresion. For example if you are have two lambda expressions with the same variable name inside, you change one of them to a new variable name. (λx.xx)(λx.x) can be rewritten as (λx.xx)(λy.y) after reduction. The result is equivalent to what you start out with, although rewritten with different variable names.

### β-reduction Rule
To handle simplifications of lambda's we introduce the β-reduction.

    (λx . * 3 x) 4 
    (* 3 4) 
    = 12

The parameter may be used several times:

    (λx . + x x) 2
    (+ 2 2) 
    = 2
    
When we encounter multiple lambda's and terms, the inner x belongs to the inner λ and the outer x belongs to the outer one

    (λx . (λx . + (− x 1)) x 2) 9 
    (λx . + (− x 1)) 9 2 
    + (− 9 1) 2
    + 8 2 
    = 10

## Going Forward
In this blog we learned about Lambda Calculus and will continue in the following [blog 8](Blog8.md) .

## Resources
* [A Tutorial Introduction to the Lambda Calculus](https://personal.utdallas.edu/~gupta/courses/apl/lambda.pdf)
* [Lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus)
* [The Lambda Calculus](https://plato.stanford.edu/entries/lambda-calculus/)
* [Syntax of the Lambda Calculus](https://opendsa.cs.vt.edu/ODSA/Books/PL/html/Syntax.html) (very helpful online supplemental resource) 
