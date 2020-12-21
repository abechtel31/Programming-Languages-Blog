# Lamda Calculus

* Introduction
* What is Lamda Calculus?
    * Syntax
    * Evaluation
    * Alpha reduction
    * Beta reduction
    * Church-Rosser Theorem
* Going forward
* Resources

## Introduction
Lambda calculus was developed in the 30's by mathemetician Alonzo Church who also wrote a lot of work regarding Turing machines. Lambda calculus was desiged as a way to study computations with functions. 

## What is Lamda Calculus?

A function is created with the notation λx.E. This signifies a function where x is an argument and E is the body of the function.

A function is applied by using the . character. A1.B1 means the function A1 applied to the argument B1.

### Syntax

There are three types of expressions in Lambda calculus: 
    
* E :: = x(variables)
* E1 E2(function application)
* λx.E(function creation)

Where λx.E is called Lambda abstraction and E is known as λ-expressions.

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
Alpha reduction is the simple form of reducing an expresion. For example if you are have two lambda expressions with the same variable name inside, you change one of them to a new variable name. (λx.xx)(λx.x) can be rewritten as (λx.xx)(λy.y) after reduction. The result is equivalent to what you start out with, just with different variable names. ##

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
    

### Church-Rosser Theorem
The theorem is this:
    If E1 ↔ E2, then there exists an E such that E1 → E and E2 → E. “Reduction in any way can eventually produce the same result.”
    If E1 → E2, and E2 is normal form, then there is a normal-order reduction of E1 to E2. “Normal-order reduction will always produce a normal form, if one exists.”

## Going Forward
In this blog we learned about Lamda Calculus and will continue in the following blog [blog 8](Blog8.md) .

## Resources
* https://personal.utdallas.edu/~gupta/courses/apl/lambda.pdf
* https://en.wikipedia.org/wiki/Lambda_calculus
* https://plato.stanford.edu/entries/lambda-calculus/
* https://opendsa.cs.vt.edu/ODSA/Books/PL/html/Syntax.html (very helpful online supplemental resource) 