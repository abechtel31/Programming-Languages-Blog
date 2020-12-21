# Input Output in Haskell  

* Introduction
* Haskell I/O
* Hello World
* Going forward
* Resources

## Introduction
In this blog I will touch on I/O methods in Haskell but will not dive deeply as I myself am not well versed on the subject.

## Haskell I/O
Haskell has two basic categories, pure functions from computations that have encoded side effects of a particular type. Some examples of these types of IO operations or these coputations with side effects are:

    getLine :: IO String
    putStrLn :: String -> IO ()
    randomRIO :: (Random a) => (a,a) -> IO a
    
Normal Haskell will not excecute this code, the only IO action which can run in a compiled Haskell program is main.

## Hello World
To write our favorite hellp world program we could do something as follows:

    main :: IO ()
    main = putStrLn "Hello, World!"
  
There are also ways to connect IO operations to make a put together chunk of code as opposed to simply a print statement. A very basic way to do this could be:

    main = putStrLn "Hello" >> putStrLn "World"
    
which will print "Hello" and "World" on separate lines by using the >> operator.

To print things in a specified order we can "bind", >>=. So that if there is an action that performs first, we can take it's result and pass it to the next operation which computes a result which is the final computation or result of the overall computation.

    main = putStrLn "Hello, what is your name?"
          >> getLine
          >>= \name -> putStrLn ("Hello, " ++ name ++ "!")

We will also need an IO action that does nothing and simply returns a value, the return operation does just that. 

## Going Forward
In this blog we learned about very simple input and output without talking about the elephant in the room, monads. Monads share similar concepts for binding and returning but are not the same as the simple I/O we discussed in this blog. To continue learning go to [blog 9](Blog9.md).

## Resources
* http://learnyouahaskell.com/input-and-output
* https://www.seas.upenn.edu/~cis194/fall16/lectures/06-io-and-monads.html
* http://book.realworldhaskell.org/read/io.html
