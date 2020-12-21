# Benchmarking Haskell

* Introduction
* Benchmarking
* Going forward 
* Resources

## Introduction
Being a computer scientist and writing code is not simply about creating code that does what you want but also in a way that is efficient in regards to both memory and time consumption. In programming langauges that you may be more familiar with, benchmarking code and predicting how efficiently it will run is quite straightforward however with functional programming things can be more challenging. This is because in Haskell expressions are evaluated on command, it will only preform as much evaluation as is necessary, which brings us back to the lazy nature of Haskell's evaluation.

## Benchmarking  
I will be using a Haskell package called [Criterion](http://hackage.haskell.org/package/criterion) for the benchmarking of code in this blog. Criterion is very easy to install, simply type cabal install criterion in your terminal. 
To test code please create a file called fib.hs with the following code:

```haskell
    import Criterion.Main (defaultMain)
    fib :: Int -> Int
    fib 0 = 0
    fib 1 = 1
    fib n = fib (n-1) + fib (n-2)
```
Additionally in that file to get various benchmarking statistics, please add this section of code to the end of the file:

```haskell
    main = defaultMain [
        bench "fib 10" $ \n -> fib (10+n-n),
        bench "fib 30" $ \n -> fib (30+n-n),
        bench "fib 35" $ \n -> fib (35+n-n)
       ]
```  

We then build:
    
    ghc -O --make fib

To run the program we use (the win extension displays in a window but you could also display as a png with something like -t png:450x175 -k png:450x175):

    ./fib -t win -k win

Try this and see what images you recieve and see if you can interpret the results.  

In the console information will also be printed out, yours may look slightly different but here is a sample of what it may be.

```
    estimating clock resolution...
    mean is 9.956511 us (80001 iterations)
    found 3711 outliers among 79999 samples (4.6%)
     3505 (4.4%) high severe
```

The first thing that fib does is measure how long it takes for the system clock to tick. It will then run our benchmarked code enough times that the resolution of the clock will not introduce a significant error. This is very important because if fib 10 takes 4.23µs to evaluate, but the clock ticks once every 12.19µs we can't determine how long the code takes. To fix this we should evaluate fib 10 thousands of times to get the measurement error introduced by the resolution of the clock down to a few parts in ten thousand.

Once we've characterised the system clock's period, we figure out how expensive it is to actually use the clock.
```
    estimating cost of a clock call...
    mean is 923.3224 ns (58 iterations)
    found 4 outliers among 58 samples (6.9%)
      1 (1.7%) high mild
      3 (5.2%) high severe
```

The last part is the most interesting. We automatically figure out how many times we need to evaluate fib 10:
```
    benchmarking fib 10
    collecting 100 samples, 1911 iterations each, in estimated 995.8188 ms
```

This is essentally a way to learn how expensive it will be to benchmark. It is only an estimate but it is quite accurate, this can be very useful in learning how much time you need to allocate to benchmarking a program. To get data of any significant significance we want to bootstrap and take many samples.
```
    bootstrapping with 100000 resamples
```    
We do this because in the real world applications do not always follow a neat pattern especially if you are working on a machine where many other things are happening. The results of the bootstrap will tell you the mean and standard deviation from the runs along with the confidence in those values. Here is an example:
```
    mean: 5.232800 us, lb 5.222862 us, ub 5.262482 us, ci 0.950
    std dev: 79.86726 ns, lb 31.06332 ns, ub 173.0716 ns, ci 0.950
```    
It then reports on the outliers in the measurements, and most importantly, tells us whether they are important.
```
    found 7 outliers among 100 samples (7.0%)
      3 (3.0%) high mild
      4 (4.0%) high severe
    variance introduced by outliers: 0.993%
    variance is unaffected by outliers
```

This is great news that the variance is uneffected by outliers, if yours says something different than you may want to take a closer look, this means your performance measurements are innacurate. You can see this quite clearly because the standard deviation and mean will be close to the same value which indicates this inaccurate measurement. 

There are many other ways to test and benchmark Haskell programs but in particular I found Criterion very easy to use and I appreciated the generated graphs.

## Going Forward
So you've made it through week 4, by now you should be capable in Haskell and have an understanding of the benefits of using Haskell as a purely functional programming language. This week we explored benchmarking Haskell using the criterion extension, now you can easily measure the performance of your Haskell code and produce easy to read charts in PDF, SVG, and CVS. Now go to [blog 6](Blog6.md) to learn about debugging.

## Resources
* http://book.realworldhaskell.org/read/profiling-and-optimization.html
* https://downloads.haskell.org/~ghc/latest/docs/html/users_guide/profiling.html
* http://www.fatvat.co.uk/2010/08/ants-and-haskell.html
* [gnomon](https://github.com/paypal/gnomon)
* http://www.serpentine.com/blog/2009/09/29/criterion-a-new-benchmarking-library-for-haskell/ 
* http://hackage.haskell.org/package/criterion
* https://hackage.haskell.org/package/criterion-1.5.9.0/docs/Criterion-Main.html
* http://www.serpentine.com/criterion/tutorial.html