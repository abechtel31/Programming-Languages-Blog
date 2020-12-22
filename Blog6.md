# Debugging 101

* Introduction
* Debug with Debug.Trace
* Going forward
* Resources

## Introduction

As a break from the more difficult topics I wanted to prepare you this week with the ability to debug your Haskell code. I have found myself in many situations wondering what I did wrong and wishing I knew how, because I most often write incorrect code the first time and write and rewrite until it's right.

## Debug with Debug.Trace
If you have any coding experience, debug statements can be your best friend. In imperative languages, we can simply add print statements. In Haskell, however, we cannot output any information other than through the IO monad which is far too much work for simple debugging.

The solution is Debug.Trace, this module exports a function called trace which provides a convenient way to attach debug print statements anywhere in a program. Using the classic example of fiboncci again, we could write code in this manner.

```haskell
    module Main where
    import Debug.Trace

    fib :: Int -> Int
    fib 0 = 0
    fib 1 = 1
    fib n = trace ("n: " ++ show n) $ fib (n - 1) + fib (n - 2)
    
    main = putStrLn $ "fib 4: " ++ show (fib 4)
```

Below is the output:
```
    n: 4
    n: 3
    n: 2
    n: 2
    fib 4: 3
```   
Trace makes it possible to trace execution steps of program; that is, which function is called first, second, etc. To do so, we annotate parts of functions we are interested in, like this:

```haskell
    module Main where
    import Debug.Trace

    factorial :: Int -> Int
    factorial n | n == 0    = trace ("branch 1") 1
                | otherwise = trace ("branch 2") $ n * (factorial $ n - 1)
    
    main = do
        putStrLn $ "factorial 6: " ++ show (factorial 6)
```

This kind of debugging can help us find missing statements or errors much more quickly in our code. One quick thing to note before you go on your way is that trace is a pure function itself. You may not need to know this all but trace bridges between IO and pure Haskell: 

"The trace function should only be used for debugging, or for monitoring execution. The function is not referentially transparent: its type indicates that it is a pure function but it has the side effect of outputting the trace message.""

## Going Forward
In this blog we discussed debugging in Haskell, the next step is to go to [blog 7](Blog7.md) and learn about Lambda calculus.

## Sources
* https://en.wikibooks.org/wiki/Haskell/Debugging 
* https://wiki.haskell.org/Debugging
* https://hackage.haskell.org/package/base-4.14.1.0/docs/Debug-Trace.html
