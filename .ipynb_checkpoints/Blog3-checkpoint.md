# Recursion Deep dive and Quick Sort

* Introduction - What is Recursion
* An example
* Quick Sort
* Going forward
* Resources

## Introduction - What is Recursion

This week we will be learning all about recursion! Recursion is a way of defining functions that call themselves or the function applied inside it's own definition. This process is often done quite requently in mathematics and is at the core of the Haskell language. One of the most frequently used examples of this is the fibonacci sequence. To start the sequence we define the first two fibonacci numbers, f_0 = 0, f_1 =bon 1. Then for every other natural number after zero and one, we say that the nth fibonacci number (f_n) = f_n-1 + f_n-2. Essentially, each fibonacci number is the sum of the two previous fibonacci numbers. The edge conditions of f_0 and f_1 are the foundation for the program though, we need these numbers to be set because without them our function would never end.

You may be asking, why is this important? Recursion is the basis of Haskell as a functional programming language. Intead of using traditional while or for loops like you may be accustomed to seeing, Haskell uses recursion to declare what something is.

## An Example
Since we've already discussed how fibonacci works on a high level I'd like to work though another example of a recursive program, finding the maximum value in a list. This function takes a list and returns the biggest value. Let's start by thinking how we would do this recursively, you may set up a variable to set the maximum value and loop through the list comparing the elements to that max value and setting that max value to the current value if the current value were bigger. 

How could we do this recursively? To start we would want to set up an edge condition that says that the maximum of a list with only one element is that element, pretty simple right! Then we would say that the maximum of any list longer than one element is the head of the list, if the head is bigger than the maximum of the tail. That is all there is to it and this is how it might look:

    max' :: (Ord a) => [a] -> a  
    max' [] = error "maximum of empty list"  
    max' [x] = x  
    max' (x:xs)   
        | x > max' xs = x  
        | otherwise = max' xs    
        
All this function is is simple pattern matching, if the list is empty there is an error, if the list has one element that is the max, if the list has a head (x) and a tail (xs) then if the head (x) is greater then the max of the tail (max xs) then x is the max, and lastly if all of those cases fail take the max of the tail.

We can try this with some numbers now, [1,9,3]. When we call max, the first two patterns aren't going to match. Then the list will be split into 1 and [9,3] and we want to find the max of [9,3]. It again will match the third pattern and splits into 9 and [3]. We then take the max of [3] which now matches the edge condition of a list with only one element so it returns 3. However, we compare 9 to the max of [3] amd we get 9. So now we know that the max of [9,3] is 9 and we go back up and compare 1 with the max of [9,3]. All to in the end return the max of the entire list as 9. 

## Quick Sort
One final example of a famous recursive program otherwise known as the poster child for why Haskell is so elegent that I would like to cover is that of quicksort. As the name implies, the function takes a list and it sorts it's elements. It's a very clever way of sorting items. Whi

The type signature is going to be quicksort :: (Ord a) => [a] -> [a]. The edge condition, empty list because a sorted empty list is an empty list. The main chuck of code is this, a sorted list is a list that has all the values less than or equal to the head of the list in front, then comes the head of the list in the middle and then come all the values that are bigger than the head. I know this may sound quite confusing in words so it may be more helpful to look at the code. Notice that we make the recursive call not once but twice in the function.

    quicksort :: (Ord a) => [a] -> [a]  
    quicksort [] = []  
    quicksort (x:xs) =   
        let smallerSorted = quicksort [a | a <- xs, a <= x]  
            biggerSorted = quicksort [a | a <- xs, a > x]  
        in  smallerSorted ++ [x] ++ biggerSorted  

Try testing this code in ghci!

ghci> quicksort [44,5,2,1,9,23,7]
[1,2,5,7,9,23,44]

If we have, say [5,1,9,4,6,7,3] and we want to sort it, this algorithm will first take the head, which is 5 and then put it in the middle of two lists that are smaller and bigger than it. So at one point, you'll have [1,4,3] ++ [5] ++ [9,6,7]. We know that once the list is sorted completely, the number 5 will stay in the fourth place since there are 3 numbers lower than it and 3 numbers higher than it. Now, if we sort [1,4,3] and [9,6,7], we have a sorted list! We sort the two lists using the same function. 

## Going Forward
An essential element of Haskell is recursion, of which you should now be an expert or at least compentant in. It truly is the most fundemental and in my opinion interesting mental shifts to coding in Haskell. Go to [blog 4](Blog4.md) to look at benchmarking between python and haskell programs.

## Resources
* http://learnyouahaskell.com/recursion#hello-recursion
* https://en.wikibooks.org/wiki/Haskell/Recursion 