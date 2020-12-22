# Haskell Exercises

* Introduction
* Exercises 
* Answers
* Resources

## Introduction
In this blog I will be present helpful projects/exercises to practice writing in Haskell which I find to be the best handson learning tool. 

## Exercises

1. Write a program that reverses a list
2. Write a program that finds the greatest common divisor of two numbers using Euclids Algorithm
3. Determine whether two positive integer numbers are coprime. Two numbers are coprime if their greatest common divisor equals 1
4. Duplicate the elements of a list
5. Given a range of integers by its lower and upper limit, construct a list of all prime numbers in that range
6. Goldbach's conjecture says that every positive even number greater than 2 is the sum of two prime numbers. Example: 28 = 5 + 23. Write a predicate to find the two prime numbers that sum up to a given even integer.


## Answers

1. 
```Haskell
reverse :: [a] -> [a]
reverse [] = []
reverse (x:xs) = reverse xs ++ [x]
```
2. 
```Haskell
gcd' 0 y = y
gcd' x y = gcd' (y `mod` x) x
myGCD x y | x < 0     = myGCD (-x) y
          | y < 0     = myGCD x (-y)
          | y < x     = gcd' y x
          | otherwise = gcd' x y
```
3. 
```Haskell
coprime a b = gcd a b == 1
```
4. 
```Haskell
dupli [] = []
dupli (x:xs) = x:x:dupli xs
```
5. 
```Haskell
primesR :: Integral a => a -> a -> [a]
primesR a b = takeWhile (<= b) $ dropWhile (< a) $ sieve [2..]
  where sieve (n:ns) = n:sieve [ m | m <- ns, m `mod` n /= 0 ]
```
6. 
```Haskell
goldbach n = head [(x,y) | x <- pr, y <- pr, x+y==n]
    where pr = primesR 2 (n-2)
```

## Going Forward
In this blog various simple excercises were presented, go to the final blog to complete this overview of Haskell and functional programming [blog 10](Blog10.md) 

## Resources
* [Haskell Exercises](https://exercism.io/tracks/haskell)
* [Helpful Homework Assignment upenn](https://www.seas.upenn.edu/~cis194/spring13/lectures.html)
* [99 Questions](https://wiki.haskell.org/99_questions/31_to_40)
