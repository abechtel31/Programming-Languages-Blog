# GCHi 

* Introduction 
* Helpful tips
* Going forward
* Resources

## Introduction
In this blog I will be giving some hints and best practices to using the [Haskell interactive enviornment](https://downloads.haskell.org/~ghc/latest/docs/html/users_guide/ghci.htm)

## Helpful tips

* Tab completion
    As in other terminal programs you can start typing text in GCHi and hit the tab key to "autocomplete" whatever it was that you were typing. If there are multiple options you can press tab to see a list of all possible endings. Tab completion works also when you are loading a file with your program into GHCi. For example, after typing :l f\<Tab>, you will be presented with all files that start with "f" that are present in the current directory, fibonacci, fastforward, fault, file, etc.. We can do the same with importing modules with the :m +C\<Tab> or import C\<Tab>, you will be presented with all modules that start with "C".

* ": commands"
    On GHCi command line, commands for the interpreter start with the character ":" (colon).

    * :help or :h -- all available command.
    * :load or :l -- loads file into GHCi (you must include the filename with the command)
    * :reload or :r -- reloads whatever file had been loaded most recently
    * :type or :t -- prints the type of a given expression included with the command
    * :module or :m -- loads a given module
    * :browse -- gives the type signatures for all functions available from a given module.
    * :Tab -- to see all possible commands

* Timing Functions in GHCi
   There is also a build in method to GHCi to time how long a function takes to run. Type :set +s into the ghci command line and run the function you are testing. After the function runs GHCi will display the time it took to run.

* Multi-line Input
    This is a common need to make code more easily readable. One way is to begin a new line with :{ Type in your code. Press enter when you need a new line. Type :} to end the multi-line input. For example:
```
   *Main> :{
   *Main| let askname = do
   *Main|               putStrLn "What is your name?"
   *Main|               name <- getLine
   *Main|               putStrLn $ "Hello " ++ name
   *Main| :}
   *Main>
```
In addition, line breaks in ghci commands can be separated by ;, like this:

```
*Main> let askname1 = do ; putStrLn "what is your name?" ; name <- getLine ; putStrLn $ "Hello " ++ name
```

## Going Forward
Today we learned about simple navigation techniques of GHCi. Now it's time to go to [blog 4](Blog4.md) to have a deep dive all into recursion.

## Resources
* [Using GHCi effectively](https://en.wikibooks.org/wiki/Haskell/Using_GHCi_effectively)
* [Haskell interactive enviornment](https://downloads.haskell.org/~ghc/latest/docs/html/users_guide/ghci.htm)
